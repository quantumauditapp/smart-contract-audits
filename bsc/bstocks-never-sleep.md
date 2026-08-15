---
token: bStocks Never Sleep
ticker: BSTOCKS
network: bsc
risk_score: 39
status: medium
date: 2026-08-15
---

# bStocks Never Sleep (BSTOCKS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bstocks-never-sleep-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and pool-based state transitions. The audit identified a critical vulnerability due to the incomplete `_processTax` function, which is central to the token's economic model. Additionally, a high-severity bug in timestamp calculation for tax expiration and medium-severity concerns regarding long-term timestamp truncation and high centralization risk were found. These issues significantly impact the contract's functionality, security, and long-term viability.

> **Final Recommendation:** It is imperative to complete the implementation of the `_processTax` function and ensure its logic is thoroughly reviewed for security vulnerabilities, especially reentrancy and correct interaction with external contracts. The `finalizeMigration` function's `taxExpirationTime` calculation must be corrected to prevent unintended and excessively long tax periods. Consider the long-term implications of `uint64` and `uint48` for timestamp storage and explore alternatives if the contract is expected to operate for several decades. Finally, review the extent of owner privileges and consider implementing a multi-signature wallet or time-locked governance for critical administrative actions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes OpenZeppelin's upgradeable standards (ERC20Upgradeable, OwnableUpgradeable, Initializable) and `SafeERC20` for secure token interactions, demonstrating good foundational… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model involves dynamic buy/sell taxes and a liquidation mechanism, which are central to its design (7.4 Economic). The `onlyOwner` role holds significant control, allowing the… |
| **Upgrades** | 8/10 | Low | The contract is designed as an upgradeable proxy implementation, correctly using OpenZeppelin's `Initializable` and `_disableInitializers()` in the constructor (7.7 Upgrades). This allows for future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium_

### `C-01` — Incomplete `_processTax` Function  *(Severity: Critical · Status: Unresolved)*

The `_processTax` function, which is called within `_liquidateTax` and is responsible for handling accumulated tax amounts, is entirely missing from the provided source code. This function is central to the token's economic model and its interactions with the `taxProcessor` and `dividendContract`. Without its implementation, the core functionality of tax distribution and liquidation cannot be assessed for security vulnerabilities, including reentrancy, incorrect calculations, or improper external calls.

**Recommendation:** Complete the implementation of the `_processTax` function. Ensure it correctly handles the accumulated tax, interacts securely with `taxProcessor` and `dividendContract`, and implements reentrancy guards if external calls are made. The completed function must be thoroughly audited.


### `H-01` — Incorrect `taxExpirationTime` Calculation in `finalizeMigration`  *(Severity: High · Status: Unresolved)*

In the `finalizeMigration` function, the `taxExpirationTime` is updated with `currentPoolState.taxExpirationTime + block.timestamp`. If `currentPoolState.taxExpirationTime` is already an absolute timestamp (as implied by its usage with `block.timestamp > currentPoolState.taxExpirationTime`), adding `block.timestamp` to it will result in an extremely large and incorrect future timestamp, effectively making the tax period last for an unintended, excessively long duration.

**Recommendation:** Correct the calculation of `taxExpirationTime` in `finalizeMigration`. If the intention is to extend the tax period from the current time, it should be `block.timestamp + duration` (where `duration` is the intended extension). If it's meant to be a fixed absolute time, it should be set directly. Ensure the logic aligns with the intended economic model.


### `M-01` — Long-Term Timestamp Truncation Risk  *(Severity: Medium · Status: Unresolved)*

The `taxExpirationTime` (uint64) and `antiFarmerExpirationTime` (uint48) variables are used to store `block.timestamp` values. While sufficient for current operations, `block.timestamp` is a `uint256`. Casting it to `uint64` or `uint48` introduces a truncation risk in the distant future (approximately 2070 for `uint64` and 2040 for `uint48`). If the contract is intended for operation beyond these dates, this could lead to unexpected behavior and incorrect state transitions.

**Recommendation:** Consider using `uint256` for `taxExpirationTime` and `antiFarmerExpirationTime` if the contract is expected to operate for several decades. Alternatively, implement a migration strategy or a mechanism to reset these values before the truncation threshold is reached.


### `M-02` — High Centralization Risk via Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `onlyOwner` role has extensive control over critical contract parameters and state transitions. The owner can initiate and finalize migration (`startMigration`, `finalizeMigration`), which changes the `PoolState` and affects tax enforcement. The owner also sets crucial external addresses (`taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, `mainPool`, and other `pools`) during initialization. This high degree of centralization means a single compromised or malicious owner account could significantly impact the protocol's integrity and user funds.

**Recommendation:** To mitigate centralization risks, consider implementing a multi-signature wallet for the owner address. For highly sensitive operations, a time-lock mechanism could be introduced to provide a delay before changes take effect, allowing the community or users to react to potentially malicious actions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x244b...7777`](https://bscscan.com/address/0x244b112cf746e62a5df723cbde9906a6defd7777) |
| **Network** | BNB Chain |
| **Price** | $0.0003492 |
| **24h Volume** | $290.1K |
| **Liquidity** | $72.8K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 8d |
| **Top-10 Holders** | 22.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1380 buys / 1061 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x45dcb68a2ddccf00271b6941cffe70676e5c8247)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bstocks-never-sleep-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
