---
token: 永生果蝇
ticker: 果蝇
network: bsc
risk_score: 0
status: low
date: 2026-09-20
---

# 永生果蝇 (果蝇) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-b8e413-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex, multi-state tax mechanism. The audit identified a critical reentrancy vulnerability in the `_liquidateTax` function, which performs external calls after modifying internal state but before fully processing the liquidation. Additionally, a critical section of the `_liquidateTax` function was truncated in the provided source code, preventing a complete security analysis of its logic. The contract also exhibits high complexity in its state machine and relies on owner-controlled functions for critical transitions.

> **Final Recommendation:** Address the critical reentrancy vulnerability in `_liquidateTax` by implementing a reentrancy guard or strictly adhering to the Checks-Effects-Interactions pattern. Provide the complete source code for a thorough audit of the truncated `_liquidateTax` function to ensure no hidden vulnerabilities exist. Conduct comprehensive testing of all state transitions and tax scenarios to ensure the economic model behaves as intended. Consider implementing a multi-signature wallet for owner-controlled functions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's upgradeable standards for ERC20, Ownable, and Permit, demonstrating sound architectural choices (7.1 Architecture). The use of `PackedPoolState` is an efficient… |
| **Governance / Economics** | 8/10 | Low | The economic model is built around a dynamic tax mechanism that adjusts based on `PoolState` and time-based expirations, influencing token transfers (7.4 Economic). Critical state transitions, such… |
| **Upgrades** | 9/10 | Low | The contract is implemented as an upgradeable proxy using OpenZeppelin's `Initializable` and `ERC20Upgradeable` patterns, which is a well-established and secure approach for upgradeability (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 11.2% |
| **Top-3 Unlocked** | 28.8% |

## Security Findings

_🟡 5 Medium · 🟢 1 Low_

### `M-01` — Truncated Code Prevents Full Audit  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). A critical section of the `_liquidateTax` function was truncated in the provided source code: `taxAmount >= currentPoolState.liqu... (truncated)`. This prevents a complete and accurate security analysis of the tax liquidation conditions and logic, which is central to the contract's economic model. The missing code could contain additional vulnerabilities, logical flaws, or critical operational details.

**Recommendation:** Provide the complete and untruncated source code for the `FlapTaxTokenV3` contract, specifically the `_liquidateTax` function, to enable a comprehensive security assessment.


### `M-02` — Reliance on External Contracts for Critical Operations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract relies on external addresses, `taxProcessor` and `dividendContract`, for core functionalities such as processing collected taxes and distributing dividends. These addresses are set during initialization and are critical to the token's economic model. If these external contracts are malicious, become compromised, are paused, or are upgraded incorrectly, they could disrupt the token's tax mechanism, prevent dividend distribution, or lead to loss of funds.

**Recommendation:** Ensure that `taxProcessor` and `dividendContract` are thoroughly audited, robust, and have appropriate access controls. Implement mechanisms to pause or replace these external contracts in an emergency, possibly with a time-locked or multi-signature controlled setter function. Clearly document the expected behavior and security properties of these external dependencies.


### `M-03` — Centralization Risk with Owner-Controlled Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `startMigration` and `finalizeMigration` functions, which control critical `PoolState` transitions, are protected by the `onlyOwner` modifier. This grants significant power to a single address to unilaterally change the contract's operational state. While common for initial setup, a compromised owner key or a malicious owner could manipulate the token's behavior, potentially impacting users or the economic model.

**Recommendation:** Consider migrating ownership of critical functions to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and reduce the risk of a single point of failure. For highly sensitive operations, implement a time-lock mechanism to allow community review or provide a window for users to react before changes take effect.


### `M-04` — Reentrancy Vulnerability in `_liquidateTax`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, called during every `_transfer`, performs external calls to `ITaxProcessor(taxProcessor).processTax` and `IDividend(dividendContract).distributeDividend`. These external calls occur after internal state variables (e.g., `poolState`) may have been updated but before the full liquidation process is complete or a reentrancy guard is applied. A malicious `taxProcessor` or `dividendContract` could re-enter the token contract, potentially manipulating balances, triggering unintended state transitions, or causing double-spending of tax amounts before the current transaction is finalized.

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function or strictly follow the Checks-Effects-Interactions pattern. Ensure that all state changes related to tax liquidation are finalized before any external calls are made. Consider setting a `notLiquidating` flag to `false` at the beginning of the function and resetting it only after all external calls and state updates are complete.


### `M-05` — Complex State Machine and Potential for Misconfiguration  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract implements a highly complex state machine with multiple `PoolState` transitions (`BondingCurve`, `Migrating`, `TaxEnforcedAntiFarmer`, `TaxEnforced`, `TaxFree`) and intricate tax calculation logic (`_getTaxWithPoolState`). State changes can occur automatically based on `block.timestamp` in `_liquidateTax` or manually via `onlyOwner` functions. This complexity increases the risk of logical errors, unintended state transitions, or misconfigurations of initial parameters (`taxDuration`, `antiFarmerDuration`, `mainPool`), which could lead to incorrect tax application or economic instability.

**Recommendation:** Thoroughly document all possible state transitions, their triggers, and expected outcomes. Conduct extensive unit and integration testing covering all edge cases and parameter combinations. Consider simplifying the state machine if possible, or adding robust invariant checks to ensure the system remains in a valid state.


### `L-01` — Reliance on `block.timestamp` for Time-Sensitive Operations  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function uses `block.timestamp` to check `taxExpirationTime` and `antiFarmerExpirationTime` for automatic state transitions. Miners have a limited ability to manipulate `block.timestamp` (typically within a 15-second window on Ethereum, but can vary on other chains like BSC). This could allow for minor front-running opportunities to slightly delay or accelerate state changes, potentially affecting tax rates or liquidation timing for specific transactions.

**Recommendation:** Be aware of the inherent limitations and potential for manipulation when using `block.timestamp` for precise timing. For critical time-sensitive operations where even minor manipulation is unacceptable, consider using a decentralized oracle for time or a more robust timing mechanism. For the current use case, the impact is likely low, but it's important to acknowledge the risk.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2b90...7777`](https://bscscan.com/address/0x2b90bb9683383b6a1440e116309ba0187ef67777) |
| **Network** | BNB Chain |
| **Price** | $0.001023 |
| **24h Volume** | $1.27M |
| **Liquidity** | $128.0K |
| **Volume / Liquidity** | 9.9× |
| **Token Age** | 5d |
| **Top-10 Holders** | 16.9% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 5322 buys / 3938 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x189fcfa548968cbd3b0118c2200f05db00d429f1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-b8e413-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
