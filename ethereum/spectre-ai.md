---
token: SPECTRE AI
ticker: SPECTRE
network: ethereum
risk_score: 25
status: low
date: 2026-09-15
---

# SPECTRE AI (SPECTRE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spectre-ai-eth)

---

## Audit Summary

The SpectreAI token contract implements standard ERC-20 functionality with additional features like transaction taxes, anti-whale/anti-bot mechanisms, and an automatic liquidity provision system. The audit identified a critical reentrancy-related vulnerability in the swap mechanism that can halt fee collection, alongside high-severity centralization risks and reliance on `block.timestamp` for security. Several medium and low-severity issues were also found, primarily concerning transparency and potential for economic manipulation by the owner.

> **Final Recommendation:** Address the critical reentrancy vulnerability by ensuring the `inSwapAndLiquify` flag is properly reset after the external swap call. Implement robust checks for `amountOutMin` in swap functions to mitigate slippage and sandwich attacks. Enhance transparency by emitting events for all critical state changes, such as tax adjustments and limit modifications. Consider decentralizing control over key parameters or implementing a timelock for sensitive administrative actions to reduce reliance on a single owner.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract's technical architecture (7.1) is a standard ERC-20 with added tax and anti-bot logic. Code security (7.2) is compromised by a critical reentrancy vulnerability in the `_transfer`… |
| **Governance / Economics** | 7/10 | Low | The economic model (7.4) includes buy/sell taxes and anti-whale/anti-bot limits. However, the governance model (7.5) is highly centralized, with the owner having extensive control over these… |
| **Upgrades** | 9/10 | Low | The SpectreAI contract is not designed as an upgradeable proxy contract (7.7). It is a standard, non-upgradeable implementation. Therefore, there are no upgrade-related risks or concerns. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, TeamFinance |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Reentrancy Vulnerability / Stuck Swap Mechanism  *(Severity: Critical · Status: Unresolved)*

The `_transfer` function's logic for swapping tokens to ETH (when `to == uniswapV2Pair`) uses an `inSwapAndLiquify` flag to prevent reentrancy during the external call to `uniswapV2Router.swapExactTokensForETHSupportingFeeOnTransferTokens`. However, the provided code snippet shows that `inSwapAndLiquify` is set to `1` before the external call but is never reset to `0`. This means that once a swap is initiated, the `inSwapAndLiquify` flag will remain `1` indefinitely, preventing any subsequent fee collection or liquidity provision through this mechanism. This effectively halts a core economic function of the token.

**Recommendation:** Ensure the `inSwapAndLiquify` flag is reset to `0` immediately after the external call to `uniswapV2Router.swapExactTokensForETHSupportingFeeOnTransferTokens` completes. A common pattern is to use a `try-catch` block or a `modifier` to ensure the flag is reset even if the external call reverts.


### `H-01` — Excessive Centralization of Control  *(Severity: High · Status: Unresolved)*

The `Ownable` contract grants the owner extensive control over critical contract parameters and functions. The owner can `addExcludedWallet`, `openTrading`, `setLimit`, `removeAllLimits`, and `changeTax` without any timelock or community governance. This high degree of centralization introduces significant trust assumptions, as a malicious or compromised owner could manipulate taxes, disable limits, or exclude specific wallets from fees, potentially leading to economic exploitation or unfair advantage.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or introducing a timelock mechanism for sensitive administrative functions. This would provide a delay before critical changes take effect, allowing the community to react and reducing the risk of immediate malicious actions. Explore options for decentralizing control over key parameters through a governance mechanism.


### `H-02` — Reliance on `block.timestamp` for Anti-Bot Measures  *(Severity: High · Status: Unresolved)*

The `_delayBetweenTx` mechanism, intended to prevent rapid transactions (e.g., by bots), relies on `block.timestamp`. Miners have a degree of control over `block.timestamp` (they can set it within a certain range, typically up to 900 seconds in the future on Ethereum). This manipulation could potentially allow sophisticated bots or miners to bypass or exploit the transaction delay protection, undermining the anti-bot measures.

**Recommendation:** While `block.timestamp` is commonly used, be aware of its limitations. For more robust time-based security, consider using `block.number` in conjunction with an estimated block time, or integrate with a decentralized oracle network that provides reliable timestamp data if precise, unmanipulable time is critical. For simple delays, `block.timestamp` is often acceptable, but the risk should be acknowledged.


### `M-01` — Potential Slippage or Sandwich Attack Vulnerability in Swap  *(Severity: Medium · Status: Unresolved)*

The code snippet for `uniswapV2Router.swapExactTokensForETHSupportingFeeOnTransferTokens` is truncated. If the `amountOutMin` parameter is not properly calculated and set to a non-zero value, the swap operation could be vulnerable to sandwich attacks or significant slippage. An `amountOutMin` of zero or a very low value allows attackers to front-run the transaction, manipulate the price, and profit from the difference, resulting in fewer ETH received by the contract for the swapped tokens.

**Recommendation:** Ensure that `amountOutMin` is always calculated based on a reasonable slippage tolerance (e.g., 0.5% to 1%) and passed to the `swapExactTokensForETHSupportingFeeOnTransferTokens` function. This protects the contract from receiving significantly less ETH than expected due to price manipulation or high network congestion.


### `L-01` — Lack of Event Emission for Critical State Changes  *(Severity: Low · Status: Unresolved)*

Several critical administrative functions, such as `setLimit`, `removeAllLimits`, `changeTax`, and `addExcludedWallet`, do not emit corresponding events upon execution. While the state changes occur on-chain, the absence of events makes it difficult for off-chain applications, block explorers, and users to monitor these significant administrative actions. This reduces transparency and auditability of the contract's operational history.

**Recommendation:** Emit specific events for all functions that modify critical contract state. For example, `event TaxChanged(uint256 newBuyTax, uint256 newSellTax)` or `event WalletExcluded(address indexed wallet, bool isExcluded)`. This enhances transparency and allows for easier monitoring and auditing of administrative actions.


### `I-01` — Hardcoded Uniswap Router Address  *(Severity: Informational · Status: Unresolved)*

The Uniswap V2 Router address (0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D) is hardcoded in the contract's constructor. While this is a common practice for well-established protocols, it means that if the Uniswap router address ever changes (e.g., due to an upgrade or migration) or if the project wishes to integrate with a different DEX, the contract would need to be redeployed. This lacks flexibility.

**Recommendation:** Consider making critical external contract addresses configurable by the owner (with appropriate access control and timelocks) or through a governance mechanism. This would allow for greater flexibility in adapting to ecosystem changes without requiring a full contract redeployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9cf0...dad6`](https://etherscan.io/address/0x9cf0ed013e67db12ca3af8e7506fe401aa14dad6) |
| **Network** | Ethereum |
| **Price** | $0.5735 |
| **24h Volume** | $79.1K |
| **Liquidity** | $511.2K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 20.8% of supply |
| **Buy / Sell Tax** | 5.0% / 5.0% |
| **24h Transactions** | 82 buys / 29 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x8a6d9525a0f07dcdc17fff15644342c314025a80)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spectre-ai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
