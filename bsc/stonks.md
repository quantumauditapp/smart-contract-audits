---
token: Stonks
ticker: STONKS
network: bsc
risk_score: 0
status: low
date: 2026-09-13
---

# Stonks (STONKS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonks-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex tax mechanism and a multi-state pool system. It leverages OpenZeppelin's upgradeable contracts for security and modularity. However, a critical portion of the `_liquidateTax` function, which governs state transitions and tax processing, is truncated in the provided source code. This truncation prevents a full security assessment of its security and economic implications, introducing significant uncertainty regarding potential vulnerabilities like reentrancy and the overall stability of the liquidation process.

> **Final Recommendation:** Prioritize resolving the issue of the truncated `_liquidateTax` function by providing the complete and verified source code for a thorough security review. Conduct a comprehensive analysis of the full liquidation logic, specifically looking for reentrancy vectors, potential denial-of-service conditions, and economic manipulation risks. Implement robust monitoring for owner-controlled functions and external contract interactions to ensure transparency and detect unauthorized actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes OpenZeppelin's upgradeable ERC20 standards, enhancing code security and modularity (7.2 Code Security). The `PackedPoolState` struct demonstrates an effort towards gas… |
| **Governance / Economics** | 8/10 | Low | The contract's economic model is centered around a dynamic tax mechanism and a multi-state system, designed to manage token liquidity and anti-farmer measures (7.4 Economic). Key state transitions… |
| **Upgrades** | 9/10 | Low | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's upgradeable contracts, including `Initializable` and `_disableInitializers()` in the constructor, which is a strong… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.6% |
| **Top-3 Unlocked** | 70.9% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control over Key State Transitions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `startMigration` and `finalizeMigration` functions are restricted to the `onlyOwner`. These functions control significant changes in the token's operational `PoolState` (e.g., from `BondingCurve` to `Migrating`, and then to `TaxEnforcedAntiFarmer`). This centralized control means a single compromised owner key or a malicious owner could unilaterally alter the token's tax structure and operational phase, potentially leading to unexpected economic consequences or user distrust (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for the owner address or introducing a time-locked governance mechanism for critical state transitions. This would add an extra layer of security and decentralization, reducing the risk associated with a single point of control.


### `M-02` — Potential Reentrancy in `_liquidateTax` (Unconfirmed due to truncation)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called within `_transfer`, and its full implementation is truncated. If the complete logic involves external calls (e.g., to `ITaxProcessor` or `IDividend` for processing taxes or dividends) and modifies state before or after these calls without proper reentrancy guards (like Checks-Effects-Interactions pattern or reentrancy locks), it could be vulnerable to reentrancy attacks. An attacker could repeatedly call `_transfer` while the contract is in an inconsistent state, leading to unintended behavior or loss of funds (7.2 Code Security).

**Recommendation:** Once the full `_liquidateTax` source code is available, thoroughly review it for any external calls. Ensure that all state changes occur before any external calls are made (Checks-Effects-Interactions pattern) and consider using a reentrancy guard if multiple external calls or complex interactions are necessary.


### `M-03` — Incomplete Liquidation Logic in `_liquidateTax`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, which is called on every transfer to the `mainPool` and is responsible for critical state transitions and potential tax liquidation, is truncated in the provided source code. The incomplete condition `taxAmount >= currentPoolState.liqu...` prevents a full assessment of the liquidation mechanism, its triggers, and its economic implications. This poses a significant risk as the core logic governing tax handling and state changes cannot be fully audited for vulnerabilities such as reentrancy, economic exploits, or denial of service.

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function. A full audit of this critical component is necessary to ensure the contract's security and economic stability. Without the full code, the system's behavior under various conditions, especially during liquidation, remains unknown and potentially exploitable.


### `L-01` — Reliance on `block.timestamp` for Critical State Transitions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function uses `block.timestamp` to determine `PoolState` transitions, specifically for `taxExpirationTime` and `antiFarmerExpirationTime`. While common, `block.timestamp` can be manipulated by miners within a certain range (up to 900 seconds on Ethereum, similar on BSC). This could allow a miner or a sophisticated attacker to slightly front-run or delay state changes, potentially gaining a minor advantage or causing a slight disruption to the intended timing of tax-related events (7.2 Code Security).

**Recommendation:** For time-sensitive operations where precise timing is critical, consider using a more robust time oracle or a time-averaged block number if the exact second is not paramount. If `block.timestamp` is deemed acceptable for the current use case, acknowledge the inherent miner manipulability and ensure the system's economics are resilient to minor time shifts.


### `I-01` — Complex State Machine  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract implements a multi-state `PoolState` machine (BondingCurve, Migrating, TaxEnforcedAntiFarmer, TaxEnforced, TaxFree) with transitions managed by `onlyOwner` functions and the `_liquidateTax` function. While providing flexibility, this complexity increases the surface area for logical errors, makes the system harder to reason about, and can complicate future upgrades or maintenance (7.1 Architecture).

**Recommendation:** Ensure comprehensive unit and integration tests cover all possible state transitions and edge cases. Maintain clear documentation of the state machine's logic, including transition conditions and effects, to aid in future development and security reviews.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc9d8...7777`](https://bscscan.com/address/0xc9d825e83aada475bd4d38c8ca984ed746277777) |
| **Network** | BNB Chain |
| **Price** | $0.00156 |
| **24h Volume** | $485.7K |
| **Liquidity** | $184.3K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 8d |
| **Top-10 Holders** | 21.2% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 2076 buys / 1346 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdb6f1d044b8b2887a6c450d0d13176c81e3f936d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonks-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
