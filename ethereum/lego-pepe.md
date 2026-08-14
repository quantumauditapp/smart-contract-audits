---
token: Lego Pepe
ticker: LEPE
network: ethereum
risk_score: 61
status: high
date: 2026-08-14
---

# Lego Pepe (LEPE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 61/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lego-pepe-eth)

---

## Audit Summary

The LEPE token contract implements an ERC-20 standard with custom tax, anti-whale, and automated liquidity features. While utilizing SafeMath for arithmetic safety, the contract exhibits critical centralization risks due to extensive owner privileges, including the ability to control all economic parameters and potentially rug-pull liquidity. Several denial-of-service vectors and a lack of slippage protection in automated swaps also pose significant risks to users.

> **Final Recommendation:** Given the critical risks identified, particularly the unlocked liquidity pool and extensive owner control, it is strongly recommended that potential users exercise extreme caution. The project team should consider implementing a timelock for critical owner functions and locking liquidity to build trust. Furthermore, the automated swap mechanism requires robust slippage protection to prevent value loss during execution.

For long-term security and decentralization, explore options to gradually reduce owner privileges or transition to a community-governed model. Ensure all critical parameter changes emit events for transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes `SafeMath` to prevent common integer overflow/underflow issues and implements a `lockTheSwap` modifier to mitigate reentrancy during automated token swaps (7.2 Code Security).… |
| **Governance / Economics** | 2/10 | High | The contract employs an `Ownable` access control pattern, granting the deployer extensive control over critical parameters like tax rates, transaction limits, and the ability to block addresses (7.3… |
| **Upgrades** | 8/10 | Low | The LEPE contract is not designed with an upgradeable proxy pattern, meaning its core logic cannot be directly modified after deployment (7.7 Upgrades). While this prevents direct code upgrades, the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 2 Low_

### `C-01` — Centralized Control and Excessive Owner Privileges  *(Severity: Critical · Status: Unresolved)*

The `Ownable` pattern grants the contract owner extensive control over critical functions and parameters. The owner can modify all tax rates (`setInitialBuyTax`, `setFinalSellTax`), transaction limits (`setMaxTxAmount`, `setMaxWalletSize`), enable/disable swaps (`setSwapEnabled`), add/remove addresses from the `bots` mapping, and update the Uniswap router. This level of centralization allows the owner to significantly alter the token's economics, halt trading, or arbitrarily block users, posing a severe risk of manipulation or malicious action (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet or a timelock contract for critical administrative functions to introduce a delay before changes take effect, allowing the community to react. Consider gradually decentralizing control over key parameters or limiting the owner's ability to make drastic changes without community consensus.


### `C-02` — Unlocked Liquidity Pool (Rug Pull Risk)  *(Severity: Critical · Status: Unresolved)*

The provided prefill information indicates that the liquidity pool (LP) is 'unlocked'. The `addLiquidityETH` function is restricted to the owner. This means the owner has the ability to add liquidity to the Uniswap pair and subsequently remove it at any time, effectively performing a 'rug pull' by draining the liquidity and rendering the token worthless. This is a critical economic vulnerability (7.4 Economic).

**Recommendation:** Immediately lock the liquidity pool tokens with a reputable third-party locker service for a significant duration (e.g., 1-5 years or permanently). Provide verifiable proof of the locked LP to the community to build trust and mitigate this critical risk.


### `H-01` — Potential Denial of Service (DoS) Vectors  *(Severity: High · Status: Unresolved)*

The contract contains several mechanisms that could lead to denial of service:  1.  **Swap Failure:** The `_transfer` function calls `swapTokensForEth`. If this external call to `IUniswapV2Router02` fails (e.g., due to network congestion, router issues, or insufficient `amountOutMin`), the entire `_transfer` transaction will revert, potentially blocking all transfers when `swapEnabled` is true and `_taxSwapThreshold` is met (7.2 Code Security). 2.  **Sell Limit:** The `require(sellCount < 3, "Only 3 sells per block!")` condition can prevent legitimate users from selling their tokens, especially during periods of high trading volume, leading to frustration and potential losses (7.2 Code Secu…

**Recommendation:** For swap failures, consider implementing a try-catch block around the external swap call to handle failures gracefully without reverting the entire transfer. For sell limits, re-evaluate the necessity and impact on user experience; if kept, ensure clear communication. For bot/wallet limits, ensure transparent policies and consider community-driven mechanisms for managing such lists.


### `H-02` — Slippage Vulnerability in Automated Swaps  *(Severity: High · Status: Unresolved)*

The `swapTokensForEth` function calls `IUniswapV2Router02.swapExactTokensForETHSupportingFeeOnTransferTokens`. This function requires an `amountOutMin` parameter to protect against slippage. However, the contract passes `0` as `amountOutMin`, meaning the swap can execute regardless of the output ETH amount. This exposes the automated tax swap to significant slippage, front-running attacks, and potential value loss, especially during volatile market conditions or if a malicious actor manipulates the pool (7.2 Code Security, 7.4 Economic).

**Recommendation:** Implement a robust mechanism to calculate and enforce a reasonable `amountOutMin` for the automated swap. This could involve using a price oracle, a fixed percentage slippage tolerance, or allowing the owner to configure a dynamic slippage parameter. This is crucial to protect the value of the collected tax tokens.


### `M-01` — Dynamic and High Tax Rates  *(Severity: Medium · Status: Unresolved)*

The contract implements dynamic buy and sell taxes (`_initialBuyTax`, `_initialSellTax`, `_finalBuyTax`, `_finalSellTax`) that can be as high as 13% for buys and 12% for sells. These rates can change based on `_buyCount` thresholds. Such high and variable taxes can be confusing for users, significantly impact trading economics, and potentially deter participation. The owner has full control to modify these rates at any time (7.4 Economic).

**Recommendation:** Clearly communicate the tax structure and its dynamic nature to users. Consider setting more predictable and potentially lower tax rates to encourage trading. If dynamic taxes are essential, ensure the logic is thoroughly tested and transparent. Implement a timelock for changes to tax rates.


### `M-02` — Anti-Bot/Anti-Whale Mechanisms Introduce Centralization  *(Severity: Medium · Status: Unresolved)*

The contract includes `bots` mapping, `_maxTxAmount`, and `_maxWalletSize` to prevent manipulation and large holdings. While intended to protect against malicious actors, these mechanisms introduce significant centralization. The owner can arbitrarily add/remove addresses from the `bots` list or adjust transaction/wallet limits, potentially blocking legitimate users or manipulating market dynamics. This creates an unfair and unpredictable trading environment (7.3 Access Control, 7.4 Economic).

**Recommendation:** Carefully evaluate the necessity and implementation of these anti-bot/anti-whale features. If retained, establish clear, transparent criteria for their use and consider community oversight or a timelock for changes. Ensure these mechanisms cannot be easily bypassed or misused by the owner.


### `L-01` — Hardcoded Tax Wallet Address  *(Severity: Low · Status: Unresolved)*

The `_taxWallet` address is hardcoded in the constructor (`_taxWallet = payable(0x6db149730442a30BbaCe3aEf29Ee894C9897a6D9);`). While there is an `onlyOwner` function `setTaxWallet` to change it, if the owner renounces ownership, this address becomes immutable. If the hardcoded wallet's private key is lost or compromised, the collected tax funds would become inaccessible or vulnerable (7.8 Operations).

**Recommendation:** Ensure the `_taxWallet` is a secure, multi-signature wallet. If ownership is to be renounced, ensure the `_taxWallet` is set to a robust, community-controlled or immutable address beforehand. Consider making the initial `_taxWallet` configurable during deployment rather than hardcoded.


### `L-02` — Lack of Event Emission for Critical Parameter Changes  *(Severity: Low · Status: Unresolved)*

Many `onlyOwner` functions that modify critical contract parameters (e.g., `setInitialBuyTax`, `setFinalSellTax`, `setReduceBuyTaxAt`, `setPreventSwapBefore`, `setTaxSwapThreshold`, `setMaxTaxSwap`, `setBots`, `setSwapEnabled`) do not emit corresponding events. Without events, it is difficult for off-chain monitoring systems, users, and block explorers to track changes to the contract's behavior and economic parameters, reducing transparency and auditability (7.8 Operations).

**Recommendation:** Emit specific events for all functions that modify critical contract state variables. This enhances transparency, allows for easier monitoring, and improves the overall auditability of the contract's operational history.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x396c...b623`](https://etherscan.io/address/0x396cdce1ef151c9d58fbdcf54c5e948a6a52b623) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $38.6K |
| **Liquidity** | $8.8K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 185 buys / 152 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xfa356393ccf8e16dfac8b0172340f5c1e3c9d814)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lego-pepe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
