---
token: CONDO
ticker: CONDO
network: ethereum
risk_score: 62
status: medium
date: 2026-09-26
---

# CONDO (CONDO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/condo-eth)

---

## Audit Summary

The LaunchToken contract implements an ERC-20 token with unique features including buy/hold caps, a launch guard period, and a holder reward distribution mechanism. The contract leverages OpenZeppelin libraries for standard ERC-20 functionality. Key findings include a critical integer overflow vulnerability in reward calculations, a high centralization risk associated with the `factory` role, and potential for rewards to become stuck under specific conditions. Several minor issues related to error message clarity, event logging, and unused variables were also identified. The contract operates as an implementation behind a proxy, making the `initialize` function and `factory` role critical for secure deployment and future upgrades.

> **Final Recommendation:** Address the critical integer overflow vulnerability in reward calculations by implementing robust overflow checks or using a safe math library for these specific operations. Mitigate the centralization risk by considering a multi-signature wallet for the `factory` role or implementing a time-locked governance mechanism for sensitive administrative actions, especially those affecting reward distribution. Improve transparency by emitting events for all critical state changes, particularly when addresses are excluded from rewards. Review and clarify error messages for better user experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract is built upon OpenZeppelin's ERC20, providing a solid foundation for token standards. The custom logic for buy/hold caps and the reward system is well-structured. However, a critical… |
| **Governance / Economics** | 1/10 | High | The tokenomics are defined by immutable constants, providing predictability for supply and initial trading limits. The reward mechanism, while designed to incentivize holding, is vulnerable to… |
| **Upgrades** | 5/10 | Medium | The contract is intended to be deployed as an upgradeable proxy implementation, utilizing an `initialize` function for one-time setup. This design allows for future logic upgrades, enhancing… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `C-01` — Integer Overflow in Reward Calculation  *(Severity: Critical · Status: Unresolved)*

The calculations `(total * ACC_PRECISION) / eligibleSupply` in `notifyReward` and `(balanceOf(account) * accRewardPerToken) / ACC_PRECISION` in `pendingReward`, `_settle`, and `_rebase` are susceptible to integer overflow. Specifically, `total * ACC_PRECISION` and `balanceOf(account) * accRewardPerToken` can exceed `type(uint256).max` if `total` or `balanceOf(account)` are sufficiently large, especially when `eligibleSupply` is small, causing `accRewardPerToken` to grow rapidly. An overflow would lead to incorrect reward calculations, potentially resulting in a denial of service for reward distribution or an attacker being able to manipulate reward values.

**Recommendation:** Implement explicit overflow checks for the multiplication operations `total * ACC_PRECISION` and `balanceOf(account) * accRewardPerToken`. Consider using OpenZeppelin's `SafeMath` library or similar custom checks to prevent these overflows. Ensure that intermediate products do not exceed `type(uint256).max` before division.


### `H-01` — Centralization Risk with `factory` Role  *(Severity: High · Status: Unresolved)*

The `factory` address has extensive control over critical contract functions, including setting the `market`, enabling holder fees, and being a valid `rewardSource`. More critically, the `factory` can manipulate the `eligibleSupply` by arbitrarily excluding and including addresses from reward participation via `_setRewardExcluded`. This allows the `factory` to potentially drain accumulated `carriedReward` or disproportionately accumulate rewards by excluding all other holders and then re-including themselves. This centralizes significant power, creating a single point of failure and a high trust requirement in the `factory` operator.

**Recommendation:** Consider implementing a multi-signature wallet for the `factory` role to distribute control. For highly sensitive actions like `_setRewardExcluded`, implement a time-lock mechanism or a community governance vote to provide transparency and allow users to react to changes. Clearly document the powers of the `factory` role.


### `M-01` — Potential for Stuck Rewards if `eligibleSupply` is Zero  *(Severity: Medium · Status: Unresolved)*

If `eligibleSupply` remains zero for an extended period, all `notifyReward` calls will only increase `carriedReward`. While `carriedReward` is eventually added to `total` when `eligibleSupply` becomes non-zero, there's no explicit mechanism to force `eligibleSupply` to be non-zero if all token holders are excluded or if the token is held entirely by excluded addresses. This could lead to rewards being indefinitely stuck in `carriedReward` if no eligible supply ever emerges.

**Recommendation:** Implement a mechanism to allow the `factory` or a governance entity to re-enable `eligibleSupply` if it becomes zero, perhaps by forcing the inclusion of a specific address or by allowing a portion of `carriedReward` to be recovered if it remains stuck for a prolonged period. Alternatively, consider a fallback mechanism for `carriedReward` distribution if `eligibleSupply` remains zero.


### `M-02` — `MarketAlreadySet` Error Misuse in `enableHolderFees`  *(Severity: Medium · Status: Unresolved)*

The `enableHolderFees` function uses `revert MarketAlreadySet()` when `holderFeesEnabled` is true. This is misleading as the error message suggests the market is already set, not that holder fees are already enabled. While functionally correct, it impacts user experience and clarity, potentially causing confusion for users or integrators.

**Recommendation:** Create a specific error message for when holder fees are already enabled, such as `revert HolderFeesAlreadyEnabled()`. This improves clarity and user experience.


### `L-01` — Lack of Event for `_setRewardExcluded`  *(Severity: Low · Status: Unresolved)*

The `_setRewardExcluded` internal function, which significantly impacts reward distribution by changing `eligibleSupply` and `rewardExcluded` status, does not emit an event. This makes it difficult to track changes to reward exclusion status and `eligibleSupply` on-chain, hindering transparency and monitoring by external parties.

**Recommendation:** Emit an event (e.g., `RewardExclusionChanged(address indexed account, bool excluded, uint256 newEligibleSupply)`) whenever `_setRewardExcluded` is called. This enhances transparency and allows for better off-chain monitoring of reward eligibility.


### `L-02` — `creator` Role Specificity and Potential for Misconfiguration  *(Severity: Low · Status: Unresolved)*

The `creator` address has special handling during the launch block (`block.number == _launchBlock && to == creator`), allowing it to bypass initial buy caps. While intended for initial distribution, if the `creator` address is misconfigured during `initialize` or subsequently compromised, it could be used to bypass these critical launch restrictions. The `creator` address is immutable after initialization.

**Recommendation:** Ensure rigorous verification of the `creator` address during deployment and initialization. Consider adding a mechanism (e.g., a time-lock or a multi-sig confirmation) for setting such critical, immutable addresses if the deployment process is complex or involves multiple parties.


### `I-01` — Unused `metadataURI` State Variable  *(Severity: Informational · Status: Unresolved)*

The `metadataURI` state variable is set during the `initialize` function but is not used anywhere else within the contract's on-chain logic. While it might be intended for off-chain use (e.g., for token metadata), its presence in storage without on-chain utility could be considered dead storage or a potential for confusion regarding its purpose within the contract.

**Recommendation:** If `metadataURI` is purely for off-chain consumption and has no on-chain effect, consider if it's strictly necessary to store it in contract state. If it is, add a comment explaining its purpose. If it's intended for on-chain use, ensure it's integrated into relevant functions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfe99...9b26`](https://etherscan.io/address/0xfe99b2fe66c7725ce30730010a864740e7c39b26) |
| **Network** | Ethereum |
| **Price** | $0.001155 |
| **24h Volume** | $1.14M |
| **Liquidity** | $181.9K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 4d |
| **Top-10 Holders** | 23.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1755 buys / 1275 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x0e471121607979c4b52d54e140527630c1d026be9b4b3087bba7f1c1c667cd16)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/condo-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-26*
