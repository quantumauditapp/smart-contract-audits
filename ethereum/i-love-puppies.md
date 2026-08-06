---
token: I love puppies
ticker: PUPPIES
network: ethereum
risk_score: 31
status: medium
date: 2026-08-06
---

# I love puppies (PUPPIES) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/i-love-puppies-eth)

---

## Audit Summary

The puppies token contract implements a standard ERC-20 interface with custom tax mechanisms, anti-bot features, and liquidity management. The contract exhibits a high degree of centralization, with the owner possessing extensive control over critical parameters such as tax rates, transaction limits, and the ability to blacklist addresses. A significant concern is the mechanism for handling collected taxes, where ETH is sent directly to a designated wallet rather than being used to bolster liquidity, posing a substantial economic risk. While some security patterns like `SafeMath` and reentrancy guards are present, the overarching centralized control introduces critical vulnerabilities.

> **Final Recommendation:** Given the high degree of centralized control and the potential for economic manipulation, it is strongly recommended that potential users exercise extreme caution. The project team should consider implementing a timelock for critical owner-controlled functions to provide users with a window to react to impending changes. Additionally, a clear and transparent mechanism for managing collected taxes, ideally involving adding them back to the liquidity pool or a community-controlled treasury, would significantly mitigate the current economic risks. All critical parameter changes should emit events for transparency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes `SafeMath` for arithmetic operations, which is a good practice, although less critical in Solidity 0.8.x. A `lockTheSwap` modifier is implemented to prevent reentrancy during… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits extreme centralization, with the `owner` having full control over all critical economic parameters, including tax rates, transaction limits, and wallet size limits (7.3 Access… |
| **Upgrades** | 8/10 | Low | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its logic cannot be changed after deployment (7.7 Upgrades). This eliminates upgrade-specific risks but also… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 97.1% (≈ permanent lock) |
| **LP Locked** | 97.1% |

## Security Findings

_🔴 2 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Excessive Centralized Control by Owner  *(Severity: Critical · Status: Unresolved)*

The contract owner possesses extensive privileges, including the ability to set initial and final buy/sell taxes, reduce tax thresholds, modify maximum transaction and wallet sizes, exclude/include addresses from fees, and manage a 'bots' blacklist. This level of control allows the owner to unilaterally alter the token's economics and restrict user interactions, posing a significant risk of manipulation or a 'rug pull' scenario. For example, the owner can set taxes to 100% or blacklist all users, effectively trapping funds.

**Recommendation:** Implement a timelock for all critical owner-controlled functions to introduce a delay before changes take effect, allowing users to react. Consider decentralizing control over key parameters through a multi-signature wallet or a community governance mechanism. Clearly document all owner privileges and their intended use.


### `C-02` — Tax Wallet Draining and Lack of Liquidity Growth  *(Severity: Critical · Status: Unresolved)*

The contract's tax mechanism swaps collected tokens for ETH and then sends this ETH directly to the `_taxWallet` (controlled by the owner) via `sendETHToFee`. There is no provision to add this ETH back to the liquidity pool. This design means that all collected taxes are effectively siphoned off to the owner's wallet, leading to a gradual drain of value from the token's liquidity pool over time. This can severely impact the token's price stability and is a common pattern in 'rug pull' schemes.

**Recommendation:** Modify the tax mechanism to allocate a portion or all of the collected ETH to reinforce the liquidity pool (e.g., by pairing it with tokens and adding it to Uniswap). Alternatively, if the ETH is intended for project development, it should be sent to a transparent, multi-signature treasury with clear spending policies and public reporting.


### `H-01` — Abuse Potential of Anti-Bot/Anti-Whale Mechanisms  *(Severity: High · Status: Unresolved)*

The `_maxTxAmount`, `_maxWalletSize`, and `bots` mapping are intended to prevent malicious bot activity and whale manipulation. However, these parameters are fully controllable by the owner. The owner can arbitrarily set these limits to extremely low values or add legitimate user addresses to the `bots` list, effectively preventing users from buying, selling, or holding tokens, thereby trapping their funds or manipulating market dynamics.

**Recommendation:** If these mechanisms are deemed necessary, consider making the `_maxTxAmount` and `_maxWalletSize` immutable after a certain period or subject to a timelock. The `bots` mapping should be managed with extreme caution and transparency, ideally with a multi-signature wallet or community oversight, and clear criteria for inclusion/exclusion.


### `H-02` — Initial Trading Restrictions and Manipulation Risk  *(Severity: High · Status: Unresolved)*

The contract includes `_preventSwapBefore`, `_buyCount`, `tradingOpen`, and `swapEnabled` flags, all controlled by the owner. Trading is initially closed and must be opened by the owner. This gives the owner significant control over the initial trading phase, allowing for potential manipulation such as front-running the `openTrading` call or controlling early price action by selectively enabling/disabling swaps and adjusting taxes.

**Recommendation:** Clearly communicate the intended use and timeline for these initial trading restrictions. Consider making the `openTrading` function callable only once and making `_preventSwapBefore` immutable after a certain block number or timestamp. Ensure transparency around the activation of trading and swap functionalities.


### `M-01` — Sell Limit per Block Causes Denial of Service  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function implements a `require(sellCount < 3, "Only 3 sells per block!")` restriction. This limits the number of sell transactions that can occur within a single block. While intended to prevent rapid price drops, this mechanism can lead to a denial of service for legitimate users, especially during periods of high market volatility or when many users attempt to sell simultaneously, potentially trapping their tokens.

**Recommendation:** Re-evaluate the necessity and impact of the 'sells per block' limit. If a limit is critical, consider alternative mechanisms that are less prone to denial of service, such as a cooldown period per wallet or a dynamic limit based on liquidity. Ensure that any such mechanism does not disproportionately affect smaller holders or create an unfair selling environment.


### `M-02` — Lack of Event Emission for Critical Parameter Changes  *(Severity: Medium · Status: Unresolved)*

Many `onlyOwner` functions that modify critical contract parameters, such as `setInitialBuyTax`, `setMaxTxAmount`, `setMaxWalletSize`, and `setBots`, do not emit corresponding events. This lack of event emission makes it difficult for external parties (e.g., users, block explorers, monitoring tools) to track changes to the contract's operational parameters on-chain, reducing transparency and auditability.

**Recommendation:** Emit specific events for every function that modifies a critical contract parameter. These events should include the old and new values of the parameter, along with the address of the caller and a timestamp, to provide a clear and auditable history of changes.


### `L-01` — Hardcoded Uniswap Router Address in `openTrading`  *(Severity: Low · Status: Unresolved)*

The Uniswap V2 Router address (0x7a250d5630B4cF539739dF2C5dAcb4c659F2488D) is hardcoded within the `openTrading` function. While this is a common and stable address for Uniswap V2 on Ethereum mainnet, hardcoding can be inflexible if the router address ever changes or if the contract were to be deployed on a different network where this address is invalid.

**Recommendation:** Consider making the Uniswap router address configurable by the owner (e.g., via a `setRouter` function) or setting it in the constructor. If the contract is intended for a single network, ensure the hardcoded address is correct for that network. For multi-chain deployments, a configurable address is essential.


### `I-01` — Redundant Use of SafeMath in Solidity 0.8.x  *(Severity: Informational · Status: Unresolved)*

The contract explicitly uses the `SafeMath` library for arithmetic operations. While `SafeMath` is crucial for preventing integer overflow/underflow in older Solidity versions (prior to 0.8.0), Solidity 0.8.x and later versions include native overflow and underflow checks by default. Therefore, the explicit use of `SafeMath` for basic operations like `add`, `sub`, `mul`, and `div` is largely redundant and adds unnecessary gas cost and code complexity.

**Recommendation:** For Solidity 0.8.x and above, consider removing the `SafeMath` library and relying on the compiler's native overflow/underflow checks. This can reduce gas costs and simplify the codebase without compromising security for standard arithmetic. Ensure all custom or complex arithmetic logic is still thoroughly reviewed for potential edge cases.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcf91...6eb2`](https://etherscan.io/address/0xcf91b70017eabde82c9671e30e5502d312ea6eb2) |
| **Network** | Ethereum |
| **Price** | $0.00000019 |
| **24h Volume** | $173.2K |
| **Liquidity** | $787.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2y |
| **Top-10 Holders** | 12.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 326 buys / 225 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2325e3f261cadb1c30cebf66c9f95f6fb016c0d4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/i-love-puppies-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-06*
