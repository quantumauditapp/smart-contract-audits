---
token: Intuition
ticker: TRUST
network: base
risk_score: 97
status: critical
date: 2026-08-13
---

# Intuition (TRUST) — Smart Contract Security Analysis | Base

> **Risk Score: 97/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/intuition-base)

---

## Audit Summary

The audit of the Intuition Trust contract (implementation of the token) identified critical vulnerabilities related to its upgradeable design and tokenomics. Specifically, the ERC20 initialization is missing, and the intended minting logic with supply caps from the inherited `TrustToken` contract is completely bypassed. This allows an authorized controller to mint an unlimited supply of tokens, severely impacting the token's economic model. While the proxy setup is robust, these implementation flaws pose significant risks.

> **Final Recommendation:** It is strongly recommended to immediately address the critical issues identified. The `Trust` contract must be upgraded to correctly initialize the ERC20 component by calling `__ERC20_init` and to properly integrate or remove the `TrustToken`'s minting logic and supply caps. A thorough review of the intended tokenomics and how they are implemented in the `Trust` contract is essential to ensure that supply limits and minter roles function as designed. Consider a full re-evaluation of the inheritance structure and function overrides to prevent similar logic bypasses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The contract utilizes OpenZeppelin's upgradeable patterns and access control, which generally provide a solid foundation (7.1 Architecture, 7.2 Code Security). However, critical implementation errors… |
| **Governance / Economics** | 1/10 | High | The economic model of the token is critically compromised due to the bypassed minting logic (7.4 Economic). The `MAX_SUPPLY` and minter-specific caps defined in `TrustToken` are not enforced by the… |
| **Upgrades** | 1/10 | High | The contract employs the Transparent Upgradeable Proxy pattern with a ProxyAdmin owned by a Timelock, which is a strong setup for upgrade safety (7.7 Upgrades). The `reinitialize` function is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 2 Critical · 🟠 1 High_

### `C-01` — ERC20 Initialization Missing in `Trust` Contract  *(Severity: Critical · Status: Unresolved)*

The `Trust` contract inherits `ERC20Upgradeable` via `TrustToken`, but its `reinitialize` function only calls `__AccessControl_init()`. The `TrustToken` contract has an `init()` function that calls `__ERC20_init("TRUST", "TRUST")`, but this `init()` function is never called by the `Trust` contract. Consequently, the ERC20 token's name, symbol, and decimals are not properly initialized, which can lead to display issues in wallets/explorers and potential integration problems with DeFi protocols.

**Recommendation:** Ensure that the `reinitialize` function in `Trust` calls the `init()` function of `TrustToken` or directly calls `__ERC20_init` with the desired token name and symbol. For example, `super.init()` or `__ERC20_init("Intuition", "INTU")` should be added to `reinitialize`.


### `C-02` — Minting Logic and Supply Caps Bypassed  *(Severity: Critical · Status: Unresolved)*

The `Trust` contract's `mint(address to, uint256 amount)` function overrides the `mint` function from `TrustToken`. However, the `Trust` contract's implementation only calls `_mint(to, amount)` (the internal ERC20 mint) and does not call `super.mint()` or otherwise incorporate the logic from `TrustToken`'s `mint` function. This means the `MINTER_A`/`MINTER_B` restrictions, `MAX_SUPPLY` check, `totalMinted` updates, and `minterAmountMinted` tracking from `TrustToken` are completely bypassed. As a result, the `baseEmissionsController` can mint an unlimited amount of tokens, ignoring all intended supply caps and minter-specific limits.

**Recommendation:** The `Trust` contract's `mint` function must be refactored to correctly enforce the intended minting logic. If the `TrustToken`'s minting logic (minter caps, max supply) is still desired, the `Trust` contract's `mint` function should call `super.mint(to, amount)` or replicate the necessary checks and state updates. If the `TrustToken` logic is deprecated, it should be explicitly removed or clearly documented, and new supply caps should be implemented in `Trust` if desired.


### `H-01` — Unused `TrustToken` Minting Logic and State Variables  *(Severity: High · Status: Unresolved)*

Due to the `Trust` contract's `mint` function overriding and bypassing the `TrustToken`'s `mint` function (C-02), the `MAX_SUPPLY`, `MINTER_A`, `MINTER_B` constants, and the `totalMinted`, `minterAmountMinted` state variables within `TrustToken` are effectively dead code. They are defined but never utilized or updated by the live `Trust` contract logic. This creates a false sense of security, makes the code harder to understand, and could lead to confusion regarding the actual tokenomics.

**Recommendation:** Align the code with the intended functionality. If the `TrustToken` minting logic is to be used, ensure it is correctly integrated (as per C-02 recommendation). If it is no longer relevant, consider removing these unused constants and state variables from `TrustToken` or refactoring the inheritance to avoid inheriting deprecated logic, to improve clarity and prevent misleading information.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6cd9...d8a3`](https://basescan.org/address/0x6cd905df2ed214b22e0d48ff17cd4200c1c6d8a3) |
| **Network** | Base |
| **Price** | $0.05391 |
| **24h Volume** | $197.9K |
| **Liquidity** | $265.5K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 77.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1348 buys / 1625 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x17f707cf3edbbd5d9251d4bcdf9ad70a247d7b84)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/intuition-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
