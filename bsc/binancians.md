---
token: Binancians
ticker: BINANCIANS
network: bsc
risk_score: 42
status: medium
date: 2026-09-25
---

# Binancians (BINANCIANS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binancians-bsc)

---

## Audit Summary

The audit of FlapTaxTokenV3 identified critical and high-severity vulnerabilities related to inconsistent state management, denial of service risks from external calls, and reentrancy. While the contract leverages OpenZeppelin's upgradeable patterns and efficient storage, these core logic and interaction flaws pose significant risks to the protocol's stability and economic model. Medium and low-severity issues regarding owner centralization and potential integer truncation were also noted. A critical informational finding was also noted due to truncated code.

> **Final Recommendation:** Address the critical logic error in `taxExpirationTime` management to ensure the protocol's economic model functions as intended. Implement robust error handling and consider alternative patterns (e.g., pull-based mechanisms, circuit breakers) for external calls within the `_liquidateTax` function to mitigate denial of service and reentrancy risks. Enhance access control for critical owner-controlled functions, potentially through multi-signature wallets or timelocks, to reduce centralization risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security are generally well-structured, utilizing OpenZeppelin's upgradeable contracts and a gas-efficient packed struct for `PoolState`. Immutable variables are… |
| **Governance / Economics** | 4/10 | Medium | 7.5 Governance relies on an `OwnableUpgradeable` pattern, granting the owner significant control over critical state transitions like `startMigration` and `finalizeMigration`. This introduces… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are handled using OpenZeppelin's `Initializable` pattern, with `_disableInitializers()` correctly called in the constructor and `initializer` modifier used for `initialize`. The use of… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Inconsistent `taxExpirationTime` Logic Leading to Premature Tax-Free State  *(Severity: Critical · Status: Unresolved)*

The `taxExpirationTime` variable is initialized as a duration (`uint64(params.taxDuration)`) in `initialize`. However, in `finalizeMigration`, `block.timestamp` is added to it, converting it into an absolute timestamp. The `_liquidateTax` function then compares `block.timestamp` directly to `currentPoolState.taxExpirationTime`. If `finalizeMigration` is *not* called, `taxExpirationTime` remains a duration. In this scenario, `block.timestamp > duration` will almost immediately evaluate to true (as `block.timestamp` is a large absolute number and `duration` is a relatively small number of seconds), causing the contract to prematurely transition to `PoolState.TaxFree`, effectively disabling ta…

**Recommendation:** Ensure `taxExpirationTime` consistently represents either a duration or an absolute timestamp. If it's an absolute timestamp, it should be initialized as `uint64(block.timestamp + params.taxDuration)` in `initialize`. If it's a duration, the comparison in `_liquidateTax` needs to be adjusted (e.g., `block.timestamp > initialTimestamp + currentPoolState.taxExpirationTime`).


### `H-01` — Denial of Service via External Calls in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function, called during every `_transfer` to the `mainPool`, makes external calls to `ITaxProcessor(taxProcessor).processTax(...)` and `IDividend(dividendContract).distribute(...)`. If either `taxProcessor` or `dividendContract` is a malicious contract, or contains a bug that causes it to revert, all transfers to the `mainPool` will be blocked. This creates a single point of failure and can lead to a denial of service for critical token functionality.

**Recommendation:** Implement robust error handling for external calls. Consider using a pull-based mechanism for tax processing and dividend distribution, or implement a circuit breaker/emergency pause mechanism for these external interactions. Ensure `taxProcessor` and `dividendContract` are highly trusted and thoroughly audited.


### `H-02` — Reentrancy Risk in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function performs state changes (updating `poolState`) and calculates `taxAmount` (based on `balanceOf(address(this))`) *before* making external calls to `ITaxProcessor(taxProcessor).processTax(...)` and `IDividend(dividendContract).distribute(...)`. While the state changes occur before the calls, if the `taxProcessor` or `dividendContract` are untrusted or malicious, they could reenter the `FlapTaxTokenV3` contract. A reentrant call could potentially manipulate the contract's internal token balance (`balanceOf(address(this))`) before `processTax` or `distribute` are executed, leading to incorrect tax processing or unexpected behavior.

**Recommendation:** Apply the Checks-Effects-Interactions pattern strictly. Ensure all state changes related to `taxAmount` and `poolState` are finalized *before* any external calls are made. Consider using a reentrancy guard if external calls cannot be moved after all state updates.


### `M-01` — Owner Centralization and Control over Pool States  *(Severity: Medium · Status: Unresolved)*

The `OwnableUpgradeable` pattern grants the contract owner significant control over critical protocol parameters and state transitions. The owner can initiate (`startMigration`) and finalize (`finalizeMigration`) changes to the `PoolState`, which directly impacts the token's tax mechanisms and transfer restrictions. While this level of control might be intended for initial setup and migration, it introduces a centralization risk where a compromised owner key could manipulate the token's core functionality.

**Recommendation:** Consider implementing a multi-signature wallet for ownership to reduce the risk of a single point of failure. For critical state transitions, consider adding a timelock or a governance mechanism to allow community oversight and reaction time.


### `L-01` — Potential `uint48` Truncation for `antiFarmerExpirationTime`  *(Severity: Low · Status: Unresolved)*

The `antiFarmerExpirationTime` is stored as a `uint48`. It is calculated as `block.timestamp + antiFarmerDuration`. While current `block.timestamp` values and typical `antiFarmerDuration` values fit within `uint48`, if `antiFarmerDuration` is set to an extremely large value (e.g., many decades or centuries in seconds), the sum `block.timestamp + antiFarmerDuration` could exceed the maximum value of `uint48` (`2^48 - 1`). This would result in silent truncation, leading to an incorrect and potentially much earlier `antiFarmerExpirationTime` than intended.

**Recommendation:** Ensure that `antiFarmerDuration` is constrained to values that, when added to `block.timestamp`, will not exceed `type(uint48).max`. Add a `require` check during initialization or any setter function for `antiFarmerDuration` to validate this. Alternatively, consider using `uint64` for `antiFarmerExpirationTime` if a longer duration is genuinely needed.


### `I-01` — Truncated Code in `_liquidateTax` Function  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated at the end of a critical conditional statement: `taxAmount >= currentPoolState.liqu... (truncated)`. This prevents a full and accurate assessment of the exact conditions under which tax processing and dividend distribution are triggered.

**Recommendation:** Provide the complete and untruncated source code for a comprehensive audit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa15a...7777`](https://bscscan.com/address/0xa15a6b1b9c256aa42cee7a0947a2404a72ed7777) |
| **Network** | BNB Chain |
| **Price** | $0.0002744 |
| **24h Volume** | $404.8K |
| **Liquidity** | $53.1K |
| **Volume / Liquidity** | 7.6× |
| **Token Age** | 19h |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2467 buys / 1785 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x17e6439085dd424ca1aefb6105cee87e647ecb9d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binancians-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
