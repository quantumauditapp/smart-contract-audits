---
token: Yee Token
ticker: YEE
network: ethereum
risk_score: 0
status: low
date: 2026-08-13
---

# Yee Token (YEE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yee-token-eth)

---

## Audit Summary

The YEE token contract implements a standard ERC-20 interface with several custom features including dynamic transaction fees, anti-MEV mechanisms, a max wallet limit, and an automated swapback function. The contract utilizes the Ownable pattern for administrative control. Key risks identified include the use of `amountOutMin = 0` in Uniswap swaps, which exposes funds to significant slippage or MEV attacks, and an unreliable anti-MEV mechanism based on `extcodesize`. High transaction fees and centralized control also present economic and governance risks.

> **Final Recommendation:** It is strongly recommended to address the critical security vulnerabilities related to the `swapback` function's `amountOutMin` parameter to prevent potential financial losses from MEV or high slippage. The anti-MEV mechanism relying on `extcodesize` should be re-evaluated and replaced with more robust, decentralized, or proven solutions. Furthermore, consider implementing multi-signature control for the owner functions to mitigate centralization risks and enhance operational security. Review the economic parameters, especially the high transaction fees, to ensure they align with the project's long-term sustainability and user adoption goals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The YEE token contract (7.1 Architecture) extends ERC-20 with custom transfer logic, including dynamic fees, anti-MEV measures, and an automated swapback to ETH. The `_transfer` function handles… |
| **Governance / Economics** | 8/10 | Low | The contract employs the Ownable pattern (7.3 Access Control), granting the deployer significant control over critical parameters such as `tradingOpen`, `antiMEV`, and potentially fee structures… |
| **Upgrades** | 10/10 | Low | The YEE token contract is not designed with an upgradeability pattern (7.7 Upgrades). It is a standard, non-proxy implementation, meaning its logic cannot be modified after deployment. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `H-01` — Lack of Slippage Protection in Swapback Function  *(Severity: High · Status: Unresolved)*

The `swapback` function calls `uniswapRouter.swapExactTokensForETHSupportingFeeOnTransferTokens` with `amountOutMin` set to `0`. This means the contract accepts any amount of ETH in return for the tokens, regardless of how unfavorable the exchange rate is. This vulnerability can be exploited by front-running bots or MEV (Maximal Extractable Value) attacks, leading to significant losses of value during the swap process. (7.2 Code Security, 7.4 Economic)

**Recommendation:** Implement a reasonable `amountOutMin` value in the `swapExactTokensForETHSupportingFeeOnTransferTokens` call within the `swapback` function. This value should be calculated based on the expected output amount and a tolerable slippage percentage, protecting the contract from unfavorable trades. Consider using Chainlink price feeds or a time-weighted average price (TWAP) oracle to determine a safe minimum output amount.


### `H-02` — Unreliable Anti-MEV Mechanism Using extcodesize  *(Severity: High · Status: Unresolved)*

The `ensureOneHuman` function, part of the anti-MEV mechanism, attempts to identify contracts using `extcodesize`. This method is unreliable because `extcodesize` returns 0 during a contract's constructor execution, allowing a malicious contract to bypass the check. Attackers can deploy contracts that interact with the token within their constructor, appearing as an EOA (Externally Owned Account) and circumventing the anti-MEV logic. (7.2 Code Security)

**Recommendation:** Relying on `extcodesize` for security-critical decisions is a known anti-pattern. Re-evaluate the anti-MEV strategy. Consider alternative, more robust methods for bot detection or implement a time-based delay for new liquidity providers to mitigate front-running without relying on `extcodesize`.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract uses the `Ownable` pattern, granting the deployer (owner) significant control over critical contract functionalities. While specific setter functions are not fully provided, the presence of `tradingOpen`, `antiMEV`, `_blocked`, and `isContractExempt` flags suggests that the owner can enable/disable trading, anti-MEV, block addresses, or exempt addresses from certain rules. This centralization (7.3 Access Control, 7.5 Governance) introduces a single point of failure and a high degree of trust in the owner's actions, which could be a risk if the owner's private key is compromised or acts maliciously. (7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) as the contract owner to distribute control and require multiple approvals for sensitive operations. Alternatively, implement a time-locked governance mechanism for critical changes to provide transparency and allow the community to react to potentially malicious actions.


### `M-02` — High and Dynamic Transaction Fees  *(Severity: Medium · Status: Unresolved)*

The contract implements high transaction fees (25% buy tax, 25% sell tax) and an even higher sniper tax (49%) for early trades or blocked addresses. While intended to manage tokenomics, such high and dynamic fees can significantly deter legitimate trading, reduce liquidity, and make the token less attractive for long-term holders. It can also lead to unpredictable price movements and user frustration. (7.4 Economic)

**Recommendation:** Evaluate the long-term impact of such high transaction fees on token adoption and liquidity. Consider reducing the fees to a more sustainable level or implementing a more gradual fee reduction mechanism over time. Clearly communicate the fee structure and its purpose to users.


### `L-01` — Unused State Variables  *(Severity: Low · Status: Unresolved)*

The contract declares state variables `preLaunch` and `tradeCooldown` but they are not used anywhere in the provided code snippet. Unused variables can indicate incomplete features, dead code, or potential for future functionality that was not fully implemented. While not a direct security vulnerability, it adds unnecessary complexity and consumes gas for storage. (7.2 Code Security)

**Recommendation:** Remove unused state variables to reduce contract size, optimize gas consumption, and improve code clarity. If these variables are intended for future features, ensure they are properly documented or implemented.


### `I-01` — Hardcoded Uniswap Router Address  *(Severity: Informational · Status: Unresolved)*

The Uniswap V2 Router address (0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D) is hardcoded as an `immutable` constant. While this is common for well-established protocols, it means the contract cannot adapt if Uniswap's router address changes or if the project wishes to migrate to a different DEX or a newer version of Uniswap. (7.6 External)

**Recommendation:** For future flexibility, consider making critical external contract addresses configurable by the owner, perhaps through an `onlyOwner` setter function. This allows for adaptability to ecosystem changes without requiring a full contract redeployment. However, for immutable addresses like Uniswap V2, this is often an acceptable design choice.


### `I-02` — Large Allowance in Swapback Function  *(Severity: Informational · Status: Unresolved)*

The `swapback` function approves the Uniswap router for `_totalSupply` (1 billion tokens) if the current allowance is insufficient. While this is a common pattern to avoid repeated approvals, it grants the router a very large, potentially unlimited, allowance. If the Uniswap router contract were to be compromised, it could theoretically drain the entire token balance held by the YEE contract. (7.2 Code Security)

**Recommendation:** Consider approving only the exact `tokenAmount` required for the swap, or a more conservative, yet sufficient, amount. While the risk of the Uniswap router being compromised is low, minimizing exposure is a good security practice. Alternatively, ensure the `swapback` function's logic is robust against reentrancy or unexpected external calls.


### `I-03` — Renounce Ownership Functionality  *(Severity: Informational · Status: Unresolved)*

The `renounceOwnership` function is present, allowing the owner to transfer ownership to the zero address. If this function is called, the contract will become unowned, and all `onlyOwner` functions will become permanently inaccessible. This could lead to a 'rug pull' scenario if critical parameters are not set correctly before renouncing, or if future maintenance is required. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Ensure all critical configurations are finalized and immutable before considering renouncing ownership. If renouncing ownership is part of the project's decentralization roadmap, clearly communicate the implications to the community. Consider transferring ownership to a community-governed multi-signature wallet or a DAO instead of renouncing it entirely.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9ac9...77fd`](https://etherscan.io/address/0x9ac9468e7e3e1d194080827226b45d0b892c77fd) |
| **Network** | Ethereum |
| **Price** | $0.00298 |
| **24h Volume** | $48.2K |
| **Liquidity** | $355.3K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 18.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 47 buys / 68 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xbc7ce7b6b5437d7d715fbb1cc7b4ec12399c5516)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yee-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
