---
token: Bicat
ticker: BICAT
network: bsc
risk_score: 55
status: medium
date: 2026-08-30
---

# Bicat (BICAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bicat-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and pool state transitions. It leverages OpenZeppelin's upgradeable standards and includes a reentrancy guard for tax liquidation. However, the audit identified several high-severity issues, including an integer overflow vulnerability in state update logic and significant centralization risks due to owner-controlled critical functions. Additionally, key economic parameters are inflexible, requiring contract upgrades for adjustments, and the complex transfer logic increases the potential for subtle bugs. These findings collectively contribute to a 'High' overall risk level.

> **Final Recommendation:** It is strongly recommended to address the identified integer overflow vulnerability immediately to prevent critical system failures. The project should also consider decentralizing control over critical state transitions by implementing a multi-signature wallet or a time-lock mechanism for owner-privileged functions. Furthermore, introducing owner-controlled functions to update key economic parameters will significantly improve the protocol's adaptability and reduce the need for costly and complex contract upgrades. Thorough testing, especially across all `PoolState` transitions, is advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes OpenZeppelin's upgradeable ERC20, Ownable, and Permit standards, which enhances code security (7.2 Code Security). The `PackedPoolState` struct is efficiently designed for gas… |
| **Governance / Economics** | 5/10 | Medium | The protocol exhibits high centralization, as the `owner` has exclusive control over critical state transitions via `startMigration` and `finalizeMigration` functions (7.3 Access Control, 7.5… |
| **Upgrades** | 4/10 | Medium | The contract correctly implements the OpenZeppelin upgradeable pattern, including `Initializable` and `_disableInitializers()` in the constructor, ensuring proper upgrade safety (7.7 Upgrades).… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Integer Overflow in `finalizeMigration` State Updates  *(Severity: High · Status: Unresolved)*

In the `finalizeMigration` function, the `taxExpirationTime` and `antiFarmerExpirationTime` are updated by adding `block.timestamp` (and `antiFarmerDuration`) and then casting the result to `uint64` and `uint48` respectively. Since `block.timestamp` is a `uint256`, the sum is performed in `uint256` arithmetic. If this sum exceeds the maximum value of `uint64` or `uint48`, the explicit cast will truncate the higher bits, leading to an integer overflow and an incorrect, potentially much smaller, expiration time. This could prematurely expire tax enforcement or anti-farmer measures, disrupting the protocol's economic model.

**Recommendation:** Before performing the addition and cast, implement a check to ensure the sum does not exceed the maximum value of the target type (`type(uint64).max` or `type(uint48).max`). If an overflow is detected, revert the transaction or implement a robust strategy to handle such large timestamp values, potentially by using larger integer types for these expiration times if feasible.


### `H-02` — Centralized Control Over Critical State Transitions  *(Severity: High · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which are responsible for transitioning the contract's `PoolState` (e.g., from `BondingCurve` to `Migrating` and then to `TaxEnforcedAntiFarmer`), are protected by the `onlyOwner` modifier. This grants a single address (the contract owner) complete and immediate control over the activation and deactivation of core tax mechanisms and anti-farmer measures. This high degree of centralization introduces a significant single point of failure and trust, as a compromised or malicious owner could manipulate the protocol's economic behavior without external checks.

**Recommendation:** To mitigate this centralization risk, consider implementing a multi-signature wallet for the owner address. Alternatively, introduce a time-lock mechanism for these critical state transition functions, allowing a grace period for community review or intervention. For long-term decentralization, explore transitioning to a community-governed voting mechanism for such sensitive operations.


### `M-01` — Inflexibility of Key Economic Parameters  *(Severity: Medium · Status: Unresolved)*

Several critical economic parameters, including `buyTaxRate`, `sellTaxRate`, `taxProcessor` address, `dividendContract` address, and `initialLiquidationThreshold` (which sets `liquidationThreshold` in `PackedPoolState`), are set exclusively during the `initialize` function and lack owner-controlled functions for subsequent modification. This inflexibility means that if market conditions change, or if the external `taxProcessor` or `dividendContract` addresses need to be updated (e.g., due to a bug, upgrade, or change in strategy), the entire contract would require an upgrade. This is a more complex, costly, and risky operation than simply updating a parameter.

**Recommendation:** Implement owner-controlled functions (e.g., `setTaxRates`, `setTaxProcessor`, `setDividendContract`, `setLiquidationThreshold`) to allow for the adjustment of these critical parameters. These functions should be protected by appropriate access controls (e.g., `onlyOwner` or multi-sig) and could benefit from time-locks to provide transparency and prevent immediate malicious changes.


### `M-02` — Potential Flash Loan Manipulation of Liquidation Timing  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function's execution, specifically the processing of accumulated tax, is triggered when `balanceOf(address(this))` exceeds `currentPoolState.liquidationThreshold` (or if the state becomes `TaxFree`). A malicious actor could potentially use a flash loan to temporarily inflate the contract's token balance by sending a large amount of tokens to the contract address just before a transaction that triggers `_liquidateTax`. This could force a premature liquidation, or conversely, prevent a liquidation if the balance is manipulated below the threshold, potentially disrupting the intended tax processing schedule and economic model.

**Recommendation:** Re-evaluate the `liquidationThreshold` mechanism. Consider alternative triggers for tax processing that are less susceptible to temporary balance manipulations, such as a time-weighted average balance or a fixed time interval. Ensure the `taxProcessor` contract is robust against unexpected or frequent calls and that its economic model can withstand potential timing manipulations.


### `L-01` — Complex `_transfer` Logic  *(Severity: Low · Status: Unresolved)*

The `_transfer` function contains multiple nested `if/else if` statements that dictate behavior based on the `PoolState` enum. This complex branching logic, while functional, can make the code harder to read, reason about, and audit. Increased complexity inherently raises the likelihood of subtle bugs or unintended interactions between different states, especially during future modifications or upgrades.

**Recommendation:** Consider refactoring the `_transfer` function to reduce its complexity. This could involve adopting a more explicit state machine pattern or breaking down the logic into smaller, more focused internal functions, each responsible for handling a specific `PoolState`. Comprehensive unit and integration testing, particularly covering all possible state transitions and edge cases, is crucial.


### `I-01` — Immutable Thresholds Limit Future Flexibility  *(Severity: Informational · Status: Unresolved)*

The `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` variables are declared as `immutable`. While this design choice ensures their values cannot be changed after deployment, it also means that if these initial parameters prove suboptimal or require adjustment in the future due to evolving market conditions or protocol needs, a full contract upgrade or redeployment would be necessary. This limits the protocol's adaptability without a more significant operational overhead.

**Recommendation:** This is a design decision. If long-term flexibility for these parameters is desired, they should be made mutable and controlled by the owner or a governance mechanism. If immutability is the intended design, ensure the initial values are thoroughly vetted and understood to be suitable for the protocol's entire lifecycle.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdbc6...7777`](https://bscscan.com/address/0xdbc6333a7d8bcd95f96641eda4d095e69f207777) |
| **Network** | BNB Chain |
| **Price** | $0.00028 |
| **24h Volume** | $237.2K |
| **Liquidity** | $68.8K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 22d |
| **Top-10 Holders** | 25.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 639 buys / 543 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb366d9e23acc1f71c421e04d3fce92c417ce63ce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bicat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
