---
token: iPod
ticker: IPOD
network: base
risk_score: 35
status: medium
date: 2026-09-12
---

# iPod (IPOD) — Smart Contract Security Analysis | Base

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ipod-base)

---

## Audit Summary

The DopplerERC20V1 contract is an upgradeable ERC20 token with vesting functionalities, built using Solady libraries. It includes features for managing vesting schedules, allocating tokens to beneficiaries, and a temporary balance limit mechanism. The contract exhibits good adherence to ERC20 standards and utilizes custom error handling. Key areas of concern include the high degree of centralized control by the owner and controller roles, potential gas limitations for beneficiaries with numerous vesting schedules, and the hardcoded nature of critical economic parameters. The balance limit mechanism, while present, has a significantly narrowed scope due to numerous explicit exclusions.

> **Final Recommendation:** It is recommended to review the extent of centralized control and consider implementing multi-signature governance for critical functions to enhance security and decentralization. For functions that iterate over dynamic arrays, assess the practical limits and consider alternative patterns or pagination if gas costs become prohibitive. Finally, evaluate the hardcoded economic parameters and determine if making them configurable via a controlled mechanism would benefit the protocol's long-term adaptability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates a solid technical foundation, utilizing Solady libraries for robust ERC20 and Ownable implementations (7.2 Code Security). Custom error handling is well-implemented… |
| **Governance / Economics** | 5/10 | Medium | The contract design incorporates significant centralized control, with the `owner` able to lock/unlock the pool and update the token URI, and the `controller` able to disable the balance limit (7.3… |
| **Upgrades** | 7/10 | Low | The contract is designed for upgradeability using the `Initializable` pattern from Solady, with the constructor correctly disabling initializers (7.7 Upgrades). The `OZ_ProxyAdmin` managing the proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.6% |
| **Top-3 Unlocked** | ⚠️ 97.3% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Potential Gas Limit Exceeded for `_releaseAllFor` Iteration  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_releaseAllFor` function (implied by the external `release` and `releaseFor` functions, and the `getScheduleIdsOf` view function) iterates through all `scheduleIds` associated with a beneficiary via `_scheduleIdsOf[beneficiary]`. If a beneficiary accumulates a very large number of distinct vesting schedules, this loop could potentially consume excessive gas, causing the transaction to exceed the block gas limit and preventing the beneficiary from releasing all their vested tokens in a single transaction.

**Recommendation:** Consider implementing a pagination mechanism or a batch release function that allows beneficiaries to release tokens for a subset of their schedules at a time. Alternatively, if the number of schedules is expected to be small, document this limitation clearly. For existing contracts, monitor gas usage for beneficiaries with many schedules.


### `M-02` — Centralized Control by Owner and Controller Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` and `controller` roles possess significant power over the contract's critical functionalities. The `owner` can `lockPool`, `unlockPool`, and `updateTokenURI`. The `controller` can `disableBalanceLimit`. While the owner is noted to be an `OZ_ProxyAdmin` (likely a multisig), the contract's architecture still grants these single addresses extensive control, posing a centralization risk. A malicious or compromised owner/controller could significantly impact the protocol's integrity and user funds.

**Recommendation:** Implement a robust multi-signature governance mechanism for all critical administrative functions, including `lockPool`, `unlockPool`, `updateTokenURI`, and `disableBalanceLimit`. This would require multiple trusted parties to approve sensitive operations, significantly reducing the risk associated with a single point of failure or compromise.


### `L-01` — Hardcoded Vesting and Pre-Mint Parameters  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several critical economic parameters, such as `MAX_PRE_MINT_PER_ADDRESS_WAD`, `MAX_TOTAL_PRE_MINT_WAD`, and `MIN_VESTING_DURATION`, are hardcoded as constants within the contract. These values define fundamental aspects of the token's initial distribution and vesting mechanics. Hardcoding them removes the flexibility to adjust these parameters in response to evolving market conditions, regulatory changes, or protocol needs without requiring a full contract upgrade.

**Recommendation:** Evaluate whether these parameters should be made configurable by the owner or a governance mechanism. If flexibility is desired, consider storing these values in state variables that can be updated through a controlled function (e.g., `onlyOwner` or `onlyGovernance`). This would allow for dynamic adjustments without necessitating a contract upgrade.


### `I-01` — Limited Scope of Balance Limit Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxBalanceLimit` feature is designed to restrict token balances for certain addresses during a specified period. However, the contract explicitly excludes the `owner`, the initial `recipient`, all initial vesting `beneficiaries`, and the designated `pool` address from this limit. This design choice significantly narrows the applicability of the balance limit, meaning it only affects a subset of token holders and may not achieve a broad-based control over token distribution.

**Recommendation:** This is an intended design choice. Ensure that the implications of these exclusions are fully understood and align with the project's economic model and risk management strategy. Clearly communicate the limited scope of the balance limit to users and stakeholders.


### `I-02` — Potential for `LibTransient` Slot Collision (Low Probability)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `LibTransient` library uses a `keccak256` hash (`HAS_SCHEDULE_TRANSIENT_SLOT`) to define a storage slot for a boolean flag. While `keccak256` collisions are extremely rare, using a fixed hash for a storage slot in a general-purpose library could theoretically lead to a collision if another part of the contract or an inherited contract also uses `LibTransient` with the same slot, or if a future upgrade introduces a state variable at that specific storage slot. This is a very low probability risk.

**Recommendation:** For future upgrades or when integrating other libraries, perform a thorough storage slot analysis to ensure no unintended collisions occur. While the probability is minimal, awareness of this pattern is important for long-term contract maintenance and upgrade safety.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa6af...fee1`](https://basescan.org/address/0xa6af0cea8fbc93e1eccc00f1fdd9a0bba251fee1) |
| **Network** | Base |
| **Price** | $0.001634 |
| **24h Volume** | $356.2K |
| **Liquidity** | $458.9K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 15d |
| **Top-10 Holders** | 49.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 718 buys / 1249 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x851f65bcdf6485f15047d4dea1cf8cb60ad1a815bbed7d2e8373a32b954045e4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ipod-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
