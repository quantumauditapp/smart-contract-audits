---
token: 施工猫
ticker: SUE
network: bsc
risk_score: 30
status: low
date: 2026-08-30
---

# 施工猫 (SUE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sue-bsc)

---

## Audit Summary

The audit of FlapTaxTokenV3 identified a critical dependency on an unaudited `_processTax` function, which is essential for the token's core tax mechanism. A high-severity bug was found in the `taxExpirationTime` calculation during migration, potentially leading to incorrect tax durations. The contract exhibits a medium level of owner centralization for state transitions.

> **Final Recommendation:** Prioritize a comprehensive audit of the `ITaxProcessor` contract and the `_processTax` function, as it is a critical dependency for the token's core functionality. Immediately address the `taxExpirationTime` calculation bug in `finalizeMigration` to ensure correct tax period enforcement. Consider implementing a multi-signature wallet for owner-controlled functions to mitigate centralization risks and enhance security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements an upgradeable ERC20 token with a multi-state tax mechanism (7.1 Architecture). It leverages OpenZeppelin's battle-tested libraries for core ERC20 and access control… |
| **Governance / Economics** | 7/10 | Low | The contract design grants the owner significant control over critical state transitions, such as `startMigration` and `finalizeMigration`, which directly impact the token's tax rates and transfer… |
| **Upgrades** | 4/10 | Medium | The contract correctly utilizes OpenZeppelin's `Initializable` pattern and `_disableInitializers()` in the constructor, ensuring proper upgradeability (7.7 Upgrades). Immutable variables are… |

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

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing Critical External Dependency (`_processTax`)  *(Severity: Critical · Status: Unresolved)*

The `_processTax` function, which is central to the token's tax mechanism and liquidation process, is called internally but its implementation is not provided in the audited code. This function is responsible for handling accumulated tax tokens and is called within a reentrancy-guarded block. Without the full implementation of `_processTax` and the `ITaxProcessor` interface, it is impossible to assess potential reentrancy vulnerabilities, economic exploits, or denial-of-service risks within this critical component.

**Recommendation:** Provide the complete source code for the `ITaxProcessor` contract and the `_processTax` function for a comprehensive security review. Ensure that `_processTax` adheres to best practices for external calls, including reentrancy guards and gas efficiency.


### `H-01` — Incorrect `taxExpirationTime` Calculation in `finalizeMigration`  *(Severity: High · Status: Unresolved)*

In the `finalizeMigration` function, the `taxExpirationTime` is calculated as `currentPoolState.taxExpirationTime + block.timestamp`. The `currentPoolState.taxExpirationTime` is initially set to `params.taxDuration` in the `initialize` function. This results in the expiration time being `params.taxDuration + block.timestamp` (from epoch) plus the current `block.timestamp`, effectively doubling the current time component. This will lead to an incorrect and significantly longer tax enforcement period than intended.

**Recommendation:** Correct the calculation of `taxExpirationTime` in `finalizeMigration`. It should likely be `uint64(block.timestamp + params.taxDuration)` or `uint64(block.timestamp + antiFarmerDuration)` if `params.taxDuration` is intended as a duration from the point of finalization, similar to how `antiFarmerExpirationTime` is set.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control critical `poolState` transitions and thus the token's tax mechanisms and transfer restrictions, are protected by the `onlyOwner` modifier. This grants a single address (the owner) significant power to unilaterally alter the token's core economic behavior, introducing a single point of failure and a high degree of trust in the owner.

**Recommendation:** Consider implementing a multi-signature wallet for the contract owner to manage critical functions. Alternatively, introduce a time-lock mechanism or a decentralized governance process for sensitive state transitions to reduce reliance on a single entity.


### `L-01` — Potential High Gas Costs for `_liquidateTax`  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function is called on every `_transfer` operation. If the `_processTax` function (whose implementation is unknown) is gas-intensive, or if the accumulated `taxAmount` (balance of `address(this)`) becomes very large, frequent transfers could lead to increased transaction costs or even potential transaction failures if `_processTax` exceeds block gas limits. While a reentrancy guard is in place, gas efficiency remains a concern.

**Recommendation:** Ensure the `_processTax` function is highly optimized for gas efficiency. Consider implementing a mechanism to cap the amount of tax processed in a single call or to allow for manual processing by the owner if automatic liquidation becomes too expensive.


### `I-01` — Unused State Variables  *(Severity: Informational · Status: Unresolved)*

Several state variables are initialized in the `initialize` function but are not subsequently used anywhere in the provided contract code. These include `liqExpectedOutputAmount`, `quoteToken`, `dividendContract`, and `initialLiquidationThreshold`. This could indicate incomplete features, dead code, or potential confusion for future development and auditing.

**Recommendation:** Review these unused variables. If they are not intended for future use, remove them to improve code clarity and reduce contract size. If they are part of incomplete features, document their intended purpose and consider their full implementation or removal.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2ab8...7777`](https://bscscan.com/address/0x2ab8a4dd2191989ac2898006df350b236d2b7777) |
| **Network** | BNB Chain |
| **Price** | $0.0006347 |
| **24h Volume** | $742.9K |
| **Liquidity** | $106.6K |
| **Volume / Liquidity** | 7.0× |
| **Token Age** | 5d |
| **Top-10 Holders** | 26.0% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 2847 buys / 2757 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xffca411cfbcd3194503effa80fd394b55387915c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sue-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
