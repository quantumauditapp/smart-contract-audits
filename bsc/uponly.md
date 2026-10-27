---
token: UPONLY
ticker: UPONLY
network: bsc
risk_score: 21
status: low
date: 2026-09-13
---

# UPONLY (UPONLY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uponly-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and a multi-state machine. It utilizes OpenZeppelin's upgradeable contracts, which is a strong foundation. The audit identified a High-severity integer overflow risk in state transition logic, along with Medium-severity concerns regarding incomplete tax liquidation logic and reliance on specific transfer patterns. Centralization risks due to owner privileges are also noted. The upgradeability pattern is correctly implemented.

> **Final Recommendation:** Address the identified integer overflow/truncation vulnerability by ensuring safe arithmetic for timestamp calculations. Complete and thoroughly review the `_liquidateTax` function, explicitly defining the role of the `notLiquidating` flag and ensuring robust reentrancy protection if external calls are made. Consider implementing a fallback mechanism for tax liquidation that does not solely rely on transfers to the `mainPool` to prevent accumulation issues. Evaluate the extent of owner privileges and consider implementing multi-signature control or time-locks for critical functions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 and access control modules, providing a robust technical foundation (7.1 Architecture, 7.2 Code Security). The tax calculation logic is… |
| **Governance / Economics** | 5/10 | Medium | The contract implements a complex multi-state machine for tax enforcement and migration, which can be difficult to manage and audit (7.4 Economic). The owner has significant control over state… |
| **Upgrades** | 9/10 | Low | The contract is designed as an upgradeable proxy implementation using OpenZeppelin's `Initializable` pattern (7.7 Upgrades). The `_disableInitializers()` is correctly called in the constructor, and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Incomplete `_liquidateTax` Logic and Unused `notLiquidating` Flag  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is truncated in the provided source, preventing a full security analysis. However, the `PackedPoolState.notLiquidating` flag is initialized to `true` but is never set to `false` within the visible code. If this flag is intended as a reentrancy guard or to indicate an active liquidation process, its current implementation is incomplete. Without a full view of the function, there's a risk of reentrancy vulnerabilities if external calls are made (e.g., to `taxProcessor` or `dividendContract`) before state updates are finalized or if the flag is not properly managed.

**Recommendation:** Provide the complete `_liquidateTax` function for a thorough review. If `notLiquidating` is intended as a reentrancy guard, implement the Checks-Effects-Interactions pattern: set `notLiquidating` to `false` at the start of the liquidation, perform all state changes, make external calls, and then set `notLiquidating` back to `true`. Ensure all external calls are handled safely, preferably using `SafeERC20` for token transfers and reentrancy guards for arbitrary calls.


### `M-02` — Reliance on `mainPool` Transfers for Tax Liquidation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, responsible for processing accumulated tax, is only triggered when a transfer is made *to* the `mainPool` (`to == mainPool`). If transfers to the `mainPool` become infrequent or cease entirely, the accumulated tax (`balanceOf(address(this))`) will not be processed or distributed. This could lead to a large amount of tokens accumulating in the contract, delaying distributions to `taxProcessor` or `dividendContract`, and potentially impacting the protocol's economic stability.

**Recommendation:** Implement a mechanism to allow for manual or scheduled tax liquidation by the owner or a trusted role, independent of transfers to the `mainPool`. Alternatively, consider a more generalized trigger for liquidation, such as a time-based check or a minimum accumulated tax threshold, to ensure timely processing of funds.


### `M-03` — Integer Overflow/Truncation in `finalizeMigration` Timestamp Calculations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `finalizeMigration` function, `currentPoolState.taxExpirationTime` (uint64) and `currentPoolState.antiFarmerExpirationTime` (uint48) are updated by adding `block.timestamp` (uint256) and `antiFarmerDuration` (uint256). If the sum of these values exceeds the maximum capacity of `uint64` or `uint48` respectively, the result will silently truncate, leading to incorrect expiration times. This could cause tax periods or anti-farmer durations to end prematurely or extend indefinitely, disrupting the contract's economic model.

**Recommendation:** Ensure that timestamp calculations are performed safely. Cast `block.timestamp` and `antiFarmerDuration` to the target `uint` size *before* addition, or use a larger `uint` type for intermediate calculations and then check for overflow before casting back. For example, `uint64(uint256(currentPoolState.taxExpirationTime) + block.timestamp)` with an explicit overflow check, or simply use `uint256` for these variables if their maximum values can exceed `uint64`.


### `L-01` — Centralization Risk with Owner Privileges  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` role holds significant control over critical contract parameters and state transitions. Functions like `startMigration`, `finalizeMigration`, and the ability to set `taxProcessor` and `dividendContract` addresses are restricted to the owner. While common in early-stage projects, this centralization introduces a single point of failure and relies heavily on the security of the owner's private key. A compromised owner key could lead to unauthorized state changes or redirection of funds.

**Recommendation:** Consider implementing a multi-signature wallet for the owner role to distribute control among multiple trusted parties. For highly sensitive operations, explore the use of time-locks to introduce a delay between a decision and its execution, allowing for community review or emergency intervention.


### `I-01` — Complex Multi-State Machine  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract implements a complex multi-state machine (`BondingCurve`, `Migrating`, `TaxEnforcedAntiFarmer`, `TaxEnforced`, `TaxFree`) with various conditions for transitions and tax application. This complexity, while potentially offering flexibility, increases the cognitive load for auditors and developers, making it more challenging to reason about all possible execution paths and potential edge cases. This can lead to subtle logic errors or unexpected behavior in specific state transitions or interactions.

**Recommendation:** Thoroughly document the state machine, including all possible states, transition conditions, and their implications for tax calculation and contract behavior. Consider using formal verification tools or extensive unit testing to ensure all state transitions and their effects are correctly implemented and behave as intended under various scenarios.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x06f7...7777`](https://bscscan.com/address/0x06f7aeabc9c37d457922a9368f291c5d57c07777) |
| **Network** | BNB Chain |
| **Price** | $0.0005772 |
| **24h Volume** | $534.2K |
| **Liquidity** | $84.3K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | 43.0% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 2230 buys / 1943 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1f12111deb29e8ae246aa53f17839fe778a217ba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uponly-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
