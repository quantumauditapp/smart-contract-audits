---
token: HOMER CZ
ticker: HOMER
network: bsc
risk_score: 40
status: medium
date: 2026-09-02
---

# HOMER CZ (HOMER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/homer-cz-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and a multi-state pool management system. It utilizes OpenZeppelin's upgradeable contracts for security and maintainability. A critical limitation of this audit is the truncation of the `_processTax` function, which is central to the token's economic logic and tax liquidation. Without its full implementation, a comprehensive security assessment, particularly regarding reentrancy and external interactions, is not possible. The current analysis identifies a critical missing component, potential reentrancy risk, and centralization concerns.

> **Final Recommendation:** It is imperative to provide the complete source code for the `_processTax` function to enable a thorough security audit, especially concerning reentrancy and external call safety. Once the full code is available, a re-audit should be conducted. Consider implementing a timelock for critical owner-controlled functions like `startMigration` and `finalizeMigration` to introduce a delay for sensitive operations, enhancing security and transparency. Ensure all external interactions within `_processTax` are protected against reentrancy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages OpenZeppelin's upgradeable ERC20 and access control patterns, enhancing code security and maintainability (7.2 Code Security). It correctly uses `SafeERC20` for external token… |
| **Governance / Economics** | 8/10 | Low | The contract's economic model relies on dynamic tax rates and liquidation thresholds, managed through a multi-state system. The `onlyOwner` modifier on `startMigration` and `finalizeMigration` grants… |
| **Upgrades** | 4/10 | Medium | The contract is designed as an upgradeable proxy implementation, using OpenZeppelin's `Initializable` pattern. The `_disableInitializers()` call in the constructor and the `initializer` modifier on… |

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

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Missing Critical Function Implementation (`_processTax`)  *(Severity: Critical · Status: Unresolved)*

The provided source code is truncated, specifically missing the implementation of the `_processTax(uint256 taxAmount)` function. This function is called within `_liquidateTax`, which is invoked on every token transfer. `_processTax` is central to the contract's tax collection and distribution mechanism. Without its full code, a comprehensive security assessment of the core economic logic, external interactions, and potential vulnerabilities (e.g., reentrancy, incorrect accounting) is impossible.

**Recommendation:** Provide the complete and verified source code for the `_processTax` function. A full re-audit of the contract, focusing on this critical component, is required once the code is available.


### `H-01` — Potential Reentrancy in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function modifies the `notLiquidating` state variable (`currentPoolState.notLiquidating = false;` then `true;`) around a call to `_processTax`. If `_processTax` (whose implementation is missing) makes an external call to an untrusted contract (e.g., `taxProcessor`, `dividendContract`, `v2Router`), and that external call re-enters `_liquidateTax` or `_transfer`, it could lead to unexpected behavior or asset manipulation. The `notLiquidating` flag is intended to prevent re-entry into the liquidation logic, but its effectiveness depends entirely on the behavior of the missing `_processTax` function.

**Recommendation:** Once the `_processTax` implementation is available, rigorously audit it for external calls. If external calls are present, ensure they follow the Checks-Effects-Interactions pattern. Consider using a reentrancy guard or OpenZeppelin's `ReentrancyGuard` if multiple external calls are made or if the logic is complex.


### `M-01` — Centralized Control Over Pool State Transitions  *(Severity: Medium · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control critical transitions in the `poolState` (e.g., from `BondingCurve` to `Migrating`, and `Migrating` to `TaxEnforcedAntiFarmer`), are protected by the `onlyOwner` modifier. This grants a single address (the owner) unilateral control over these significant operational changes, posing a centralization risk. A malicious or compromised owner could manipulate the pool state without community consensus.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or integrating a timelock mechanism for these critical state-changing functions. This would introduce a delay before changes take effect, allowing for community review and mitigating risks associated with a single point of failure.


### `L-01` — Reliance on `block.timestamp` for Expiration Times  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function uses `block.timestamp` to determine if `taxExpirationTime` or `antiFarmerExpirationTime` have passed, triggering state changes. While common, `block.timestamp` can be manipulated by miners within a certain range (up to 900 seconds on Ethereum, similar on BSC). This could allow a miner to slightly front-run or delay a state transition, potentially affecting the timing of tax enforcement or anti-farmer periods.

**Recommendation:** For critical time-sensitive operations, consider using `block.number` and calculating time based on average block times, or accept the inherent minor manipulation risk of `block.timestamp`. Given the context of tax periods, this risk is generally low but worth noting.


### `I-01` — Hardcoded `maxSupply` and Initial Minting  *(Severity: Informational · Status: Unresolved)*

The `maxSupply` is declared as a `public constant` with a value of `1e9 ether`. During initialization, the entire `maxSupply` is minted to `msg.sender`. This design choice means the total supply is fixed and fully controlled by the deployer at the outset. While not a vulnerability, it represents a high degree of centralization in initial token distribution.

**Recommendation:** Document this design choice clearly for users and investors. If future decentralization of supply is desired, consider mechanisms for controlled release or distribution beyond the initial deployer's address.


### `I-02` — Complex State Machine Logic  *(Severity: Informational · Status: Unresolved)*

The contract implements a multi-state system (`PoolState.BondingCurve`, `Migrating`, `TaxEnforcedAntiFarmer`, `TaxEnforced`, `TaxFree`) with intricate transition conditions and corresponding logic in `_transfer` and `_liquidateTax`. The `PackedPoolState` struct also combines multiple variables into a single storage slot. While this can be efficient, the complexity of the state machine increases the surface area for potential logical errors or unexpected interactions between states, even if no specific bug was identified in the available code.

**Recommendation:** Ensure comprehensive unit and integration tests cover all possible state transitions and edge cases. Consider adding Natspec comments to clearly explain the purpose and conditions for each state and transition.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4f06...7777`](https://bscscan.com/address/0x4f06dba806d66e1caeb37516c0f7a28728067777) |
| **Network** | BNB Chain |
| **Price** | $0.0002909 |
| **24h Volume** | $151.8K |
| **Liquidity** | $60.8K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 7d |
| **Top-10 Holders** | 29.0% of supply |
| **Buy / Sell Tax** | 0.0% / 1.0% |
| **24h Transactions** | 1286 buys / 1483 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6bb5743a627050b72d924cac69945d30cd0ea4e4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/homer-cz-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
