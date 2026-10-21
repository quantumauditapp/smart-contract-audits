---
token: 牛来
ticker: 牛来
network: bsc
risk_score: 33
status: low
date: 2026-08-30
---

# 牛来 (牛来) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-15a23f-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an upgradeable ERC20 token incorporating dynamic tax mechanisms and state management. It leverages OpenZeppelin's upgradeable contracts for security and maintainability. The audit identified several medium-severity issues related to potential reentrancy in external calls, centralized owner control over critical state transitions, and upgrade safety concerns regarding storage collisions. Additionally, minor issues include gas cost implications and configuration risks for initial tax rates. A significant portion of the `_processTax` function was truncated, limiting a full security assessment of its critical logic.

> **Final Recommendation:** Prioritize a full review of the `_processTax` function's complete implementation to ensure all external calls are robustly protected against reentrancy and other vulnerabilities. Implement a multi-signature wallet or time-locked governance for critical owner-controlled functions to mitigate centralized control risks and enhance decentralization. For future upgrades, meticulously plan storage slot management, especially for custom structs, to prevent data corruption. Consider optimizing the `_liquidateTax` call to reduce gas overhead on non-relevant transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good practices by using OpenZeppelin's upgradeable contracts and SafeERC20 for external token interactions (7.2 Code Security). The `PackedPoolState` struct helps optimize… |
| **Governance / Economics** | 9/10 | Low | The contract implements a centralized ownership model, with the `onlyOwner` role having significant control over critical state transitions like `startMigration` and `finalizeMigration` (7.3 Access… |
| **Upgrades** | 4/10 | Medium | The contract is designed for upgradeability using OpenZeppelin's `Initializable` pattern, correctly disabling initializers in the constructor and using the `initializer` modifier. However, the use of… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 18.8% |
| **Top-3 Unlocked** | 38.1% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Reentrancy Risk in External Calls within `_processTax`  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function uses a `notLiquidating` flag as a reentrancy guard for its own execution. However, the `_processTax` function, which is called within `_liquidateTax` and is expected to make external calls to `taxProcessor` and `dividendContract`, is truncated in the provided code. Without the full implementation, it's unclear if these external calls are adequately protected against reentrancy, potentially allowing malicious re-entries into other parts of the system or leading to unexpected state changes or fund manipulation.

**Recommendation:** Provide the complete implementation of the `_processTax` function for a thorough security review. Ensure that all external calls within `_processTax` are made with appropriate reentrancy guards (e.g., Checks-Effects-Interactions pattern, OpenZeppelin's `ReentrancyGuard`) to prevent malicious re-entries.


### `M-02` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The `onlyOwner` modifier on `startMigration` and `finalizeMigration` grants significant power to a single address to transition the contract's operational state. These state changes directly impact tax application and token behavior, introducing a single point of failure and trust. A compromised owner key could lead to unauthorized state changes and potential economic manipulation.

**Recommendation:** Consider implementing a multi-signature wallet for the owner role to distribute control and reduce the risk of a single point of failure. Alternatively, introduce a time-lock mechanism for critical state-changing functions to provide a window for community review or emergency intervention.


### `M-03` — Potential Storage Collisions in Upgrades  *(Severity: Medium · Status: Unresolved)*

The contract is designed as an upgradeable proxy implementation. The `PackedPoolState` struct is used for multiple state variables. Future upgrades that modify the layout of this struct (e.g., changing variable types, adding/removing variables) or the order of state variables in the contract without careful consideration of storage slot management could lead to storage collisions and data corruption, potentially bricking the contract or leading to loss of funds.

**Recommendation:** Adhere strictly to the storage layout rules for upgradeable contracts. When modifying structs or adding new state variables in future versions, ensure that new variables are appended to the end of the storage layout and that existing variable types or order are not changed. Utilize tools like `hardhat-upgrades` or `truffle-upgrades` to detect storage layout incompatibilities during development.


### `L-01` — Gas Cost Implications of `_liquidateTax` on Every Transfer  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function is invoked at the beginning of every `_transfer` operation. While its core logic is conditionally executed (only for transfers to `mainPool` under specific conditions), this unconditional call adds a small, constant gas overhead to all transfers. For transfers that trigger the full liquidation process, the gas cost could be significantly higher, potentially impacting user experience and network congestion.

**Recommendation:** Consider refactoring the `_liquidateTax` call to be more conditional, perhaps only calling it when `to == mainPool` or when a specific flag indicates a potential need for liquidation, rather than on every transfer. Alternatively, ensure that the `_processTax` function is highly optimized for gas efficiency.


### `I-01` — High Initial Tax Rates Possible  *(Severity: Informational · Status: Unresolved)*

The `buyTaxRate` and `sellTaxRate` are `uint16` values set during initialization, allowing for rates up to 655.35% (65535/10000). While there are no setters to change these rates post-initialization, the ability to set such extremely high rates initially could render the token economically unviable or lead to user distrust if misconfigured. This is a configuration risk rather than a code vulnerability.

**Recommendation:** Ensure that the initial `buyTaxRate` and `sellTaxRate` are set to economically sensible values during deployment. Clearly communicate the chosen tax rates to users to manage expectations and maintain transparency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbeea...7777`](https://bscscan.com/address/0xbeea1d618e533a387d941f58a7d4c9b7bd377777) |
| **Network** | BNB Chain |
| **Price** | $0.0941 |
| **24h Volume** | $2.94M |
| **Liquidity** | $1.39M |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 16d |
| **Top-10 Holders** | 40.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9090 buys / 8758 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x595d70977dff3c841df0bc0138ce89f80c7c9423)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-15a23f-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
