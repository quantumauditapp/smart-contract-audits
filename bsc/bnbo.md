---
token: 币恩宝
ticker: BNBO
network: bsc
risk_score: 16
status: low
date: 2026-09-03
---

# 币恩宝 (BNBO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnbo-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex, time-based tax and liquidation mechanism. The audit identified a high-severity integer overflow vulnerability in time-related state variable updates, which could lead to incorrect tax expiration logic. Medium-severity issues include centralization risks due to immutable critical parameters and potential denial of service from external contract dependencies. The contract generally follows OpenZeppelin upgradeable patterns and includes a reentrancy guard for tax processing.

> **Final Recommendation:** Address the identified integer overflow vulnerability immediately by ensuring proper type handling for time-related calculations. Implement owner-controlled functions to update critical external contract addresses and economic parameters, or clearly document the upgrade process required for such changes. Thoroughly test the external `taxProcessor` and `dividendContract` implementations to ensure their stability and resilience against reverts, as their failure can impact core token functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's upgradeable standards (ERC20Upgradeable, OwnableUpgradeable) for robust foundational security (7.2 Code Security). A reentrancy guard is correctly implemented in… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model is driven by a multi-state tax mechanism, with the owner controlling key migration steps via `startMigration` and `finalizeMigration` (7.5 Governance). The… |
| **Upgrades** | 5/10 | Medium | The contract is designed as an upgradeable proxy, correctly utilizing OpenZeppelin's `Initializable` pattern, including `_disableInitializers()` in the constructor and the `initializer` modifier (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Integer Overflow in PackedPoolState Time Fields  *(Severity: High · Status: Unresolved)*

The `taxExpirationTime` (uint64) and `antiFarmerExpirationTime` (uint48) fields within the `PackedPoolState` struct are updated by casting a `uint256` sum (e.g., `currentPoolState.taxExpirationTime + block.timestamp` or `block.timestamp + antiFarmerDuration`) directly to the smaller `uint64` or `uint48` types. If the calculated sum exceeds the maximum value representable by the target smaller type, the value will silently truncate, leading to an incorrect and potentially much earlier expiration time than intended. This can prematurely disable tax collection or anti-farmer mechanisms, impacting the contract's economic model.

**Recommendation:** Ensure that the sums `currentPoolState.taxExpirationTime + block.timestamp` and `block.timestamp + antiFarmerDuration` are checked against the maximum values of `uint64` and `uint48` respectively before assignment. If an overflow is possible and undesirable, consider using larger types for these fields (e.g., `uint256`) or implementing explicit overflow checks and handling. For example, `require(sum <= type(uint64).max, "Overflow");` before casting.


### `M-01` — Centralization Risk due to Immutable Critical Parameters  *(Severity: Medium · Status: Unresolved)*

Several critical parameters, including `v2Router`, `taxProcessor`, `dividendContract`, `quoteToken`, `liqExpectedOutputAmount`, `antiFarmerDuration`, `buyTaxRate`, `sellTaxRate`, and the `pools` mapping, are set only during the `initialize` function and cannot be modified by the owner thereafter. This rigidity means that any necessary updates, corrections, or changes to these external dependencies or economic parameters (e.g., if a `taxProcessor` contract needs to be replaced or tax rates adjusted) would necessitate a full contract upgrade. This limits operational flexibility and increases the burden of maintenance.

**Recommendation:** Consider implementing owner-only functions to allow for the safe update of critical external contract addresses and configurable economic parameters (e.g., `setTaxProcessor(address newProcessor)`, `setBuyTaxRate(uint16 newRate)`). These functions should include appropriate input validation and emit events for transparency. For parameters that are intended to be immutable, ensure this is clearly documented and understood.


### `M-02` — Denial of Service from External Tax Processor/Dividend Contract  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function, which is called on every transfer to the `mainPool`, makes external calls to `ITaxProcessor(taxProcessor).processTax` and `IDividend(dividendContract).distributeDividends`. If either of these external contracts contains a bug, is paused, or is maliciously designed to revert, the `_liquidateTax` function will revert. This would consequently cause any transfer to the `mainPool` to fail, leading to a denial of service for a critical part of the token's functionality. While a reentrancy guard is present, it does not prevent reverts from external calls.

**Recommendation:** Implement robust error handling for external calls. Consider using a `try/catch` block to gracefully handle reverts from `taxProcessor` and `dividendContract`, allowing the `_liquidateTax` function to complete without reverting the entire transfer. Alternatively, ensure that the external contracts are highly reliable and thoroughly audited. Implement circuit breakers or emergency pause mechanisms for these external interactions if their failure could halt core operations.


### `L-01` — Reliance on `block.timestamp` for Critical Logic  *(Severity: Low · Status: Unresolved)*

The contract heavily relies on `block.timestamp` for managing `taxExpirationTime` and `antiFarmerExpirationTime`, and for triggering state transitions within the `_liquidateTax` function. While `block.timestamp` is commonly used for time-based logic, it is susceptible to manipulation by miners within a certain range (e.g., up to 900 seconds on Ethereum, though typically less on BSC). A malicious miner could slightly adjust the timestamp to accelerate or delay the expiration of tax or anti-farmer periods, potentially impacting trading strategies or arbitrage opportunities.

**Recommendation:** For critical time-sensitive operations where miner manipulation could have significant financial implications, consider using Chainlink Keepers or similar decentralized oracle solutions for time-based triggers, which provide more robust and tamper-resistant time sources. For less critical operations, `block.timestamp` is generally acceptable, but its limitations should be acknowledged.


### `I-01` — Lack of Owner Functions for `pools` Management  *(Severity: Informational · Status: Unresolved)*

The `pools` mapping, which determines which addresses are subject to buy/sell tax in the `TaxEnforcedAntiFarmer` state, is initialized only once during the `initialize` function. There are no owner-controlled functions to add or remove addresses from this mapping after deployment. This design choice makes the list of taxable pools immutable, which might be intended for simplicity or to prevent arbitrary changes. However, it limits operational flexibility, as any future need to update the list of pools would require a contract upgrade.

**Recommendation:** If the `pools` mapping is intended to be dynamic, consider adding owner-only functions like `addPool(address _pool)` and `removePool(address _pool)` to manage the list. If immutability is the desired design, ensure this is clearly documented and understood by all stakeholders, acknowledging that any changes will necessitate a contract upgrade.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7fb4...7777`](https://bscscan.com/address/0x7fb4758cb0c617c0bab1baf80525fab958637777) |
| **Network** | BNB Chain |
| **Price** | $0.0007743 |
| **24h Volume** | $183.4K |
| **Liquidity** | $89.9K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 7d |
| **Top-10 Holders** | 34.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 1386 buys / 1029 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7f7cac531dfad516b9bd55e63de2f773d00999cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnbo-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
