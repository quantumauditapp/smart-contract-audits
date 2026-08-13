---
token: usocks
ticker: USOCKS
network: ethereum
risk_score: 86
status: critical
date: 2026-08-13
---

# usocks (USOCKS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 86/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usocks-eth)

---

## Audit Summary

The USocks contract implements an ERC20 token with integrated NFT reward mechanisms and fee distribution. While utilizing OpenZeppelin libraries and reentrancy guards for some functions, the audit identified critical economic design flaws related to buyback redirection and token burning, alongside a high-severity reentrancy vulnerability in the ETH deposit and distribution logic. Several medium and low-severity issues pertain to the immutability of critical dependencies and the complexity of the reward system. Addressing these core issues is paramount for the security and integrity of the protocol.

> **Final Recommendation:** It is critical to immediately address the identified economic vulnerabilities related to redirected buybacks and unexpected token burning. These design flaws pose an existential threat to user funds and protocol integrity. A thorough review and redesign of the `_tryRedirectedBuybackAfterTransfer` and `_burnExcess` mechanisms are essential. Furthermore, the reentrancy vulnerability in the ETH deposit and distribution logic must be patched by applying reentrancy guards to prevent potential fund drains. Consider implementing a more flexible dependency management system or an upgradeable architecture for future resilience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages OpenZeppelin's ERC20 and ReentrancyGuard, providing a solid foundation for token operations and preventing reentrancy in several key functions (7.2 Code Security). However, a… |
| **Governance / Economics** | 1/10 | High | The economic design contains critical flaws that could lead to significant fund loss or manipulation (7.4 Economic). Specifically, the `_tryRedirectedBuybackAfterTransfer` function allows any user to… |
| **Upgrades** | 4/10 | Medium | The USocks contract is not designed to be upgradeable, as it does not implement a proxy pattern (7.7 Upgrades). This means its logic cannot be modified post-deployment. While this simplifies the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Critical: Redirected Buyback Vulnerability  *(Severity: Critical · Status: Unresolved)*

The `_tryRedirectedBuybackAfterTransfer` function is called after every `transfer` and `transferFrom`. If `buybackExecutor.buy` fails in `_payBuyback`, the `buybackRewardRemainder` is added to `redirectedBuybackTotal`. This accumulated `redirectedBuybackTotal` is then transferred from the `USocks` contract's balance to the recipient of *any subsequent token transfer*. This means a user making a small transfer to themselves or a controlled address can claim a potentially large accumulated `redirectedBuybackTotal`, effectively draining funds intended for buybacks. This creates a severe incentive for users to monitor `redirectedBuybackTotal` and exploit it.

**Recommendation:** Rework the buyback redirection logic. Instead of redirecting to the next transfer recipient, consider a dedicated claim function for accumulated buyback funds, or ensure `redirectedBuybackTotal` is handled in a way that prevents arbitrary claiming by any transfer recipient. The `redirectedBuybackTotal` should be cleared or distributed in a controlled, auditable manner.


### `H-01` — High: Unexpected Token Burning on Sell  *(Severity: High · Status: Unresolved)*

The `recordSell` function, called by the `market`, invokes `_burnExcess(seller)`. This internal function burns `balanceOf(seller) - amount`. This means that when a user sells a specific `amount` of tokens, any *additional* tokens they hold in their balance beyond that `amount` are also burned. This is a highly unusual and potentially destructive behavior, as users might not expect their entire balance (minus the sold amount) to be destroyed.

**Recommendation:** Clarify this behavior in documentation and user interfaces, or, preferably, remove the `_burnExcess` mechanism entirely. If the intent is to enforce a specific balance post-sell, this should be explicitly communicated and potentially opt-in, rather than an automatic burn.


### `H-02` — High: Reentrancy in ETH Deposit/Distribution  *(Severity: High · Status: Unresolved)*

The `receive()` and `depositFees()` functions are `payable` and call `_depositFees`. `_depositFees` distributes received ETH to `holderDistributionRemainder`, `pendingOfficial`, and `pendingBuyback`. It then makes external calls to `_payHolderDistribution`, `_payOfficial`, and `_payBuyback`. Critically, `_payBuyback` calls `buybackExecutor.buy{value: amount}(address(this), address(this))`. If `buybackExecutor`, `settlement`, or `official` are malicious or compromised contracts, they could re-enter `USocks` via `receive()` or `depositFees()` during these external calls. This could lead to repeated distribution of the same ETH or other state manipulation before the initial `_depositFees` call…

**Recommendation:** Apply the `nonReentrant` modifier to `depositFees()` and ensure `receive()` is also protected (e.g., by making `receive()` call a `nonReentrant` internal function). Thoroughly review all external calls within the ETH distribution logic to ensure no reentrancy vectors exist.


### `M-01` — Medium: Immutability of Critical Dependencies  *(Severity: Medium · Status: Unresolved)*

The `market`, `settlement`, `official`, `buybackExecutor`, and `renderer` addresses are set as `immutable` in the constructor. While this provides certainty, it also means that if any of these external contracts become compromised, deprecated, or require an upgrade, there is no mechanism to update them. This could lead to a permanent failure of core protocol functionalities (e.g., market operations, buybacks, NFT rendering) without the ability to recover or adapt.

**Recommendation:** Consider implementing an upgradeable proxy pattern for the `USocks` contract itself, or at least for the critical external dependencies, allowing a trusted governance or multisig to update these addresses if necessary. This introduces centralization but provides resilience against external contract failures.


### `M-02` — Medium: Complexity of Reward Distribution Logic  *(Severity: Medium · Status: Unresolved)*

The reward distribution system involving `accRewardPerWeight`, `totalRewardWeight`, `nftRewardDebt`, `nftRewardRemainder`, `nftClaimable`, and various internal functions (`_settleNft`, `_updateAccRewardPerWeight`, `_claimNft`) is highly complex. Such intricate logic increases the surface area for subtle bugs, rounding errors, or unintended economic incentives, which can be difficult to identify and verify.

**Recommendation:** Conduct a thorough mathematical review and formal verification of the reward distribution logic to ensure its correctness and fairness under all possible scenarios. Provide comprehensive documentation and unit tests for each component of the reward system.


### `L-01` — Low: Precision Loss in Reward Calculations  *(Severity: Low · Status: Unresolved)*

The reward calculation uses `ACCURACY = 1e36` for scaling and division. While large, division operations like `(delta + nftRewardRemainder[tokenId]) / ACCURACY` inherently involve precision loss if the numerator is not perfectly divisible. Although `nftRewardRemainder` attempts to capture remainders, repeated calculations over time could lead to minor discrepancies or accumulation of unclaimable dust amounts, potentially impacting the long-term fairness or exactness of rewards.

**Recommendation:** Document the expected precision behavior and potential for dust accumulation. Consider using a fixed-point math library if extreme precision is required, or explicitly state that minor precision losses are an acceptable trade-off for gas efficiency.


### `I-01` — Informational: Lack of Emergency Pause/Withdrawal  *(Severity: Informational · Status: Unresolved)*

The contract lacks a mechanism to pause critical operations in an emergency (e.g., a severe vulnerability discovered in a dependency or the `USocks` contract itself). Additionally, there are no explicit functions for an authorized entity to withdraw accidentally sent or stuck tokens/ETH, although the `_depositFees` function immediately distributes ETH.

**Recommendation:** Implement a `Pausable` mechanism (e.g., from OpenZeppelin) for critical functions to allow for emergency halts. Consider adding an `emergencyWithdraw` function, callable by a trusted multisig, to recover tokens or ETH accidentally sent to the contract, although this should be carefully designed to not interfere with intended protocol operations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2e43...f7d2`](https://etherscan.io/address/0x2e43e18a19ae896c6f8657ca6285b9672f67f7d2) |
| **Network** | Ethereum |
| **Price** | $0.00000324 |
| **24h Volume** | $690.2K |
| **Liquidity** | $146.3K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 20h |
| **Top-10 Holders** | 40.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2143 buys / 2304 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x18adf6fa633dfadb0aaa108b5773f9a878b293ee180c6b7da8db9a3f88c3bfcf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usocks-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
