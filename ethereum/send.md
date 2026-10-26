---
token: send
ticker: SEND
network: ethereum
risk_score: 21
status: low
date: 2026-09-13
---

# send (SEND) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/send-eth)

---

## Audit Summary

The LaunchToken contract is an ERC20 token implementation designed for a specific launch phase with trading restrictions and a holder reward mechanism. The contract utilizes OpenZeppelin libraries for standard ERC20 functionality and includes custom logic for reward distribution and initial market caps. Key strengths include a robust proxy initialization pattern and reentrancy-safe reward claiming. However, significant centralized control by the 'factory' address introduces high governance and economic risks, including potential for reward manipulation. Several medium and informational findings were identified, primarily related to economic incentives and minor code quality.

> **Final Recommendation:** Address the high-severity centralized control issue by implementing a multi-signature wallet or time-locks for the `factory` address's critical functions. Review and potentially restrict the `factory`'s ability to call `notifyReward` without actual reward contributions to prevent economic manipulation. Consider safeguards against `eligibleSupply` manipulation to protect reward distribution integrity. Implement the recommended minor code quality improvements for enhanced clarity and robustness.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's ERC20 and SafeERC20 for robust token operations, ensuring standard compliance and safe external interactions. The reward distribution mechanism, including… |
| **Governance / Economics** | 2/10 | High | The `factory` address holds significant centralized control, including critical setup functions like `setMarket` and `enableHolderFees`, and the ability to bypass reward source checks for… |
| **Upgrades** | 6/10 | Medium | The contract is designed as an upgradeable implementation, utilizing a standard `initialize` function with a `factory != address(0)` guard to prevent re-initialization. The constructor sets `factory`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 67.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `M-01` — Potential for Reward Manipulation by Factory  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `factory` address can call `notifyReward` without requiring a corresponding transfer of `rewardToken` or native ETH to the contract. This allows the `factory` to artificially inflate `accRewardPerToken`, potentially diluting legitimate rewards for other holders or creating a misleading impression of rewards being distributed without actual contributions (7.4 Economic, 7.3 Access Control).

**Recommendation:** Restrict `notifyReward` to only the `rewardSource` address, or modify the `notifyReward` function to explicitly require a corresponding transfer of actual rewards to the contract when called by the `factory`.


### `M-02` — `eligibleSupply` Manipulation Risk  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). If a malicious actor (e.g., `factory` or `rewardSource`) can significantly reduce `eligibleSupply` (e.g., by excluding most holders), a small `amount` in `notifyReward` could cause a disproportionately large increase in `accRewardPerToken`. This could be exploited to claim a large share of rewards with minimal actual contribution, leading to unfair reward distribution (7.4 Economic).

**Recommendation:** Implement safeguards or monitoring for drastic changes in `eligibleSupply` or `accRewardPerToken` relative to actual reward contributions. Consider a minimum `eligibleSupply` threshold for `notifyReward` to prevent extreme dilution, or a mechanism to cap the `accRewardPerToken` increase per `notifyReward` call.


### `M-03` — Centralized Control by Factory Address  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `factory` address holds significant power, including the ability to set the market, enable holder fees, and bypass reward source checks for `notifyReward`. A compromise of this address could lead to manipulation of the token's economic parameters and reward system, potentially causing financial loss or unfair distribution. This represents a single point of failure for critical operations (7.3 Access Control, 7.4 Economic).

**Recommendation:** Consider implementing a multi-signature wallet for the `factory` address or introducing time-locks for critical operations (e.g., `setMarket`, `enableHolderFees`, `notifyReward` calls by `factory`) to mitigate single-point-of-failure risks and provide a window for community reaction.


### `L-01` — Theoretical Integer Overflow in Reward Calculation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While unlikely given typical values, the intermediate product `balanceOf(account) * accRewardPerToken` in `_settle` and `_rebase` could theoretically overflow if `accRewardPerToken` grows to an extremely large value (e.g., `type(uint256).max / TOTAL_SUPPLY`). Although Solidity 0.8+ checks for this, it would lead to a transaction revert, potentially blocking reward claims for affected users (7.2 Code Security, 7.4 Economic).

**Recommendation:** Monitor `accRewardPerToken` growth in production. While the risk is low, consider adding a maximum cap to `accRewardPerToken` or implementing a mechanism to reset it if it approaches dangerous levels, though this would require careful economic modeling.


### `I-01` — `MarketAlreadySet` Error Misuse  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `enableHolderFees` function uses the `MarketAlreadySet` error when `holderFeesEnabled` is already true. This is a minor inconsistency in error messaging, as the error name does not accurately reflect the condition (7.2 Code Security).

**Recommendation:** Rename the error to `HolderFeesAlreadyEnabled` or create a new specific error for this condition to improve clarity and maintain consistent error semantics.


### `I-02` — Unused `metadataURI` Variable  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `metadataURI` state variable is set during `initialize` but is not used anywhere else within the contract logic. If its purpose is solely for off-chain metadata, its presence in the contract might be unnecessary (7.2 Code Security).

**Recommendation:** If `metadataURI` is not intended for on-chain use, consider removing it to reduce contract size and complexity. If it serves an off-chain purpose, ensure this is clearly documented.


### `I-03` — `receive()` function without specific logic  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `receive()` function is present and `payable` but contains no specific logic. While it allows the contract to receive native ETH, its explicit purpose might be unclear if not directly tied to a specific feature beyond `notifyReward` being payable (7.2 Code Security).

**Recommendation:** If the contract is not intended to directly receive native ETH for purposes other than `notifyReward`, consider removing the `receive()` function or adding a comment explaining its intended use to improve code clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x47ac...5999`](https://etherscan.io/address/0x47accd13264d8f954105256faac8376ce6a55999) |
| **Network** | Ethereum |
| **Price** | $0.001993 |
| **24h Volume** | $2.36M |
| **Liquidity** | $287.4K |
| **Volume / Liquidity** | 8.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 23.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3305 buys / 2311 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xfd1c4559ad314e035e2440d88574ce44ff10ab05cfc90e4c8591b2fae7c73a6f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/send-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
