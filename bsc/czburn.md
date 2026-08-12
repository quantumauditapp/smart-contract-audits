---
token: CZBURN
ticker: CBURN
network: bsc
risk_score: 36
status: medium
date: 2026-08-12
---

# CZBURN (CBURN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/czburn-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and pool state management. The audit identified a high-severity reentrancy vulnerability in the tax liquidation process, which could lead to unintended fund manipulation or state corruption. Additionally, potential denial of service for transfers to the main pool and several medium to informational findings were noted. The contract utilizes OpenZeppelin's upgradeable patterns correctly, demonstrating a solid architectural foundation for upgradeability.

> **Final Recommendation:** Address the high-severity reentrancy vulnerability by implementing a reentrancy guard or strictly adhering to the Checks-Effects-Interactions pattern in the `_liquidateTax` function. Mitigate the denial of service risk for `mainPool` transfers by adding robust error handling for external calls to `taxProcessor`, potentially allowing transfers to proceed without tax processing in case of external failures. Review and either utilize or remove all unused state variables to improve code clarity and reduce potential for future issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 and Ownable patterns, contributing to a robust architectural foundation (7.1 Architecture). However, a significant reentrancy vulnerability was… |
| **Governance / Economics** | 6/10 | Medium | The economic model (7.4 Economic) involves dynamic tax rates and liquidation thresholds, which are managed through state transitions. A potential denial of service exists for transfers to the… |
| **Upgrades** | 5/10 | Medium | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` and `Upgradeable` patterns (7.7 Upgrades). The `_disableInitializers()` call in the constructor and the use of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Reentrancy Vulnerability in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function modifies `poolState.notLiquidating` to `false`, then makes an external call to `_processTax(taxAmount)`, and only after the external call, resets `poolState.notLiquidating` to `true`. If the `taxProcessor` contract is malicious or compromised, it could re-enter the `_transfer` function (which calls `_liquidateTax`) while `notLiquidating` is still `false`. This could lead to `_processTax` being called multiple times with the same `taxAmount`, potentially draining the contract's tax balance or causing incorrect state transitions and economic manipulation.

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function or ensure that all state changes (effects) are completed before any external calls (interactions). Specifically, set `poolState.notLiquidating` to `true` immediately after the `_processTax` call, or consider moving the external call to `_processTax` to a separate, owner-triggered function if it doesn't strictly need to happen within the same transaction as a transfer.


### `M-01` — Potential Denial of Service for Transfers to `mainPool`  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function is called on every transfer to the `mainPool`. This function includes an external call to `_processTax` on the `taxProcessor` contract. If the `_processTax` call reverts for any reason (e.g., `taxProcessor` is paused, buggy, or runs out of gas), the entire `_transfer` transaction will revert. This could prevent all transfers to the `mainPool`, effectively halting a critical part of the token's functionality and causing a denial of service for users attempting to interact with the main liquidity pool.

**Recommendation:** Implement robust error handling for the external call to `_processTax`. Consider wrapping the call in a `try/catch` block to gracefully handle failures. In case of a revert, the contract could log the error and allow the transfer to proceed without tax processing, or temporarily disable tax processing until the issue with `taxProcessor` is resolved. Additionally, provide an owner-controlled mechanism to update or pause the `taxProcessor` address.


### `M-02` — Unused State Variables and Parameters  *(Severity: Medium · Status: Unresolved)*

Several state variables are initialized but not used within the provided contract code. Specifically, `liqExpectedOutputAmount`, `v2Router`, `quoteToken`, and `dividendContract` are set during initialization but do not appear to be referenced in any of the contract's functions. While these might be intended for external interaction or future functionality, their current unused status can indicate incomplete design, potential for future integration issues, or simply dead code, increasing contract complexity unnecessarily.

**Recommendation:** Review the contract's design to ensure all state variables serve a clear purpose within the contract or are explicitly documented as external dependencies. Remove any truly unused variables to reduce contract size, improve readability, and minimize potential attack surface. If they are intended for future use, consider adding placeholder functions or comments to indicate their purpose.


### `L-01` — Hardcoded `maxSupply` and Tax Rate Divisor  *(Severity: Low · Status: Unresolved)*

The `maxSupply` is declared as a `constant` `1e9 ether`, fixing the total token supply permanently. While this might be an intentional design choice, it removes any flexibility for future adjustments to the token's supply cap. Similarly, tax rates are consistently divided by `10000` (`(amount * rate) / 10000`), implying a fixed basis point precision for tax calculations. This hardcoded divisor means that changing the precision of tax rates would require a contract upgrade.

**Recommendation:** Clearly document the implications of a fixed `maxSupply` for the token's economic model. For the tax rate divisor, consider making it a configurable parameter (e.g., `TAX_RATE_DENOMINATOR`) if future flexibility in tax precision is desired. If not, ensure the current precision is well-understood and accepted by the protocol's stakeholders.


### `I-01` — Insufficient Event Emission for Critical State Changes  *(Severity: Informational · Status: Unresolved)*

The contract emits `PoolStateChanged` when the `state` enum changes. However, other critical economic parameters and internal states that can be modified within `_liquidateTax` are not accompanied by event emissions. Specifically, changes to `poolState.liquidationThreshold`, `poolState.taxExpirationTime`, `poolState.buyTaxRate`, `poolState.sellTaxRate` (when state becomes `TaxFree`), and `poolState.notLiquidating` are not explicitly logged. This lack of events makes it challenging for off-chain monitoring, analytics, and user interfaces to accurately track the token's real-time economic parameters.

**Recommendation:** Emit events for all significant state changes, especially those affecting economic parameters or internal flags that influence core logic. This includes `liquidationThreshold`, `taxExpirationTime`, `buyTaxRate`, `sellTaxRate`, and `notLiquidating`. Comprehensive event logging enhances transparency, auditability, and allows for more robust off-chain integration.


### `I-02` — Potential Truncation in `antiFarmerExpirationTime` Type Casting  *(Severity: Informational · Status: Unresolved)*

The `antiFarmerExpirationTime` variable is declared as `uint48`. It is set by casting `block.timestamp + antiFarmerDuration` (both `uint256`) to `uint48`. While `block.timestamp` is unlikely to exceed `2^48 - 1` in the foreseeable future (approximately 8.9 million years), if `antiFarmerDuration` is set to an extremely large value, or if the contract remains active for an exceptionally long period, the sum `block.timestamp + antiFarmerDuration` could exceed the maximum value of `uint48`. This would result in silent truncation of the value, leading to an incorrect expiration time.

**Recommendation:** Ensure that the combined value of `block.timestamp` and `antiFarmerDuration` will not exceed `uint48` maximum. Consider adding a `require` check during initialization or when `antiFarmerDuration` is set to prevent values that would lead to truncation. Alternatively, use a larger integer type (e.g., `uint64`) for `antiFarmerExpirationTime` if there's a possibility of very long durations or contract longevity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3094...7777`](https://bscscan.com/address/0x309409237c4db70cd66067741edcf02bf69e7777) |
| **Network** | BNB Chain |
| **Price** | $0.006038 |
| **24h Volume** | $909.1K |
| **Liquidity** | $219.1K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 22h |
| **Top-10 Holders** | 87.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3747 buys / 1422 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0b72bf3c70531e04d58783b2dd12fb71180744de)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/czburn-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
