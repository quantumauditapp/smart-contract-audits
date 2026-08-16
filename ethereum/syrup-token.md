---
token: Syrup Token
ticker: SYRUP
network: ethereum
risk_score: 70
status: high
date: 2026-08-16
---

# Syrup Token (SYRUP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/syrup-token-eth)

---

## Audit Summary

The MapleToken contract, serving as the implementation for a UUPS proxy, provides standard ERC-20 functionality with additional minting and burning capabilities controlled by designated modules and a governor. While access control for critical functions is robust, a critical upgradeability flaw exists due to incorrect handling of state variables in the inherited ERC20Proxied contract. Significant reliance on an external Globals contract introduces a high external dependency risk. Additionally, unchecked arithmetic for balance additions presents a theoretical overflow risk, and standard ERC-20 front-running concerns are present.

> **Final Recommendation:** Address the critical upgradeability flaw by refactoring the `ERC20Proxied` contract to manage ERC-20 state variables via explicit storage slots, ensuring persistence across upgrades. Conduct a comprehensive security audit of the `Globals` contract to mitigate the high external dependency risk. Re-evaluate the use of `unchecked` blocks for balance additions in `_mint` and `_transfer` to prevent theoretical overflow scenarios. Educate users on standard ERC-20 front-running risks, particularly concerning `approve` and `permit` functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract implements standard ERC-20 functionality (7.2 Code Security) with robust access control (7.3 Access Control) for minting, burning, and module management, leveraging a governor and… |
| **Governance / Economics** | 2/10 | High | The governance model (7.5 Governance) is centralized through a `governor` address, which controls critical functions like `addModule` and `removeModule`. These actions are further protected by a… |
| **Upgrades** | 1/10 | High | The contract is designed as a UUPS proxy implementation, correctly using storage slots for `GLOBALS_SLOT` and `IMPLEMENTATION_SLOT` (7.7 Upgrades). However, a critical upgradeability flaw exists: the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 26.3% |
| **Top-3 Unlocked** | 60.6% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — UUPS Implementation State Variable Mismanagement  *(Severity: Critical · Status: Unresolved)*

The `ERC20Proxied` abstract contract, inherited by `MapleToken`, declares storage variables such as `name`, `symbol`, `decimals`, `totalSupply`, `balanceOf`, `allowance`, and `nonces`. In a UUPS proxy architecture, these state variables must reside in the proxy's storage, not directly in the implementation contract. Declaring them in the implementation means their values are stored in the implementation's storage, which is not persistent across upgrades. An upgrade to a new implementation would result in the complete loss of all token state, including user balances and allowances.

**Recommendation:** Refactor `ERC20Proxied` to manage all ERC-20 state variables using explicit storage slots, similar to how `GLOBALS_SLOT` and `IMPLEMENTATION_SLOT` are handled. This ensures that the state is stored in the proxy's persistent storage and remains intact across upgrades. Alternatively, consider using a well-established UUPS base contract that correctly handles ERC-20 state for proxy implementations.


### `H-01` — Centralized Control and High External Dependency on Globals Contract  *(Severity: High · Status: Unresolved)*

The `MapleToken` contract relies heavily on an external `Globals` contract for critical access control functions, specifically for determining the `governor()` and validating/unscheduling `onlyScheduled` calls. If the `Globals` contract is compromised, misconfigured, or contains vulnerabilities, it could directly impact the security and functionality of `MapleToken`, potentially allowing unauthorized `addModule`, `removeModule`, or other future governor-controlled actions.

**Recommendation:** Conduct a thorough security audit of the `Globals` contract to ensure its robustness, immutability (if intended), and proper access control mechanisms. Implement robust monitoring for the `Globals` contract's state and ownership. Consider implementing emergency pause mechanisms or circuit breakers within `MapleToken` that can be triggered independently of `Globals` in extreme situations to mitigate cascading risks.


### `M-01` — Unchecked Arithmetic for Balance Additions  *(Severity: Medium · Status: Unresolved)*

The `_mint` and `_transfer` internal functions utilize `unchecked` blocks for `balanceOf[recipient_] += amount_`. While Solidity 0.8.x generally provides checked arithmetic, `unchecked` blocks bypass these checks for gas optimization. In a highly improbable scenario where `balanceOf[recipient_]` is very close to `type(uint256).max` and `amount_` is non-zero, an overflow could occur, causing the recipient's balance to wrap around to a small number. This could lead to a loss of funds for the recipient or unexpected token economics.

**Recommendation:** Re-evaluate the necessity of `unchecked` blocks for `balanceOf` additions. While gas savings are a consideration, the potential for an overflow, however rare, might outweigh the benefit. If `unchecked` is deemed essential, ensure that the system's design accounts for the theoretical possibility of balance overflows and that total supply and individual balances are monitored for anomalies.


### `L-01` — Standard ERC-20 Front-Running Risks  *(Severity: Low · Status: Unresolved)*

Standard ERC-20 functions such as `approve`, `increaseAllowance`, `decreaseAllowance`, and `permit` are susceptible to front-running attacks. For instance, a user calling `approve(spender, newAmount)` could be front-run by a malicious `spender` who quickly spends the `oldAmount` before the `newAmount` is set, effectively allowing the `spender` to spend `oldAmount + newAmount`. Similarly, `permit` can be front-run on the `deadline` or `nonces` to invalidate a signature or execute it prematurely.

**Recommendation:** Educate users about the inherent risks associated with front-running on ERC-20 approvals and `permit` functions. Advise users to exercise caution with approvals, especially for large amounts, and to use `increaseAllowance`/`decreaseAllowance` carefully. For `permit`, users should be aware of the implications of `deadline` and `nonces`. While these are inherent to the ERC-20 standard, clear communication can help mitigate user-level risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x643c...2d66`](https://etherscan.io/address/0x643c4e15d7d62ad0abec4a9bd4b001aa3ef52d66) |
| **Network** | Ethereum |
| **Price** | $0.16 |
| **24h Volume** | $208.6K |
| **Liquidity** | $1.89M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 47.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 68 buys / 35 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x29dfcb94b1ab021ca46442d2b1a3ed3d2268fdc985d2fe9a3b67a6963670ec02)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/syrup-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
