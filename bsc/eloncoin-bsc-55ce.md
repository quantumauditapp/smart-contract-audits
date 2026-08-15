---
token: ElonCoin
ticker: ELONCOIN
network: bsc
risk_score: 0
status: low
date: 2026-08-15
---

# ElonCoin (ELONCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eloncoin-bsc-55ce)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and state-based pool interactions. The audit identified a potential high-severity reentrancy vulnerability due to an external call within the transfer flow, and medium-severity concerns regarding the immutability of critical external contract addresses. A full assessment of the `_processTax` function was limited due to truncated code.

> **Final Recommendation:** It is highly recommended to address the potential reentrancy vulnerability by implementing a reentrancy guard in the `_transfer` function or ensuring that `_processTax` cannot cause reentrant calls. Consider adding owner-controlled functions to update the `taxProcessor` and `dividendContract` addresses to enhance operational flexibility. Thoroughly review the complex state transition logic in `_liquidateTax` for all possible edge cases, and ensure the complete `_processTax` function is audited.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's upgradeable standards and SafeERC20 for secure token operations (7.2 Code Security). Gas optimizations are present through the `PackedPoolState` struct (7.1… |
| **Governance / Economics** | 9/10 | Low | The contract implements a multi-state tax system with owner-controlled migration phases, providing flexibility in token economics (7.4 Economic, 7.5 Governance). Owner privileges are appropriately… |
| **Upgrades** | 10/10 | Low | The contract correctly implements the OpenZeppelin upgradeable pattern, including `Initializable` and `_disableInitializers()` in the constructor (7.7 Upgrades). Immutable variables are properly… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Potential Reentrancy in `_transfer` via `_processTax`  *(Severity: High · Status: Unresolved)*

The `_transfer` function calls `_liquidateTax`, which in turn calls `_processTax` (an external call to `taxProcessor`). While `_liquidateTax` uses a `notLiquidating` flag to prevent reentrant calls to itself, the `_transfer` function itself does not have a reentrancy guard. If the `_processTax` external call can reenter the token contract (e.g., by calling `transfer` or `transferFrom`), it could lead to unexpected behavior, state manipulation, or double-spending before the initial `_transfer` completes. The re-reading of `poolState` after `_processTax` further suggests potential state changes by the external call.

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_transfer` function or ensure that the `_processTax` function (and the `taxProcessor` contract) is designed to be non-reentrant. Follow the Checks-Effects-Interactions pattern strictly, ensuring all state changes are completed before any external calls.


### `M-01` — Immutability of `taxProcessor` and `dividendContract` Addresses  *(Severity: Medium · Status: Unresolved)*

The addresses for `taxProcessor` and `dividendContract` are set only during the `initialize` function and cannot be modified later. This design choice introduces rigidity (7.8 Operations). If these external contracts need to be updated, replaced due to vulnerabilities, or if their addresses change for any reason, the `FlapTaxTokenV3` contract itself would require an upgrade. Contract upgrades are more complex, costly, and carry higher risk than simply updating an address via an owner-controlled function.

**Recommendation:** Consider adding owner-controlled functions (e.g., `setTaxProcessor(address newProcessor)`) to allow the owner to update the `taxProcessor` and `dividendContract` addresses. This would provide greater operational flexibility and reduce the need for full contract upgrades for simple address changes. Ensure appropriate access control and validation for these setter functions.


### `L-01` — Complex State Transition Logic in `_liquidateTax`  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function contains intricate conditional logic for transitioning between `PoolState`s (`TaxFree`, `TaxEnforced`, `TaxEnforcedAntiFarmer`) based on `block.timestamp` and `liquidationThreshold`. While the current logic appears sound, complex state machines are inherently prone to subtle bugs or edge cases that might not be immediately apparent during initial review. Misconfigurations of `taxExpirationTime`, `antiFarmerExpirationTime`, or `liquidationThreshold` could lead to unexpected state transitions or tax processing behavior.

**Recommendation:** Thoroughly review and test all possible scenarios and edge cases for the state transition logic in `_liquidateTax`. Consider adding comprehensive unit tests and formal verification if possible, to ensure the state machine behaves as intended under all conditions. Document the expected behavior for each state transition clearly.


### `I-01` — Truncated Code for `_processTax` Function  *(Severity: Informational · Status: Unresolved)*

The provided source code for `FlapTaxTokenV3.sol` is truncated, specifically the implementation of the `_processTax` function within `_liquidateTax`. This function is critical for the core tax processing mechanism and involves an external call to `taxProcessor`. Without the complete code for `_processTax`, a full and comprehensive security assessment of the tax handling, external interactions, and potential vulnerabilities (e.g., reentrancy, gas limits, error handling) cannot be performed.

**Recommendation:** Provide the complete and untruncated source code for all relevant contracts, especially `_processTax` and the `ITaxProcessor` interface implementation, to enable a full security audit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x499c...7777`](https://bscscan.com/address/0x499c573997a1382f4051ece45b3d6b2f0e317777) |
| **Network** | BNB Chain |
| **Price** | $0.0003857 |
| **24h Volume** | $206.1K |
| **Liquidity** | $67.7K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 10d |
| **Top-10 Holders** | 29.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1081 buys / 902 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe7f3445ed7593770e5301793057f48878c6788b4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eloncoin-bsc-55ce)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
