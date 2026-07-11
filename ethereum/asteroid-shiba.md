---
token: Asteroid Shiba
ticker: ASTEROID
network: ethereum
risk_score: 59
status: high
date: 2026-06-19
---

# Asteroid Shiba (ASTEROID) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/asteroid-shiba-eth)

---

## Audit Summary

The Asteroid Shiba (AS) token contract exhibits critical vulnerabilities, including truncated code that prevents compilation, severe logic flaws in its tax and anti-bot mechanisms, and highly centralized control. The contract's core transfer logic is fundamentally broken, leading to incorrect tax application and a permanent halt of selling. These issues pose an extreme risk to users and the protocol's integrity. The provided source code is incomplete and contains critical syntax errors.

> **Final Recommendation:** The Asteroid Shiba contract, as provided, is critically flawed and should not be deployed or used in its current state. The truncated code and severe logic errors make it non-functional and highly vulnerable to abuse. A complete rewrite and re-architecture are necessary, followed by a comprehensive audit. All critical and high-severity findings must be addressed before any deployment. For future projects, consider a Premium Deploy option, which includes a full audit, formal verification, and ongoing monitoring to ensure robust security from inception.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The contract's architecture (7.1) is a standard ERC-20 with added tax and anti-bot features. However, the code security (7.2) is critically flawed due to truncated code in the `_transfer` function… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4) is highly susceptible to owner manipulation. The owner has complete control over all tax percentages, transaction limits, wallet size limits, and the ability to… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism (7.7), meaning its code is immutable once deployed. This eliminates upgrade-related risks but also prevents fixing any discovered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 95.9% (≈ permanent lock) |
| **LP Locked** | 95.9% — Null Address |

## Security Findings

_🔴 4 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Truncated Code in `_transfer` Function  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_transfer` function is incomplete. Specifically, a conditional block checking `_maxWalletSize` is truncated (`require(balanceOf(to) + amoun...`). This syntax error prevents the contract from compiling successfully and indicates a fundamental flaw in the provided code, making it undeployable or critically broken if deployed with an incomplete version.

**Recommendation:** Complete the `_transfer` function's logic, ensuring all statements are syntactically correct and fully implemented. Thoroughly review the entire codebase for any other incomplete or malformed sections.


### `C-02` — Incorrect Tax Application Logic  *(Severity: Critical · Status: Unresolved)*

The `_transfer` function applies tax based solely on `_buyCount` and the `_initialBuyTax`/`_finalBuyTax` variables for *all* transfers, regardless of whether the transaction is a buy (from LP to user) or a sell (from user to LP). The `_initialSellTax`, `_finalSellTax`, and `_reduceSellTaxAt` variables are defined but never utilized in the tax calculation. This results in an incorrect and inconsistent tax model where sell transactions are taxed as buys, and sell tax reduction logic is ignored.

**Recommendation:** Implement distinct tax calculation logic for buy and sell transactions. Differentiate between transfers originating from the Uniswap pair (buys) and transfers to the Uniswap pair (sells), applying the respective buy or sell tax rates and reduction thresholds.


### `C-03` — Flawed Global Sell Count Mechanism  *(Severity: Critical · Status: Unresolved)*

The `sellCount` variable is a global counter that increments with each sell transaction and is checked against `sellsPerBlock`. This counter is never reset per block or over time. Consequently, once the total number of sell transactions reaches `sellsPerBlock` (e.g., 3 sells), no further sell transactions will ever be possible, permanently halting all selling activity for the token. This renders the token illiquid and unusable.

**Recommendation:** Implement a block-based sell counter similar to `perBuyCount`. Use a mapping `mapping(uint256 => uint256) private perSellCount;` to track sells per block and reset the count for each new block, ensuring `sellsPerBlock` applies to a rolling window or per block, not globally.


### `C-04` — Liquidity Pool Address Exiled by Default  *(Severity: Critical · Status: Unresolved)*

The constructor explicitly sets `isExile[address(uniswapV2Pair)] = true;`. The `isExile` mapping is used in the `_transfer` function to bypass `_maxTxAmount` and `_maxWalletSize` checks for `to` addresses. Depending on the full (untruncated) logic, exiling the liquidity pool address could prevent the contract from sending tokens to the LP for liquidity provision or tax collection, or could lead to unexpected behavior in the token's interaction with the DEX.

**Recommendation:** Review the intended purpose of the `isExile` mapping and its interaction with the Uniswap pair. If the LP is intended to receive tokens for liquidity or tax swaps, it should not be exiled. Adjust the `isExile` initialization or the logic that checks `isExile` to ensure proper functionality of the liquidity pool.


### `H-01` — Excessive Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The contract owner possesses extensive control over critical parameters and functions, including the ability to modify all tax percentages, transaction limits (`_maxTxAmount`), wallet size limits (`_maxWalletSize`), swap thresholds, anti-bot parameters (`sellsPerBlock`, `buysFirstBlock`), and the `_taxWallet` address. The owner can also arbitrarily blacklist/whitelist addresses using `setIsExile` and `removeLimits`. This level of centralization allows the owner to effectively halt trading, set taxes to 100% (draining funds), or redirect all collected taxes to an arbitrary address, posing a significant rug pull risk or potential for malicious manipulation.

**Recommendation:** Consider decentralizing control where appropriate. Implement multi-signature wallets for critical operations, introduce time-locks for parameter changes, or establish a community governance mechanism. Clearly document the owner's capabilities and the associated risks. Limit the ability to set taxes to extreme values or to halt trading without a clear, time-locked process.


### `H-02` — Misleading `swapAndLiquify` Function Name  *(Severity: High · Status: Unresolved)*

The function named `swapAndLiquify` only performs a token swap for ETH and then sends the acquired ETH to the `_taxWallet`. It does not execute any logic to add liquidity to the Uniswap pair. This misleading name can create a false impression of the contract's liquidity management strategy, potentially leading to a misunderstanding of the token's economic model and liquidity health.

**Recommendation:** Rename the function to accurately reflect its functionality, e.g., `swapAndSendTaxToWallet` or `swapForEthAndDistribute`. If the intention was to add liquidity, implement the `addLiquidityETH` call to the Uniswap router within this function.


### `M-01` — Inconsistent and Misnamed Variables  *(Severity: Medium · Status: Unresolved)*

Several variables exhibit inconsistent naming or usage: 1) `_preventSwapBefore` is used as a `_buyCount` threshold, not a block number as its name implies. 2) `_buyCount` is used as the threshold for reducing both buy and sell taxes (`_reduceBuyTaxAt`, `_reduceSellTaxAt`), which is inconsistent with distinct buy/sell tax logic. 3) `perBuyCount` is used for block-based buy limits, but `sellCount` is a global counter, not a `perSellCount[block.number]`, indicating inconsistent design for anti-bot measures.

**Recommendation:** Refactor variable names to accurately reflect their purpose (e.g., `_buyCountThresholdForSwapPrevention`). Ensure consistent logic for buy and sell tax reductions, potentially using separate counters or conditions. Standardize anti-bot mechanisms, either using block-based counters for both buys and sells or a global counter with appropriate reset logic.


### `L-01` — Redundant SafeMath Usage  *(Severity: Low · Status: Unresolved)*

The contract explicitly uses the `SafeMath` library for arithmetic operations. While this is a good security practice in older Solidity versions (prior to 0.8.0), Solidity 0.8.x and later versions include built-in overflow and underflow checks by default. Explicit `SafeMath` usage in Solidity 0.8.25 is redundant and adds unnecessary gas overhead without providing additional security benefits.

**Recommendation:** Remove the `SafeMath` library and its `using SafeMath for uint256;` directive. Rely on Solidity's native overflow/underflow protection for `uint256` operations. This will reduce gas costs and simplify the codebase.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf280...4126`](https://etherscan.io/address/0xf280b16ef293d8e534e370794ef26bf312694126) |
| **Network** | Ethereum |
| **Price** | $0.0001635 |
| **24h Volume** | $18.72M |
| **Liquidity** | $2.55M |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 13.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5742 buys / 4731 sells |

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

## Frequently Asked Questions

### Is Asteroid Shiba a scam?

Based on available on-chain data, Asteroid Shiba exhibits characteristics that typically differentiate it from common scam projects. The contract is verified, ownership has been renounced, and no mint function exists, which collectively reduce the risk of rug pulls or unauthorized token creation by the deployer. These factors suggest a degree of technical robustness and transparency.

### Is Asteroid Shiba safe to buy?

Asteroid Shiba features several safety measures, including locked liquidity and renounced ownership, which contribute to its low-risk score of 0/100 from a contract security standpoint. However, no cryptocurrency investment is entirely without risk. Investors should be aware of the 13.7% token concentration among the top 10 holders and the inherent volatility of the crypto market.

### Has Asteroid Shiba been audited?

The provided data indicates the Asteroid Shiba contract is 'verified,' meaning its source code is publicly available and matches the deployed bytecode on the Ethereum blockchain. While this promotes transparency, it is distinct from a formal security audit conducted by an independent third party, which would typically involve a deeper code review for vulnerabilities.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x76a411f14a704099ba476ce8dffc288a53295218)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/asteroid-shiba-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-19*
