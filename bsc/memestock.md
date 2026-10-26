---
token: memestock
ticker: MEMESTOCK
network: bsc
risk_score: 18
status: low
date: 2026-08-30
---

# memestock (MEMESTOCK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/memestock-bsc)

---

## Audit Summary

The audit of FlapTaxTokenV3 identified a critical vulnerability due to missing code for the `_processTax` function, which is essential for assessing reentrancy and external call risks. The contract implements an upgradeable ERC20 token with dynamic tax mechanisms and state transitions controlled by the owner. While the architecture is sound and leverages OpenZeppelin standards, the incomplete code prevents a full security assessment.

> **Final Recommendation:** Prioritize providing the complete implementation of the `_processTax` function and the remainder of `_liquidateTax` to address the critical missing code vulnerability. Implement a timelock for owner-controlled state transitions to enhance transparency and provide users with reaction time. Review the immutability of economic parameters to ensure long-term adaptability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's upgradeable standards for ERC20 and access control, demonstrating a solid architectural foundation (7.1 Architecture). Gas optimizations are evident through… |
| **Governance / Economics** | 7/10 | Low | The contract's economic model includes dynamic buy/sell taxes and liquidation thresholds, managed through various `PoolState`s. The owner has significant control over these states via… |
| **Upgrades** | 4/10 | Medium | The contract correctly implements the `Initializable` pattern from OpenZeppelin, including `_disableInitializers()` in the constructor and proper `__init` calls (7.7 Upgrades). This indicates a UUPS… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 88.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Pool State Transitions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `startMigration` and `finalizeMigration` functions, restricted to the contract owner, allow unilateral changes to the `PoolState` (e.g., from `BondingCurve` to `Migrating` to `TaxEnforcedAntiFarmer`). These state changes directly impact transfer restrictions and tax application, potentially leading to unexpected behavior or economic implications for users without prior notice.

**Recommendation:** Implement a timelock for critical state transitions to provide users with a grace period to react. Clearly document the implications of each pool state and the owner's ability to change them. Consider using a multi-signature wallet for ownership to distribute control.


### `M-02` — Incomplete `_liquidateTax` Function (Missing `_processTax` Implementation)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided code snippet for `_liquidateTax` is truncated, specifically the `_processTax(taxAmount)` call and subsequent state updates. This external call is crucial for handling collected taxes and could introduce reentrancy vulnerabilities, external call risks, or incorrect tax processing if not properly implemented and secured. Without the full implementation, a complete security assessment is impossible.

**Recommendation:** Provide the full implementation of `_processTax` and the remainder of `_liquidateTax` for a complete security assessment. Ensure `_processTax` adheres to the Checks-Effects-Interactions pattern, handles potential reentrancy, and correctly manages tax funds.


### `L-01` — Reliance on `block.timestamp` for Critical Expiration Logic  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function uses `block.timestamp` to determine if `taxExpirationTime` or `antiFarmerExpirationTime` has passed, triggering state changes. Miners can slightly manipulate `block.timestamp` (within a certain range), potentially influencing the exact block at which these state transitions occur.

**Recommendation:** While common, for highly time-sensitive or economically critical transitions, acknowledge the inherent miner manipulability. For most cases, `block.timestamp` is acceptable, but the risk should be understood. If absolute precision is required, consider a decentralized oracle for time.


### `I-01` — Immutable Liquidation Thresholds  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` variables are declared as `immutable`, fixing their values at deployment. While this provides predictability, it removes the flexibility to adjust these critical economic parameters in response to evolving market conditions or protocol needs.

**Recommendation:** Assess whether these thresholds are truly intended to be immutable for the lifetime of the contract. If future flexibility is desired, consider making them configurable by the owner or governance, potentially with a timelock.


### `I-02` — All `maxSupply` Minted to Initializer  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function mints the entire `maxSupply` of tokens to `msg.sender` (the initializer/owner). This centralizes the initial token supply, which might not align with decentralization goals or require subsequent manual distribution mechanisms.

**Recommendation:** Ensure this initial distribution strategy aligns with the project's tokenomics and distribution plans. If a more distributed initial supply is desired, consider alternative minting or distribution mechanisms during initialization.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6ff4...7777`](https://bscscan.com/address/0x6ff45323817d1d53bbb8a8dfba9245ae74057777) |
| **Network** | BNB Chain |
| **Price** | $0.9827 |
| **24h Volume** | $400.84M |
| **Liquidity** | $42.00M |
| **Volume / Liquidity** | 9.5× |
| **Token Age** | 17d |
| **Top-10 Holders** | 23.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1166 buys / 1042 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7bdc9582aca6ca25e5db1f2c8e59003b880672cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/memestock-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
