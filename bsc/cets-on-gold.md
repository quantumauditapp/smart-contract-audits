---
token: Cets On Gold
ticker: CETS
network: bsc
risk_score: 35
status: medium
date: 2026-08-31
---

# Cets On Gold (CETS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cets-on-gold-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and a multi-state pool system. The contract utilizes OpenZeppelin's upgradeable standards, ensuring a robust foundation. Key findings include potential risks associated with external calls in the `_processTax` function, which could lead to denial of service or reentrancy if not handled carefully. Additionally, the immutability of critical external addresses post-initialization presents a rigidity risk, and the `_liquidateTax` function's execution on every transfer introduces a single point of failure for all token operations. Several informational findings highlight areas for improved clarity and documentation.

> **Final Recommendation:** Prioritize a thorough audit of the `_processTax` function and all external contracts it interacts with, implementing robust error handling and reentrancy protection. Consider adding owner-controlled update functions for critical external addresses, protected by a timelock or multi-signature wallet, to enhance protocol adaptability. Ensure comprehensive testing covers all state transitions and edge cases within the `_transfer` logic to mitigate potential denial of service risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates a solid technical foundation, leveraging OpenZeppelin's upgradeable ERC20 and access control components (7.2 Code Security, 7.1 Architecture). The `PackedPoolState` struct… |
| **Governance / Economics** | 7/10 | Low | Access control is appropriately managed with `OwnableUpgradeable` for critical state transitions like `startMigration` and `finalizeMigration` (7.3 Access Control). However, several critical external… |
| **Upgrades** | 4/10 | Medium | The contract is designed for upgradeability using OpenZeppelin's `Initializable` pattern (7.7 Upgrades). The `_disableInitializers()` in the constructor and the `initializer` modifier are correctly… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 66.2% |
| **Top-3 Unlocked** | ⚠️ 90.4% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `M-01` — External Call Risk in `_processTax`  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function calls `_processTax` (truncated in the provided code). While `poolState.notLiquidating` acts as a reentrancy guard for the `_liquidateTax` function itself, `_processTax` likely involves external calls (e.g., to `taxProcessor`, `dividendContract`, or `v2Router`). If these external contracts are untrusted, compromised, or contain vulnerabilities, they could lead to unexpected behavior, reentrancy into other parts of the `FlapTaxTokenV3` contract not protected by `notLiquidating`, or denial of service if they revert.

**Recommendation:** Thoroughly audit the `_processTax` function and all external contracts it interacts with. Implement `try/catch` blocks for external calls within `_processTax` to handle failures gracefully without reverting the entire transaction. Consider adding a reentrancy guard to `_processTax` itself if it performs sensitive state changes before/after external calls.


### `M-02` — Denial of Service via `_liquidateTax` Revert  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function is invoked at the beginning of every `_transfer` operation. If `_liquidateTax` (specifically the truncated `_processTax` call within it, or any other logic) encounters an error and reverts, it will cause the entire `_transfer` transaction to revert. This could lead to a denial of service for all token transfers, effectively freezing the token.

**Recommendation:** Ensure `_processTax` is highly resilient to failures. Implement `try/catch` blocks for external calls within `_processTax` to prevent them from propagating reverts to `_transfer`. If `_processTax` is critical, consider a mechanism for the owner to pause/unpause tax processing or to recover from failed liquidations without blocking all transfers.


### `M-03` — Immutability of Critical External Addresses  *(Severity: Medium · Status: Unresolved)*

Several critical external contract addresses, including `v2Router`, `quoteToken`, `mainPool`, `taxProcessor`, `dividendContract`, and the `pools` mapping, are set only during the `initialize` function and cannot be modified afterward. This immutability means that if any of these addresses become compromised, deprecated, or if the protocol needs to adapt to changes (e.g., router upgrades, new tax processors), the contract would require a costly and disruptive upgrade or redeployment.

**Recommendation:** Consider adding `onlyOwner` functions to allow updating these critical addresses. Implement appropriate security measures for these update functions, such as timelocks, multi-signature wallet requirements, or a governance mechanism, to prevent malicious or accidental changes.


### `I-01` — Redundant Liquidation Threshold Variables  *(Severity: Informational · Status: Unresolved)*

The contract defines `MIN_LIQ_THRESHOLD` (immutable), `START_LIQ_THRESHOLD` (immutable), `initialLiquidationThreshold` (public state variable), and `poolState.liquidationThreshold` (part of a packed struct). Both `initialLiquidationThreshold` and `poolState.liquidationThreshold` are initialized to `START_LIQ_THRESHOLD` and are never modified thereafter. This creates redundancy and potential for confusion regarding which variable represents the active liquidation threshold, especially given `MIN_LIQ_THRESHOLD` is also present but not actively used in the provided logic.

**Recommendation:** Clarify the purpose and usage of each liquidation threshold variable in the contract's documentation. Consider removing redundant variables if they serve no distinct purpose to improve code clarity and reduce storage footprint.


### `I-02` — Complex `_transfer` State Machine  *(Severity: Informational · Status: Unresolved)*

The `_transfer` function implements a complex state machine with multiple `if/else if` branches based on the `PoolState` enum. While this design allows for flexible tax and transfer logic, the intricate conditional paths can increase the cognitive load for understanding the contract's behavior and raise the potential for subtle logic errors or edge cases if not thoroughly tested.

**Recommendation:** Ensure comprehensive unit and integration tests cover all possible `PoolState` transitions and transfer scenarios. Consider refactoring complex conditional logic into smaller, well-named helper functions to improve readability and maintainability.


### `I-03` — Hardcoded `maxSupply`  *(Severity: Informational · Status: Unresolved)*

The `maxSupply` of the token is defined as a `constant` with a value of `1e9 ether`. This design choice fixes the total supply of the token permanently. While this might be the intended economic model, it means the total supply cannot be adjusted (e.g., for burning or minting beyond initial supply) without a contract upgrade.

**Recommendation:** Document this design choice clearly, confirming that a fixed supply is the intended and desired behavior for the token's economic model.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0c2...7777`](https://bscscan.com/address/0xb0c2ab5af4028461ace3f6e1c33a4ee1404e7777) |
| **Network** | BNB Chain |
| **Price** | $0.0155 |
| **24h Volume** | $1.10M |
| **Liquidity** | $522.2K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 25d |
| **Top-10 Holders** | 24.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 840 buys / 929 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xdabbd019c0174bdae6354f32b158d42e4a0e7489)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cets-on-gold-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
