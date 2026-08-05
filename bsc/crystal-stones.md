---
token: CRYSTAL STONES
ticker: CRYSTAL STONES
network: bsc
risk_score: 55
status: high
date: 2026-08-05
---

# CRYSTAL STONES (CRYSTAL STONES) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crystal-stones-bsc)

---

## Audit Summary

The provided source code for the FatToken contract is incomplete, specifically missing the critical `_transfer` function implementation. This omission severely limits the scope and depth of the security audit, as core token logic, fee application, and anti-bot mechanisms cannot be fully assessed. Based on the available code, the contract exhibits a highly centralized ownership model, complex and potentially high transaction fees, and intricate anti-bot/anti-whale mechanisms, all of which introduce significant security and economic risks.

> **Final Recommendation:** It is critical to provide the complete and verified source code for a comprehensive security audit. Without the full `_transfer` function, the contract's core functionality and security cannot be properly evaluated. We strongly recommend simplifying the token's economic model, particularly the fee structure and anti-bot mechanisms, to reduce complexity and potential attack vectors. Furthermore, consider implementing a multi-signature wallet for critical administrative functions to mitigate the risks associated with centralized control and a single point of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The technical architecture (7.1 Architecture) of FatToken is complex, incorporating various anti-bot and fee mechanisms. A critical issue is the incomplete source code, specifically the missing… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model (7.4 Economic) features highly dynamic and potentially high transaction fees (up to 25%), which can significantly impact user experience and market stability. The… |
| **Upgrades** | 8/10 | Low | The FatToken contract is not designed with upgradeability features (7.7 Upgrades), meaning its logic cannot be modified after deployment. This eliminates upgrade-related risks but also removes the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 3.8% |
| **LP Locked** | 78.2% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 21.3% |
| **Top-3 Unlocked** | 21.8% |

## Security Findings

_🔴 1 Critical · 🟠 3 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Incomplete Source Code Provided  *(Severity: Critical · Status: Unresolved)*

The provided source code is truncated, specifically missing the entire implementation of the `_transfer` function. This function is fundamental to any ERC-20 token, handling all token movements, applying fees, and enforcing anti-bot/anti-whale limits. Without this critical component, a comprehensive security audit of the token's core logic, economic model, and anti-manipulation features is impossible.

**Recommendation:** Provide the complete and verified source code for the FatToken contract, including all internal helper functions and the full `_transfer` implementation, to enable a thorough security assessment.


### `H-01` — High and Complex Transaction Fees  *(Severity: High · Status: Unresolved)*

The contract allows for transaction fees up to 25% (checked by `_buyFundFee + ... < 2500`). While explicitly capped, a 25% fee is exceptionally high and can deter legitimate trading, leading to poor liquidity and a negative user experience. The fee structure is also complex, with separate fund, LP, reward, and burn fees for both buy and sell transactions, increasing the likelihood of miscalculation or unexpected behavior.

**Recommendation:** Re-evaluate and significantly reduce the maximum allowable transaction fees to a more reasonable and sustainable level (e.g., below 10%). Simplify the fee structure by consolidating fee types where possible to reduce complexity and potential for errors.


### `H-02` — Centralized Control and Potential for Abuse  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants the contract owner extensive control over critical functionalities. The owner can enable/disable trading (`enableOffTrade`), adjust taxes (`enableChangeTax`), manage whitelists (`_feeWhiteList`, `_rewardList`, `isMaxEatExempt`), and control anti-bot mechanisms. This high degree of centralization creates a single point of failure, making the protocol vulnerable to malicious actions by a compromised or rogue owner, including potential rug pulls or market manipulation.

**Recommendation:** Consider implementing a multi-signature wallet for critical administrative functions to distribute control and reduce the risk associated with a single point of failure. Explore mechanisms to gradually decentralize control over time, such as time-locks for sensitive operations or community governance for parameter changes.


### `H-03` — Anti-Bot/Anti-Whale Mechanisms Complexity and Risk  *(Severity: High · Status: Unresolved)*

The contract incorporates a multitude of anti-bot and anti-whale mechanisms, including `maxBuyAmount`, `maxSellAmount`, `maxWalletAmount`, `_feeWhiteList`, `isMaxEatExempt`, `user2blocks`, `batchBots`, `enableKillBatchBots`, and `killBatchBlockNumber`. Such complex systems are notoriously difficult to implement without introducing unintended side effects, false positives, or bypasses. They can lead to legitimate users being blocked, create a honeypot scenario where only certain addresses can sell, or be exploited by sophisticated attackers.

**Recommendation:** Thoroughly review and simplify the anti-bot/anti-whale logic. Conduct extensive testing, including edge cases and adversarial simulations, to ensure fairness and prevent unintended consequences. Consider whether the benefits of these complex mechanisms outweigh the inherent risks and potential for abuse.


### `M-01` — Reward Path Configuration Risk  *(Severity: Medium · Status: Unresolved)*

The `rewardPath` array, crucial for multi-hop swaps in reward distribution and LP additions, is constructed with complex conditional logic in the constructor. The path depends on `currency`, `ETH`, and `_swapRouter.WETH()`. Incorrect configuration or unexpected values for these addresses could lead to an invalid swap path, causing reward distribution or liquidity provision functions to fail, effectively breaking a core part of the tokenomics.

**Recommendation:** Simplify the `rewardPath` construction logic if possible. Implement robust validation for `currency`, `ETH`, and `_swapRouter.WETH()` addresses to ensure they are valid and correctly configured. Consider adding owner-only functions to update the `rewardPath` in case of misconfiguration, along with a time-lock to prevent immediate malicious changes.


### `I-01` — `TokenDistributor` Approval Pattern  *(Severity: Informational · Status: Unresolved)*

The `TokenDistributor` contract's constructor immediately approves `msg.sender` for `uint256(~uint256(0))` (maximum allowance) of the specified token. While in this specific context, `FatToken` deploys `TokenDistributor` and thus `FatToken` itself receives the approval (likely for internal operations), this pattern can be risky if `TokenDistributor` is deployed by an untrusted address or with a malicious token, granting excessive control to the deployer.

**Recommendation:** Ensure that any deployment of `TokenDistributor` is done by a trusted entity and with a legitimate token. For future designs, consider if such a broad, immediate approval is strictly necessary or if a more granular, on-demand approval mechanism could be used to reduce potential attack surface.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe252...0b00`](https://bscscan.com/address/0xe252fcb1aa2e0876e9b5f3ed1e15b9b4d11a0b00) |
| **Network** | BNB Chain |
| **Price** | $0.002452 |
| **24h Volume** | $34.8K |
| **Liquidity** | $41.2K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 39.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.1% |
| **24h Transactions** | 425 buys / 708 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x52bf227c8d43026697fa5fa6cd4a81c446977130)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crystal-stones-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-05*
