---
token: 金蟾
ticker: JIN
network: bsc
risk_score: 48
status: high
date: 2026-08-14
---

# 金蟾 (JIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jin-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and state transitions. It utilizes OpenZeppelin's upgradeable contracts for security and follows a structured design with a packed state variable. Key findings include high centralization risk due to owner privileges over state transitions and initial token supply, and significant dependency on external contracts for tax processing. Medium risks relate to immutable liquidation thresholds and reliance on block.timestamp for critical state changes. Overall, the contract demonstrates good use of standard libraries but requires careful management of external dependencies and owner responsibilities.

> **Final Recommendation:** It is recommended to thoroughly audit all external contracts, especially `ITaxProcessor`, to ensure their security and intended behavior. Consider implementing a multi-signature wallet or a timelock for critical owner-controlled state transitions to enhance decentralization and provide users with a reaction window. Evaluate the immutability of the `liquidationThreshold` and `block.timestamp` reliance for state changes, and consider making them configurable or using more robust time sources if the economic impact is significant. Finally, address the unused state variable to improve code clarity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's upgradeable contracts, providing a solid foundation for ERC20 functionality and upgradeability (7.1 Architecture). The use of a `PackedPoolState` struct is an… |
| **Governance / Economics** | 2/10 | High | The contract includes a check ensuring `taxDuration` is greater than or equal to `antiFarmerDuration`, which is a positive economic constraint. However, the owner has significant control over… |
| **Upgrades** | 8/10 | Low | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` pattern. The `_disableInitializers()` call in the constructor correctly prevents re-initialization of the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 1 Informational_

### `H-01` — External Contract Dependency Risk  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function makes an external call to `taxProcessor.processTax(taxAmount)`. The security and correctness of the `ITaxProcessor` contract are paramount. If `taxProcessor` is malicious, buggy, or itself vulnerable (e.g., to reentrancy or unauthorized access), it could lead to the loss of all accumulated tax funds held by `FlapTaxTokenV3`. While a reentrancy guard (`notLiquidating`) is present for `_liquidateTax`, it does not mitigate risks stemming from the `taxProcessor`'s own logic or its interactions with other contracts. (7.6 External)

**Recommendation:** Thoroughly audit the `ITaxProcessor` contract and any other external contracts it interacts with. Ensure robust access controls and security measures are in place for `taxProcessor`. Consider implementing a timelock for changing critical external contract addresses if they were mutable (though in this case, `taxProcessor` is immutable after initialization).


### `H-02` — Centralized Control over Token State Transitions  *(Severity: High · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control significant transitions in the token's `PoolState` (e.g., from `BondingCurve` to `Migrating` to `TaxEnforcedAntiFarmer`), are restricted to `onlyOwner`. This grants the owner considerable power to alter the token's economic behavior, including tax enforcement and anti-farmer mechanisms, without community input or a timelock. Additionally, the `initialize` function mints the entire `maxSupply` to the deployer, concentrating initial token supply with the owner. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Consider decentralizing control over critical state transitions through a multi-signature wallet or a decentralized autonomous organization (DAO). Implement a timelock for such sensitive operations to provide users with a window to react. Document the owner's capabilities clearly to manage user expectations.


### `M-01` — Immutable Liquidation Threshold  *(Severity: Medium · Status: Unresolved)*

The `liquidationThreshold` within the `PackedPoolState` struct is initialized to `START_LIQ_THRESHOLD` and remains constant throughout the contract's lifecycle. This fixed threshold dictates when accumulated tax (`balanceOf(address(this))`) is processed by the `taxProcessor`. If market conditions or the protocol's needs change, this immutable threshold might become suboptimal, leading to inefficient tax processing (e.g., processing too frequently with small amounts or accumulating excessively large amounts before processing). The `initialLiquidationThreshold` variable is also set but unused. (7.4 Economic)

**Recommendation:** Consider making the `liquidationThreshold` configurable by a trusted entity (e.g., owner, multisig, or governance) to allow for adjustments based on evolving protocol requirements or market dynamics. If it's intended to be immutable, ensure this design choice is well-justified and documented. Remove the unused `initialLiquidationThreshold` variable to improve code clarity.


### `M-02` — Reliance on `block.timestamp` for Critical State Transitions  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function uses `block.timestamp` to determine if `taxExpirationTime` or `antiFarmerExpirationTime` have passed, triggering changes in the `PoolState` (e.g., to `TaxFree` or `TaxEnforced`). While `block.timestamp` is suitable for relative time checks, miners can manipulate it within a small window (up to 900 seconds on Ethereum, though BSC might differ). This could potentially allow a miner or a sophisticated attacker to slightly influence the timing of these state transitions to their economic advantage, for example, by delaying a block to avoid a tax or accelerating it to trigger a specific state. (7.2 Code Security, 7.4 Economic)

**Recommendation:** For highly sensitive time-dependent logic where even minor manipulation could have significant economic impact, consider using an oracle-based timestamp (e.g., Chainlink Keepers or similar decentralized time services) if precise, unmanipulable timing is critical. Alternatively, ensure the economic impact of minor `block.timestamp` manipulation is acceptable for the protocol.


### `I-01` — Unused State Variable `initialLiquidationThreshold`  *(Severity: Informational · Status: Unresolved)*

The state variable `initialLiquidationThreshold` is set during the `initialize` function but is never subsequently read or used anywhere else in the contract. This indicates dead code, which can increase contract size, deployment costs, and potentially lead to confusion for future developers. (7.2 Code Security)

**Recommendation:** Remove the `initialLiquidationThreshold` variable if it serves no purpose, or integrate it into the contract's logic if it was intended to be used.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x49f5...7777`](https://bscscan.com/address/0x49f5bcab31a86c1ceefa6fb34680ff66bf8a7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001629 |
| **24h Volume** | $201.7K |
| **Liquidity** | $38.6K |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 16h |
| **Top-10 Holders** | 30.0% of supply |
| **Buy / Sell Tax** | 0.1% / 0.0% |
| **24h Transactions** | 1744 buys / 1167 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe31ebd4896df7f7947d2186d581991644a1f7afe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
