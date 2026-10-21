---
token: ELON
ticker: ELON
network: base
risk_score: 46
status: medium
date: 2026-09-13
---

# ELON (ELON) — Smart Contract Security Analysis | Base

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elon-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an ERC20 token with voting capabilities and a vesting mechanism. It utilizes Solady libraries for efficiency and security. The contract includes features such as a configurable balance limit and a pool locking mechanism. While the overall architecture appears sound and standard security practices like `Ownable` and `Initializable` are employed, the audit identified several areas for improvement, particularly concerning operational flexibility, upgrade safety, and the economic implications of initial token distribution. A significant portion of the core vesting logic was truncated, limiting a full assessment of its security.

> **Final Recommendation:** It is recommended to implement a mechanism to update the `controller` address post-initialization, possibly through an owner-controlled function, to enhance operational flexibility and mitigate single points of failure. For future upgrades, carefully consider the storage layout, especially when adding new state variables after dynamic arrays like `vestingSchedules`, to prevent storage collisions. Finally, ensure the full implementation of the vesting logic (`_available`, `_releaseFor`, `_releaseAllFor`) is thoroughly reviewed to confirm correct calculation, cliff/duration enforcement, and prevention of double-spending, as this is critical for the economic integrity of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices, leveraging battle-tested Solady libraries for ERC20, Ownable, and Initializable functionalities (7.2 Code Security). Error handling is robust with… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model includes a vesting mechanism with configurable schedules, which is a standard approach for token distribution. The `owner` role is appropriately restricted for critical… |
| **Upgrades** | 7/10 | Low | The contract is designed for upgradeability, correctly using `Initializable` and `_disableInitializers()` (7.7 Upgrades). The storage layout for fixed variables appears straightforward. However, the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Immutable Controller Address for Balance Limit Feature  *(Severity: Medium · Status: Unresolved)*

The `controller` address, responsible for disabling the `isBalanceLimitActive` feature via `disableBalanceLimit()`, is set only during the `initialize` function. If the `balanceLimitEnd_` and `maxBalanceLimit_` parameters are both zero during initialization, the `controller` address remains `address(0)`. Even if the balance limit is active, the `controller` cannot be changed after initialization. This creates an operational inflexibility and a single point of failure: if the initial `controller` address is compromised or becomes inactive, the balance limit cannot be disabled without a contract upgrade.

**Recommendation:** Implement an `onlyOwner` function to allow the `controller` address to be updated after initialization. This would provide greater operational flexibility and resilience against a compromised or inactive controller.


### `M-02` — Upgradeability Risk with Dynamic Public Array  *(Severity: Medium · Status: Unresolved)*

The `vestingSchedules` array is declared as `public` and is a dynamic array. In upgradeable contracts, adding new state variables *after* a dynamic array in a future implementation can lead to storage slot collisions if the array grows significantly. While `vestingSchedules` is currently the last non-mapping state variable, this pattern introduces a risk if not carefully managed in future upgrades.

**Recommendation:** When planning future upgrades, ensure that new state variables are not introduced in a way that would cause storage slot collisions with the `vestingSchedules` array. Consider using explicit storage gap patterns or placing dynamic arrays at the end of the storage layout to mitigate this risk.


### `L-01` — High Initial Pre-Mint Allocation Parameters  *(Severity: Low · Status: Unresolved)*

The constants `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` are both set to `0.8 ether`, effectively allowing up to 80% of the `initialSupply` to be pre-minted and allocated through vesting schedules. While this is a design choice, such a high pre-allocation percentage can lead to significant token concentration in early beneficiaries, potentially impacting initial liquidity, decentralization, and market dynamics.

**Recommendation:** Review the tokenomics and distribution strategy to ensure that such a high pre-allocation aligns with the project's goals for decentralization and market health. Consider if a lower initial pre-mint percentage or a more diversified distribution strategy would be beneficial.


### `I-01` — Incomplete Vesting Logic Provided for Audit  *(Severity: Informational · Status: Unresolved)*

The core logic for `_available`, `_releaseFor`, and `_releaseAllFor` functions, which are central to the vesting mechanism, is truncated in the provided source code. A comprehensive security assessment of the vesting functionality, including correct calculation of vested amounts, cliff/duration enforcement, and prevention of double-spending, cannot be performed without access to these critical internal implementations.

**Recommendation:** Provide the complete source code for all internal vesting-related functions (`_available`, `_releaseFor`, `_releaseAllFor`) to enable a full and accurate security assessment of the vesting mechanism.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa3d3...aba3`](https://basescan.org/address/0xa3d353743164972b37c8e5358fb1e76f0be8aba3) |
| **Network** | Base |
| **Price** | $0.00000252 |
| **24h Volume** | $204.1K |
| **Liquidity** | $106.1K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | 51.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 685 buys / 1667 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x955590753d5c19ab840d2901900625a8dcee8aa54f4184c84a79e015673b10ae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elon-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
