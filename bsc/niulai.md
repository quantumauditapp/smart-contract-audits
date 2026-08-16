---
token: niulai
ticker: NIULAI
network: bsc
risk_score: 48
status: high
date: 2026-08-16
---

# niulai (NIULAI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/niulai-bsc)

---

## Audit Summary

The CosmTaxToken contract implements an ERC-20 token with a complex tax mechanism and a multi-state machine. A critical vulnerability was identified where the `_processTax` function, essential for handling accumulated tax tokens, is missing its implementation. Additionally, the contract uses upgradeable patterns but appears to be deployed directly, indicating a potential architectural mismatch. High owner privileges and complex internal logic also contribute to the overall risk profile.

> **Final Recommendation:** Address the critical missing `_processTax` implementation immediately to ensure the core tax mechanism functions as intended. Clarify and align the contract's upgradeability strategy; either deploy it behind a proxy if upgrades are desired, or refactor to use standard OpenZeppelin contracts if not. Implement a multi-signature wallet for the owner address to mitigate centralization risks and consider time-locks for highly sensitive administrative actions. Thoroughly review and simplify the `_transfer` logic to enhance maintainability and reduce the potential for errors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes OpenZeppelin's upgradeable ERC20 and Ownable components, demonstrating a foundation of well-audited libraries. It employs a `PackedPoolState` struct for gas efficiency and… |
| **Governance / Economics** | 6/10 | Medium | The contract benefits from a clearly defined `onlyOwner` role for critical administrative functions, such as setting tax exemptions and managing migration states. The tax mechanism includes… |
| **Upgrades** | 4/10 | Medium | The contract is built using OpenZeppelin's upgradeable contracts and the `initializer` pattern, suggesting an intent for future upgradeability. This provides a robust framework for potential future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing Critical Functionality (`_processTax`)  *(Severity: Critical · Status: Unresolved)*

The `_processTax` internal function, which is crucial for handling accumulated tax tokens, is called within `_liquidateTax` but its implementation is entirely missing from the provided source code. This renders the core tax mechanism non-functional and prevents the protocol from processing and distributing collected taxes, leading to a complete failure of a primary contract feature (7.2 Code Security, 7.8 Operations).

**Recommendation:** Implement the `_processTax` function with the intended logic for tax distribution, liquidity provision, or other specified uses. Ensure it handles external calls securely (e.g., reentrancy guards) and aligns with the protocol's economic model.


### `H-01` — Inconsistent Upgradeability Pattern Usage  *(Severity: High · Status: Unresolved)*

The contract `CosmTaxToken` inherits from OpenZeppelin `Upgradeable` contracts (e.g., `ERC20PermitUpgradeable`, `OwnableUpgradeable`) and uses the `initializer` pattern. However, the provided metadata indicates `is_proxy: false` and `implementation: null`, suggesting it's deployed directly as a standalone contract, not as an implementation behind a proxy. This misapplication of the upgradeability pattern leads to unnecessary complexity, gas overhead, and potentially confusion regarding the contract's intended lifecycle. If direct deployment is intended, `Upgradeable` contracts should not be used. If upgradeability is intended, it must be deployed behind a proxy (7.1 Architecture, 7.7 Upgrad…

**Recommendation:** Clarify the intended deployment strategy. If upgradeability is desired, deploy `CosmTaxToken` as an implementation contract behind a proxy (e.g., UUPS proxy). If upgradeability is not required, refactor the contract to use standard (non-upgradeable) OpenZeppelin contracts and remove the `initializer` pattern.


### `M-01` — High Owner Privileges and Centralization Risk  *(Severity: Medium · Status: Unresolved)*

The `onlyOwner` role has significant control over critical contract parameters and state transitions. Functions like `setDexTaxExempt`, `startMigration`, and `finalizeMigration` allow the owner to unilaterally change the contract's operational state and tax exemptions. This centralization introduces a single point of failure and potential for malicious or compromised owner actions to impact all token holders (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to reduce single-point-of-failure risk. For critical state changes, explore time-locks or governance mechanisms to introduce a delay or community oversight.


### `M-02` — Complex `_transfer` Logic and State Machine  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function contains a complex series of `if-else if` statements based on the `PoolState` enum, leading to multiple execution paths. This complexity increases the likelihood of subtle bugs, unexpected behavior, or edge cases being missed, especially concerning tax calculations and pool interactions. The `_liquidateTax` function, called at the beginning of `_transfer`, also modifies `poolState`, adding to the complexity (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Refactor the `_transfer` logic to improve readability and reduce complexity. Consider using a state-machine pattern with clearer transitions and encapsulated logic for each state. Thoroughly test all possible state transitions and their impact on transfers and tax calculations.


### `L-01` — Reliance on `block.timestamp` for Critical State Transitions  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function uses `block.timestamp` to determine when `taxExpirationTime` and `antiFarmerExpirationTime` have passed, triggering `PoolState` changes. While `block.timestamp` is generally reliable, miners have a limited ability to manipulate it (typically within a few seconds of actual time). This could potentially allow for minor front-running or back-running opportunities for state transitions, though the impact might be limited given the long durations involved (7.4 Economic).

**Recommendation:** For time-sensitive operations, consider using a time oracle or a more robust time-keeping mechanism if the exact timing of state transitions is critical and susceptible to minor manipulation. For durations of days/years, the risk is generally acceptable.


### `I-01` — Unused `MIN_LIQ_THRESHOLD` and `initialLiquidationThreshold`  *(Severity: Informational · Status: Unresolved)*

The `MIN_LIQ_THRESHOLD` immutable variable is set in the constructor but does not appear to be used anywhere else in the provided code. Similarly, `initialLiquidationThreshold` is set in `initialize` but its usage is not visible. The `liquidationThreshold` within `PackedPoolState` is used, but it's initialized with `START_LIQ_THRESHOLD`, not `initialLiquidationThreshold` (7.2 Code Security).

**Recommendation:** Review the contract logic to determine if `MIN_LIQ_THRESHOLD` and `initialLiquidationThreshold` are intended for future use or if they can be removed to reduce contract size and complexity. Ensure that `liquidationThreshold` is correctly managed and updated if `initialLiquidationThreshold` was meant to play a role.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3604...0111`](https://bscscan.com/address/0x3604b5c377124d2180c4fb791953fc8431a90111) |
| **Network** | BNB Chain |
| **Price** | $0.007188 |
| **24h Volume** | $877.2K |
| **Liquidity** | $238.0K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 17h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2865 buys / 1417 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xc91d0280d92e2c89f2c6a984ddafa6cca39c7643)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/niulai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
