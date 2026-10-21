---
token: SOCK
ticker: SOCK
network: bsc
risk_score: 70
status: high
date: 2026-09-03
---

# SOCK (SOCK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sock-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic taxation and liquidation mechanisms. The audit identified a critical denial of service vulnerability where external calls within the transfer logic can halt all token transfers. Medium risks include significant owner control over critical state transitions and potential for front-running on tax rate changes. The contract utilizes OpenZeppelin's upgradeable patterns effectively, ensuring upgrade safety. Recommendations focus on robust error handling for external interactions, decentralizing control where feasible, and optimizing gas efficiency.

> **Final Recommendation:** Prioritize addressing the critical denial of service vulnerability by implementing robust error handling for external calls within the `_liquidateTax` function. Consider moving tax processing to a separate, pull-based mechanism or an owner-triggered function to decouple it from core token transfers. Evaluate the economic impact of owner-controlled state transitions and explore options for decentralization or timelocks for critical parameters. Finally, optimize struct packing for gas efficiency and acknowledge the precision loss in tax calculations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates a well-structured architecture (7.1) using OpenZeppelin standards for ERC20 and upgradeability. However, a critical code security (7.2) vulnerability exists where external… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model (7.4) involves dynamic tax rates and state transitions (e.g., `BondingCurve` to `TaxEnforcedAntiFarmer`). Access control (7.3) is managed via `OwnableUpgradeable`… |
| **Upgrades** | 3/10 | High | The contract is designed as an upgradeable proxy (7.7) using OpenZeppelin's `Initializable` and `ERC20Upgradeable` patterns. The constructor correctly calls `_disableInitializers()` to prevent… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Denial of Service (DoS) on All Transfers Due to Reverting External Calls  *(Severity: Critical · Status: Unresolved)*

The `_liquidateTax` function is called at the beginning of every `_transfer` operation. This function contains external calls to `ITaxProcessor(taxProcessor).processTax(...)` and `IDividend(dividendContract).distributeDividends(...)`. If either of these external calls reverts for any reason (e.g., misconfiguration, temporary issues in the external contract, or malicious action targeting the external contract), all subsequent `_transfer` calls will also revert, effectively halting all token transfers for all users. This constitutes a severe denial of service for the entire token functionality.

**Recommendation:** Implement robust error handling for external calls within `_liquidateTax`. Consider using `try/catch` blocks to gracefully handle reverts without blocking core token transfers. Alternatively, decouple the tax liquidation process from the `_transfer` function. This could involve moving the liquidation logic to a separate, owner-callable function or a function that can be called by anyone but does not revert if external calls fail (e.g., by using a pull-based mechanism for tax processing or allow…


### `M-01` — Centralization Risk with Owner-Controlled State Transitions  *(Severity: Medium · Status: Unresolved)*

The `OwnableUpgradeable` pattern grants the contract owner significant control over critical state transitions. Functions like `startMigration` and `finalizeMigration` are `onlyOwner` and directly change the `poolState`, which dictates the token's taxation rules. While necessary for initial setup and migration, this centralized control allows the owner to unilaterally alter the token's economic behavior, potentially without sufficient community oversight or warning. The `taxProcessor` and `dividendContract` addresses are set during initialization and cannot be changed, but the owner's ability to trigger state changes that affect their interaction is significant.

**Recommendation:** For critical owner-controlled functions that significantly alter the token's economic model, consider implementing a timelock mechanism. This would introduce a delay between the owner initiating a change and it becoming effective, providing users and the community with time to react or exit if they disagree with the proposed changes. Additionally, review if any other critical parameters should be immutable or have a more decentralized update mechanism.


### `M-02` — Potential for Front-running/MEV on Time-Based State Transitions  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function modifies the `poolState` based on `block.timestamp` exceeding `taxExpirationTime` or `antiFarmerExpirationTime`. Specifically, it can transition the pool state from `TaxEnforcedAntiFarmer` to `TaxEnforced` or `TaxFree`. If the economic impact of these state changes (e.g., changes in tax rates) is significant, malicious actors or miners could front-run transactions to ensure their operations occur just before or after a state transition, potentially gaining an unfair advantage. While `block.timestamp` is a standard mechanism, its manipulability by miners within a small window is a known vector for MEV.

**Recommendation:** While `block.timestamp` is commonly used, be aware of its limitations regarding precise timing and potential for MEV. If the economic implications of these state transitions are critical, consider if alternative mechanisms (e.g., a commit-reveal scheme, or requiring a specific block number instead of timestamp for critical changes) could mitigate front-running. Ensure that the economic model accounts for potential MEV around these state changes.


### `L-01` — Precision Loss in Tax Calculation  *(Severity: Low · Status: Unresolved)*

The tax calculation `(amount * rate) / 10000` uses integer division. For small `amount` values or small `buyTaxRate`/`sellTaxRate` values, this can result in a calculated `tax` of 0, even if a fractional tax should theoretically apply. For example, if `amount` is 100 and `rate` is 1 (representing 0.01%), the calculation `(100 * 1) / 10000` yields 0. This means the protocol might collect slightly less tax than intended for small transactions.

**Recommendation:** Acknowledge that integer division inherently causes precision loss. If this minor loss is acceptable for the protocol's economic model, no change is strictly necessary. If higher precision is desired for very small transactions or rates, consider using a higher precision fixed-point math library or adjusting the tax rate basis (e.g., using a denominator of `100_000` or `1_000_000` instead of `10_000`) to allow for finer granularity in tax rates.


### `I-01` — Suboptimal Storage Packing in `PackedPoolState` Struct  *(Severity: Informational · Status: Unresolved)*

The `PackedPoolState` struct contains members of various sizes: `uint8`, `uint16`, `bool`, `uint96`, `uint64`, `uint48`. While Solidity attempts to pack variables into 32-byte storage slots, the current ordering may not be optimal. Reordering the members from largest to smallest (or grouping smaller types strategically) can reduce the number of storage slots used, thereby saving gas on state reads and writes.

**Recommendation:** Reorder the `PackedPoolState` struct members to optimize storage packing. A more efficient order would typically place larger data types before smaller ones, for example: `uint96 liquidationThreshold`, `uint64 taxExpirationTime`, `uint48 antiFarmerExpirationTime`, `uint16 buyTaxRate`, `uint16 sellTaxRate`, `uint8 state`, `bool notLiquidating`. This could potentially reduce the number of storage slots from 3 to 1 or 2, leading to gas savings.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1250...7777`](https://bscscan.com/address/0x1250a23a460316e4cb3d3a674a260b0e30947777) |
| **Network** | BNB Chain |
| **Price** | $0.00003551 |
| **24h Volume** | $98.1K |
| **Liquidity** | $19.5K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 44.4% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 1753 buys / 1386 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x981d496e8aeb4291300b715bb60b8b2856a7e3ff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sock-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
