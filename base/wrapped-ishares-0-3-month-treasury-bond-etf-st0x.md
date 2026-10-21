---
token: Wrapped  iShares 0-3 Month Treasury Bond ETF ST0x
ticker: WTSGOV
network: base
risk_score: 72
status: high
date: 2026-09-14
---

# Wrapped  iShares 0-3 Month Treasury Bond ETF ST0x (WTSGOV) — Smart Contract Security Analysis | Base

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-ishares-0-3-month-treasury-bond-etf-st0x-base)

---

## Audit Summary

The StoxWrappedTokenVault contract, implemented as an ERC4626 vault, has been audited. The contract leverages OpenZeppelin's upgradeable standards and follows a BeaconProxy pattern. The core logic is minimal, primarily relying on the well-vetted ERC4626 standard. Identified issues are primarily related to potential economic risks from underlying asset choices and minor code hygiene, with no critical or high-severity vulnerabilities found in the contract's direct implementation.

> **Final Recommendation:** It is recommended to carefully select the underlying asset token, ensuring it adheres to standard ERC-20 behavior without transfer fees or rebasing mechanisms, or to implement specific handling for such tokens. Consider the trade-offs of not having emergency administrative controls; if such controls are deemed necessary for operational safety, integrate a robust access control mechanism. Review and address the minor code hygiene issues to improve clarity and maintainability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract is built upon OpenZeppelin's battle-tested ERC4626Upgradeable standard, providing a robust foundation for a token vault (7.2 Code Security). The custom logic is minimal, primarily… |
| **Governance / Economics** | 1/10 | High | The contract does not implement any explicit governance mechanisms (7.5 Governance), operating as a permissionless ERC4626 vault once initialized. Economic risks are primarily associated with the… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern, with the implementation contract `StoxWrappedTokenVault` utilizing OpenZeppelin's `Initializable` base (7.7 Upgrades). The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `M-01` — Missing Handling for Fee-on-Transfer or Rebase Tokens  *(Severity: Medium · Status: Unresolved)*

The ERC4626 vault does not implement specific checks or logic to handle underlying asset tokens that charge fees on transfer or rebase their balances. If such a token is used as the `asset`, the vault's `totalAssets()` calculation could become inaccurate, leading to a discrepancy between the actual assets held and the reported value. This can result in legitimate depositors losing funds or enable malicious actors to profit from the accounting imbalance (7.4 Economic, 7.2 Code Security).

**Recommendation:** Implement a whitelist for approved asset tokens to ensure only standard ERC-20 tokens are used. Alternatively, if non-standard tokens must be supported, add custom logic to account for transfer fees or rebase mechanisms to maintain accurate vault accounting. Consider disallowing tokens that do not return `true` on transfer success or have other non-standard behaviors.


### `L-01` — Absence of Emergency Administrative Controls  *(Severity: Low · Status: Unresolved)*

The `StoxWrappedTokenVault` contract, as a standard ERC4626 implementation, does not include any explicit owner or administrative roles, nor does it have mechanisms for emergency actions such as pausing deposits/withdrawals. While this reduces centralization risk, it also means there is no way to halt operations in case of a critical vulnerability in the underlying asset, a severe market event, or an unforeseen exploit within the vault itself (7.3 Access Control, 7.8 Operations).

**Recommendation:** Evaluate the operational requirements for the vault. If emergency intervention capabilities are desired, consider integrating an `OwnableUpgradeable` or `AccessControlUpgradeable` pattern to allow a trusted entity to pause the contract or perform other critical administrative functions. This would introduce a degree of centralization but enhance the ability to respond to emergencies.


### `I-01` — Potential for Sandwich Attacks/Front-running on Deposit/Withdraw  *(Severity: Informational · Status: Unresolved)*

As with many DeFi protocols involving asset exchange or pooling, the standard `deposit` and `withdraw` functions of an ERC4626 vault can be susceptible to sandwich attacks or front-running. An attacker could observe a pending transaction, execute a prior transaction to manipulate the vault's share price (e.g., by making a large deposit/withdrawal), allow the victim's transaction to execute at a disadvantageous rate, and then execute a final transaction to revert the price manipulation and profit from the difference (7.4 Economic).

**Recommendation:** While this is an inherent market risk rather than a contract bug, users should be aware of this potential. For high-value operations, users could consider using private transaction relays or other MEV-resistant transaction methods to mitigate front-running risks.


### `I-02` — Redundant `__ERC20_init` Call with Empty Strings  *(Severity: Informational · Status: Unresolved)*

The `initialize` function calls `__ERC20_init("", "")`. While `ERC4626Upgradeable` itself inherits `ERC20Upgradeable` and correctly overrides `name()` and `symbol()` to derive them from the underlying asset, this explicit `__ERC20_init` call is redundant. It initializes the internal ERC20 state with empty strings, which is then effectively ignored by the overrides. This could be confusing or imply an unused internal ERC20 state (7.2 Code Security).

**Recommendation:** Remove the `__ERC20_init("", "")` call from the `initialize` function. The `ERC4626Upgradeable`'s own initialization (`__ERC4626_init`) handles the necessary ERC20 aspects, and the `name()` and `symbol()` overrides correctly fetch metadata from the asset.


### `I-03` — Misleading `initialize(address asset)` Function  *(Severity: Informational · Status: Unresolved)*

The contract includes a `pure` function `initialize(address asset)` that immediately reverts with `InitializeSignatureFn()`. This function has a similar signature to the actual initializer `initialize(bytes calldata data)`, which could be confusing for users or automated tools inspecting the contract's ABI. While it prevents accidental direct initialization, its presence without a clear purpose beyond reverting adds unnecessary complexity (7.2 Code Security).

**Recommendation:** Consider removing the `initialize(address asset)` function if its sole purpose is to revert. The `_disableInitializers()` in the constructor and the `initializer` modifier on `initialize(bytes calldata data)` are sufficient to prevent improper initialization. If kept, add a clear comment explaining its specific purpose.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x78c3...e935`](https://basescan.org/address/0x78c31580c97101694c70022c83d570150c11e935) |
| **Network** | Base |
| **Price** | $101.6100 |
| **24h Volume** | $73.9K |
| **Liquidity** | $26.4K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 334 buys / 300 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd5b83c33a8711e727c0abb6f72ee508755d37e10)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-ishares-0-3-month-treasury-bond-etf-st0x-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
