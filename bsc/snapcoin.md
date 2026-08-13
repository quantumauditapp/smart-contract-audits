---
token: SnapCoin
ticker: SNAPCOIN
network: bsc
risk_score: 90
status: critical
date: 2026-08-13
---

# SnapCoin (SNAPCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/snapcoin-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and a state machine for managing pool interactions. A critical portion of the `_liquidateTax` function was truncated in the provided source, preventing a full security assessment. Key findings include significant centralization of token supply to the deployer, potential reentrancy/MEV risks in the tax liquidation process, and immutability of critical external dependencies. The contract utilizes OpenZeppelin's upgradeable patterns correctly for its proxy implementation.

> **Final Recommendation:** It is imperative to provide the complete source code for the `_liquidateTax` function to enable a thorough security review, especially concerning reentrancy and external call interactions. Address the high centralization of token supply by implementing a more distributed initial token allocation or a robust governance mechanism. Consider adding owner-controlled functions to update critical external dependencies and adjust tax parameters to enhance operational flexibility and responsiveness to unforeseen circumstances. Review the `_liquidateTax` trigger mechanism for gas efficiency and potential MEV vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages OpenZeppelin's battle-tested upgradeable ERC20, Ownable, and Permit implementations, contributing to a solid foundation (7.1 Architecture). However, a critical portion of the… |
| **Governance / Economics** | 1/10 | High | The contract establishes clear owner roles for initiating and finalizing migration states, which is a positive aspect of its operational control (7.5 Governance). However, a significant economic risk… |
| **Upgrades** | 3/10 | High | The contract correctly implements the UUPS proxy pattern by inheriting from `Initializable` and calling `_disableInitializers()` in the constructor, ensuring proper upgradeability (7.7 Upgrades). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incomplete `_liquidateTax` Function Prevents Full Audit  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated, specifically at the point where `poolState = currentPoolState` is assigned after `_processTax(taxAmount)`. This prevents a complete analysis of the function's logic, including its interaction with external contracts, potential reentrancy vectors, and overall security implications. Without the full implementation, critical vulnerabilities could remain undetected.

**Recommendation:** Provide the complete and untruncated source code for the `_liquidateTax` function to allow for a comprehensive security assessment. This is essential for verifying the integrity and safety of the contract's core tax processing logic.


### `H-01` — Centralization of Token Supply to Deployer  *(Severity: High · Status: Unresolved)*

During the `initialize` function, the entire `maxSupply` (1e9 ether) of tokens is minted directly to `msg.sender` (the deployer). This grants the deployer 100% of the token supply, leading to extreme centralization. This single entity has the power to significantly influence market prices, control any future governance mechanisms, or dump tokens, posing a severe economic risk to the project and its users (7.4 Economic).

**Recommendation:** Implement a more decentralized initial token distribution strategy. This could involve vesting schedules, multi-signature wallets for large holdings, or a community-controlled treasury. If this is an intended design for a specific phase, ensure users are fully aware of this centralization risk.


### `H-02` — Potential Reentrancy and MEV Risk in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function performs state changes (`currentPoolState.notLiquidating = false` before `_processTax` and `true` after) and likely makes external calls via `_processTax(taxAmount)` (which would interact with `taxProcessor` and `dividendContract`). This pattern is highly susceptible to reentrancy if `_processTax` calls an untrusted contract that can re-enter `_transfer` and subsequently `_liquidateTax` before `notLiquidating` is reset. Additionally, the function's reliance on `block.timestamp` and `taxAmount` to trigger state changes or tax processing creates opportunities for MEV (Miner Extractable Value) where an attacker could front-run transactions to manipulate the timing…

**Recommendation:** Implement a 'Checks-Effects-Interactions' pattern to mitigate reentrancy. Ensure all state changes are completed before any external calls are made. If `_processTax` involves external calls, consider using reentrancy guards. Thoroughly analyze the full `_processTax` implementation for reentrancy vectors. For MEV, consider adding a delay or a commit-reveal scheme for sensitive state transitions if applicable, or ensure that the economic incentives for front-running are minimized.


### `M-01` — Immutability of Critical External Dependencies  *(Severity: Medium · Status: Unresolved)*

The `taxProcessor` and `dividendContract` addresses are set during the `initialize` function and are immutable thereafter. This means that if these external contracts are compromised, become buggy, or require upgrades, the `FlapTaxTokenV3` contract cannot adapt by updating these addresses. This introduces a single point of failure and limits operational flexibility (7.6 External, 7.8 Operations).

**Recommendation:** Implement owner-controlled functions to allow for updating the `taxProcessor` and `dividendContract` addresses. This should be protected by `onlyOwner` and potentially a timelock to provide a window for users to react to changes. Ensure robust validation for new addresses (e.g., checking for non-zero address).


### `M-02` — Lack of Direct Owner Control over Tax Parameters  *(Severity: Medium · Status: Unresolved)*

While the owner can initiate state transitions (`startMigration`, `finalizeMigration`) that indirectly affect tax parameters, there are no direct owner-controlled functions to adjust `buyTaxRate`, `sellTaxRate`, `taxExpirationTime`, or `antiFarmerDuration` after initialization. This limits the project's ability to respond to changing market conditions, regulatory requirements, or unforeseen economic circumstances by dynamically adjusting the tax structure (7.5 Governance).

**Recommendation:** Consider adding owner-controlled functions to allow for the adjustment of key tax parameters such as `buyTaxRate`, `sellTaxRate`, `taxExpirationTime`, and `antiFarmerDuration`. These functions should be protected by `onlyOwner` and potentially a timelock to ensure transparency and provide a grace period for users.


### `L-01` — Inefficient `_liquidateTax` Trigger Mechanism  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function is called on every `_transfer` where the `to` address is the `mainPool`. While this ensures tax liquidation is regularly checked, it could lead to unnecessary gas consumption if transfers to the `mainPool` are frequent but the conditions for actual liquidation (e.g., `taxAmount >= liquidationThreshold` or `block.timestamp > taxExpirationTime`) are rarely met. This constant checking adds overhead without always performing a useful action (7.2 Code Security).

**Recommendation:** Consider optimizing the trigger for `_liquidateTax`. This could involve: 1) Implementing a minimum time interval between liquidation checks. 2) Allowing an external actor (e.g., keeper bot) to trigger liquidation when conditions are met, potentially incentivized by a small fee. 3) Only checking liquidation conditions if the accumulated tax balance exceeds a certain threshold.


### `I-01` — Upgradeability Considerations for `PackedPoolState` Struct  *(Severity: Informational · Status: Unresolved)*

The `PackedPoolState` struct is efficiently packed into a single storage slot (8+16+16+8+96+64+48 = 256 bits). While this is good for gas efficiency, adding new fields to this struct in a future upgrade requires extreme caution. If new fields are added without careful consideration of storage slot packing, it could lead to storage collisions with existing data, resulting in data corruption or unexpected contract behavior (7.7 Upgrades).

**Recommendation:** When planning future upgrades, if modifications to the `PackedPoolState` struct are necessary, ensure that new fields are appended carefully to avoid overwriting existing data. Consult OpenZeppelin's upgrade guidelines on storage layout and consider using tools like `hardhat-upgrades` or `foundry-upgrades` to detect storage layout incompatibilities during development.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x354e...7777`](https://bscscan.com/address/0x354e1a55ac2c0c11d77f83c67f186ca2f2457777) |
| **Network** | BNB Chain |
| **Price** | $0.00002716 |
| **24h Volume** | $104.6K |
| **Liquidity** | $17.2K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1277 buys / 924 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x27d2d737fce9f46b3512fa6aa1149e82c1498df8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/snapcoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
