---
token: Giggle Cat
ticker: NIANNIAN
network: bsc
risk_score: 43
status: medium
date: 2026-08-30
---

# Giggle Cat (NIANNIAN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/giggle-cat-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms, anti-farmer features, and a multi-state pool management system. It leverages OpenZeppelin's upgradeable contracts for security and modularity. The contract includes a reentrancy guard for external calls during tax liquidation. Key areas of concern include the significant control vested in the owner and the reliance on external contracts for core tax processing and dividend distribution, which introduces dependencies and potential points of failure.

> **Final Recommendation:** It is recommended to implement a multi-signature wallet or a time-lock for critical owner-controlled functions to mitigate centralization risks. Thoroughly audit and secure all external contract dependencies, especially the `ITaxProcessor` and `IDividend` contracts, as their integrity is crucial for the token's functionality. Consider adding a recovery mechanism or robust error handling for collected tax funds in case external calls to `_processTax` fail.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices, utilizing OpenZeppelin's upgradeable standards and implementing a reentrancy guard (`notLiquidating` flag) for external calls in `_liquidateTax`… |
| **Governance / Economics** | 6/10 | Medium | The economic model is centered around dynamic buy/sell taxes and an anti-farmer mechanism, with immutable liquidation thresholds (`MIN_LIQ_THRESHOLD`, `START_LIQ_THRESHOLD`) providing some stability… |
| **Upgrades** | 5/10 | Medium | The contract is designed for upgradeability, inheriting from `Initializable` and using OpenZeppelin's upgradeable ERC20 and Ownable contracts. The `_disableInitializers()` call in the constructor and… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.6% (≈ permanent lock) |
| **LP Locked** | 99.6% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralization Risk with Owner Privileges  *(Severity: High · Status: Unresolved)*

The `owner` role has significant control over the contract's operational state, specifically through the `startMigration()` and `finalizeMigration()` functions. These functions allow the owner to transition the token's state from `BondingCurve` to `Migrating` and then to `TaxEnforcedAntiFarmer`, which directly impacts tax collection and anti-farmer mechanisms. This level of control introduces a single point of failure and potential for malicious or erroneous state changes by a compromised owner key.

**Recommendation:** Implement a multi-signature wallet for the `owner` role to require multiple approvals for critical state-changing functions. Alternatively, consider a time-lock mechanism to introduce a delay before such operations take effect, allowing for community review or intervention.


### `M-01` — Dependency on External `ITaxProcessor` and `IDividend` Contracts  *(Severity: Medium · Status: Unresolved)*

The contract relies heavily on external contracts (`taxProcessor` and `dividendContract`) for core functionalities such as processing collected taxes and distributing dividends. The `_processTax` function, which is critical for the token's economic model, makes an external call to `ITaxProcessor.processTax`. If these external contracts are malicious, buggy, or become inaccessible, the entire tax and dividend distribution system could fail, leading to loss of funds or system instability.

**Recommendation:** Conduct a comprehensive security audit of the `ITaxProcessor` and `IDividend` contracts to ensure their integrity and robustness. Implement robust monitoring for these external dependencies. Consider adding circuit breakers or emergency stop mechanisms that can temporarily disable tax processing if issues are detected with the external contracts.


### `M-02` — Potential for Stuck Funds if `_processTax` Fails  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function collects tax tokens into the contract's balance and then attempts to process them by calling `ITaxProcessor.processTax(taxAmount)`. If this external call to the `taxProcessor` contract reverts or fails for any reason (e.g., due to a bug in the `taxProcessor`, insufficient gas, or an intentional block), the collected `taxAmount` will remain in the `FlapTaxTokenV3` contract. Without a specific recovery mechanism, these funds could accumulate and become permanently inaccessible.

**Recommendation:** Implement a recovery function, callable by the owner, to withdraw any accumulated tax tokens from the contract in case of `_processTax` failures. Alternatively, consider wrapping the external call in a `try/catch` block to handle failures gracefully, perhaps by logging the event and allowing the transaction to proceed without processing tax, or by temporarily disabling tax collection until the issue is resolved.


### `L-01` — `antiFarmerExpirationTime` Overflow Risk  *(Severity: Low · Status: Unresolved)*

The `antiFarmerExpirationTime` is stored as a `uint48`. In `finalizeMigration()`, it is set by `block.timestamp + antiFarmerDuration`. While `uint48` provides sufficient range for many years (approximately 8.9 million years), `block.timestamp` is a `uint256`. If `block.timestamp + antiFarmerDuration` were to exceed the maximum value of `uint48`, the value would silently truncate due to implicit conversion, leading to an incorrect (and potentially much earlier) expiration time.

**Recommendation:** Add an explicit `require` check to ensure that `block.timestamp + antiFarmerDuration` does not exceed `type(uint48).max` before assignment. For example: `require(block.timestamp + antiFarmerDuration <= type(uint48).max, "Anti-farmer expiration time exceeds uint48 max");`


### `L-02` — `taxExpirationTime` Overflow Risk  *(Severity: Low · Status: Unresolved)*

The `taxExpirationTime` is stored as a `uint64`. In `finalizeMigration()`, it is updated by `currentPoolState.taxExpirationTime + block.timestamp`. If `currentPoolState.taxExpirationTime` already holds a large value (e.g., from previous additions) and `block.timestamp` is also large, their sum could theoretically exceed `type(uint64).max`. This would result in an integer overflow, leading to an incorrect (and potentially much earlier) expiration time.

**Recommendation:** Add an explicit `require` check to ensure that `currentPoolState.taxExpirationTime + block.timestamp` does not exceed `type(uint64).max` before assignment. For example: `require(currentPoolState.taxExpirationTime + block.timestamp <= type(uint64).max, "Tax expiration time exceeds uint64 max");`


### `I-01` — `_plainTransfer` Function Visibility  *(Severity: Informational · Status: Unresolved)*

The `_plainTransfer` function is declared as `internal`. This function serves as a wrapper for `super._transfer` without applying any tax logic. While its current `internal` visibility is appropriate for its usage within the contract, it means no external entity or even derived contracts (without specific inheritance patterns) can directly call a non-taxed transfer. This is an architectural choice that might limit flexibility if a public non-taxed transfer mechanism were ever desired for specific scenarios or roles.

**Recommendation:** No immediate action is required. This is an observation regarding design choice. If future requirements include allowing specific roles or external contracts to perform non-taxed transfers, consider creating a new public/external function with appropriate access control that calls `_plainTransfer`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcb74...7777`](https://bscscan.com/address/0xcb74970b86b9abf3d75748eb2c3bff53e5cd7777) |
| **Network** | BNB Chain |
| **Price** | $0.00003926 |
| **24h Volume** | $8.2K |
| **Liquidity** | $23.4K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 6d |
| **Top-10 Holders** | 53.4% of supply |
| **Buy / Sell Tax** | 5.0% / 5.0% |
| **24h Transactions** | 525 buys / 522 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x012af0c25e8660aa41cc1f0297a8613254418109)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/giggle-cat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
