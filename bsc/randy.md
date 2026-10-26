---
token: Randy
ticker: RANDY
network: bsc
risk_score: 36
status: medium
date: 2026-09-02
---

# Randy (RANDY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/randy-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and a multi-state pool system. The audit identified a critical reentrancy vulnerability in the tax liquidation process and a significant logical error in the calculation of tax expiration times during state transitions. These issues pose substantial risks to the contract's integrity and economic model.

> **Final Recommendation:** Address the reentrancy vulnerability in `_liquidateTax` by implementing a reentrancy guard before the external call to `_processTax`. Correct the `taxExpirationTime` calculation in `finalizeMigration` to ensure accurate duration setting. Review the potential for integer overflow in time-related variables and consider using `uint256` for durations if extremely long periods are intended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes OpenZeppelin's upgradeable standards for ERC20 and access control, demonstrating a commitment to established patterns (7.1 Architecture). The tax calculation logic is generally… |
| **Governance / Economics** | 6/10 | Medium | The contract implements a multi-state system for tax enforcement and migration, with `onlyOwner` functions controlling key state transitions (`startMigration`, `finalizeMigration`) (7.5 Governance).… |
| **Upgrades** | 4/10 | Medium | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` pattern (7.7 Upgrades). The constructor correctly calls `_disableInitializers()`, and the `initialize` function… |

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

_🟡 4 Medium · ⚪ 1 Informational_

### `M-01` — Significant Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` role has extensive control over critical contract functions, including `startMigration` and `finalizeMigration`, which dictate the transition between different `PoolState`s. The owner also controls the `taxProcessor` and `dividendContract` addresses through initialization parameters. While this may be intended for initial setup and operational flexibility, it introduces a single point of failure and trust. A compromised owner key could lead to unauthorized state changes or manipulation of the token's economic model (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` role to reduce the risk associated with a single point of compromise. As the protocol matures, explore decentralizing control through a governance mechanism or time-locked operations for critical functions.


### `M-02` — Potential Integer Overflow in `uint48`/`uint64` Expiration Times  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `taxExpirationTime` (uint64) and `antiFarmerExpirationTime` (uint48) variables store timestamps. Calculations like `block.timestamp + antiFarmerDuration` (where `antiFarmerDuration` is `uint256`) could potentially result in values exceeding the maximum capacity of `uint48` or `uint64` if the durations are extremely long. While `block.timestamp` itself is typically within `uint48` range for many years, adding a very large `antiFarmerDuration` could cause an overflow, leading to incorrect expiration times (7.2 Code Security, 7.4 Economic).

**Recommendation:** Ensure that `antiFarmerDuration` and `taxDuration` parameters are constrained to values that, when added to `block.timestamp`, will not exceed the maximum values of `uint48` or `uint64`. Alternatively, consider using `uint256` for all timestamp-related variables if extremely long durations (beyond ~136 years for `uint48` or ~584 billion years for `uint64`) are a design requirement, or implement explicit overflow checks.


### `M-03` — Reentrancy Vulnerability in `_liquidateTax`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function performs an external call to `_processTax(taxAmount)` on the `taxProcessor` contract. Before this call, `currentPoolState.notLiquidating` is set to `false`, and after the call, it is reset to `true`. If the `taxProcessor` contract is malicious or compromised, it could re-enter `_liquidateTax` or other functions in `FlapTaxTokenV3` before `notLiquidating` is reset. This could lead to unexpected state changes, double-spending of collected taxes, or other malicious actions. This is a classic reentrancy pattern (7.2 Code Security, 7.6 External).

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function or ensure that all state changes related to `notLiquidating` are completed *before* any external calls are made. Alternatively, consider a 'checks-effects-interactions' pattern.


### `M-04` — Incorrect `taxExpirationTime` Calculation in `finalizeMigration`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `finalizeMigration` function, the `taxExpirationTime` is updated with `currentPoolState.taxExpirationTime + block.timestamp`. The `currentPoolState.taxExpirationTime` is initialized with `params.taxDuration` in `initialize`. Adding `block.timestamp` to an already set duration (which is likely intended to be a future timestamp) will result in an incorrect and potentially extremely long or unintended expiration time. This logic error could lead to taxes being enforced for a much longer period than intended, impacting the token's economic model (7.4 Economic, 7.2 Code Security).

**Recommendation:** The `taxExpirationTime` should be set to `block.timestamp + params.taxDuration` (or a similar calculation based on the intended duration from the current time) in `finalizeMigration`, not `currentPoolState.taxExpirationTime + block.timestamp`. Review the intended behavior for `taxExpirationTime` and correct the calculation accordingly.


### `I-01` — High Complexity in `_liquidateTax` and Pool State Machine  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is invoked on every transfer to `mainPool` and is responsible for multiple state transitions, tax processing, and liquidation logic. The overall `PoolState` machine, with its five distinct states and various transition conditions, adds significant complexity to the contract. Complex logic increases the surface area for potential bugs and makes auditing and reasoning about the contract's behavior more challenging (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Consider refactoring `_liquidateTax` into smaller, more focused functions to improve readability and maintainability. Thoroughly document the state machine transitions and their conditions to ensure clarity and prevent unintended behavior. Implement comprehensive unit tests for all state transitions and tax calculation scenarios.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4154...7777`](https://bscscan.com/address/0x4154b19017a63d054ad1888bbde1e188253a7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001356 |
| **24h Volume** | $52.2K |
| **Liquidity** | $48.6K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 7d |
| **Top-10 Holders** | 40.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 536 buys / 421 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x62c806cdcb6e97b3a83d8e4e715c05d66e71a080)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/randy-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
