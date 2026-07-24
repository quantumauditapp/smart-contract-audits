---
token: wojak
ticker: WOJAK
network: ethereum
risk_score: 32
status: medium
date: 2026-06-10
---

# wojak (WOJAK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 32/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wojak-eth)

---

## Audit Summary

The Wojak Token contract is an ERC-20 token implementation with extensive owner-controlled features, including configurable transaction fees, maximum transaction/wallet limits, minting capabilities, and a liquidity generation mechanism. While leveraging OpenZeppelin's secure base contracts, the high degree of centralization introduces significant economic and operational risks. The owner possesses the ability to drastically alter tokenomics, potentially leading to a honeypot scenario or liquidity rug-pull. Technical aspects like unchecked external call return values and lack of slippage protection in swaps also present vulnerabilities.

> **Final Recommendation:** Given the extreme centralization, it is crucial for the project to clearly communicate the extent of owner privileges to all potential users and investors. Consider implementing a multi-signature wallet for ownership and introducing time-locks for critical parameter changes to reduce single-point-of-failure risks and increase transparency. For all swap operations, implement a `minAmountOut` parameter to protect against slippage and front-running. Ensure that all external ERC20 calls check their return values to prevent unexpected failures. For enhanced transparency and off-chain monitoring, emit events for all state-changing functions, especially those modifying critical token parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes OpenZeppelin's battle-tested ERC20 and Ownable implementations, providing a solid foundation (7.1 Architecture, 7.2 Code Security). A reentrancy guard (`inSwapAndLiquify`) is… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits extreme centralization, with the owner having unilateral control over critical token parameters (7.3 Access Control, 7.5 Governance). The owner can set arbitrary transaction… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgrade mechanism (7.7 Upgrades). This means its logic is immutable after deployment, eliminating upgrade-related risks but also preventing future bug fixes or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Extreme Centralization and Honeypot Risk  *(Severity: Critical · Status: Unresolved)*

The contract grants the owner extensive control over critical token parameters, including the ability to set arbitrary transaction and wallet limits, adjust transfer fees (tax and liquidity fees) up to 100%, mint new tokens, pause trading, and exclude specific addresses from all tokenomics. This level of control allows the owner to manipulate the token's economy at will, potentially creating a honeypot scenario where users can buy but are prevented from selling or face prohibitive fees. This impacts 7.3 Access Control, 7.4 Economic, 7.5 Governance, and 7.8 Operations.

**Recommendation:** Implement a multi-signature wallet for ownership, introduce time-locks for critical parameter changes, or decentralize control through a governance mechanism. Clearly communicate the extent of owner privileges to users and consider capping fees and limits at reasonable, non-exploitable levels.


### `H-01` — Lack of Minimum Amount Out in Swaps  *(Severity: High · Status: Unresolved)*

The `_swapAndLiquify` function, as well as `swapTokensForEth` and `addLiquidity`, use Uniswap's `swapExactTokensForETHSupportingFeeOnTransferTokens` without specifying a `minAmountOut` parameter. This omission exposes the swap operation to sandwich attacks and significant slippage, especially during periods of high volatility or low liquidity, potentially leading to a loss of value for the tokens being swapped. This impacts 7.2 Code Security and 7.4 Economic.

**Recommendation:** Implement a `minAmountOut` parameter in all swap functions to protect against excessive slippage and front-running. This value should ideally be calculated based on current market conditions or a user-defined tolerance.


### `H-02` — Owner Can Drain Liquidity Pool Tokens  *(Severity: High · Status: Unresolved)*

The `_swapAndLiquify` function adds liquidity to the Uniswap pair, and the resulting LP tokens are sent to the contract itself. The `rescueERC20` function, callable by the owner, allows the owner to withdraw any ERC20 tokens held by the contract. This means the owner can withdraw the LP tokens, effectively removing liquidity from the pool and potentially rug-pulling investors. This impacts 7.3 Access Control and 7.4 Economic.

**Recommendation:** Implement a mechanism to burn LP tokens or send them to a locked, unspendable address (e.g., the zero address) to ensure liquidity remains permanently locked. If LP tokens are intended to be managed, a transparent and secure governance or time-lock mechanism should be in place for their withdrawal.


### `M-01` — Configurable Router and Pair Addresses  *(Severity: Medium · Status: Unresolved)*

The owner can update the `uniswapV2Router` and `uniswapV2Pair` addresses via `updateUniswapV2Router` and `updateUniswapV2Pair` functions. While this offers flexibility, a malicious or compromised owner could redirect token swaps and liquidity additions to a fraudulent router or pair contract, leading to loss of funds or manipulation of the token's market. This impacts 7.3 Access Control and 7.6 External.

**Recommendation:** Consider making these addresses immutable after deployment or implementing a time-lock for changes to critical external contract addresses. If flexibility is required, ensure robust monitoring and transparency around such changes.


### `M-02` — Unchecked Return Values of External Calls  *(Severity: Medium · Status: Unresolved)*

The `_swapAndLiquify` and `swapTokensForEth` functions call `IERC20(token).approve(address(this), type(uint256).max)` without checking the boolean return value. While many ERC20 tokens revert on failure, some older or non-standard implementations might return `false` instead. Ignoring this return value could lead to a false assumption that the approval succeeded, potentially causing subsequent operations to fail unexpectedly. This impacts 7.2 Code Security.

**Recommendation:** Always check the boolean return value of external ERC20 calls, especially `transfer`, `transferFrom`, and `approve`, to ensure the operation was successful. For example, `require(IERC20(token).approve(...), "ERC20: approve failed");`.


### `L-01` — Lack of Events for Critical Parameter Changes  *(Severity: Low · Status: Unresolved)*

Several owner-controlled functions that modify critical parameters, such as `setMaxTxAmount`, `setMaxWalletAmount`, `setSwapAndLiquifyThreshold`, `setNumTokensSellToAddToLiquidity`, `setRouterAddress`, `setPairAddress`, `setTradingOpen`, `excludeFromMaxTx`, `includeInMaxTx`, `excludeFromMaxWallet`, `includeInMaxWallet`, `excludeFromSwap`, `includeInSwap`, do not emit events. This makes it difficult for off-chain monitoring tools and users to track changes to the token's behavior and parameters, reducing transparency. This impacts 7.8 Operations.

**Recommendation:** Emit explicit events for all functions that modify critical contract state variables. This enhances transparency and allows for easier monitoring and auditing of contract behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8de3...31ef`](https://etherscan.io/address/0x8de39b057cc6522230ab19c0205080a8663331ef) |
| **Network** | Ethereum |
| **Price** | $0.00000007 |
| **24h Volume** | $190.3K |
| **Liquidity** | $889.0K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 38.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xcaa3a16f8440f85303afaab1992f2b97d12469b1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wojak-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
