---
token: Clawd
ticker: CLAWD
network: ethereum
risk_score: 29
status: medium
date: 2026-06-20
---

# Clawd (CLAWD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 29/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clawd-eth)

---

## Audit Summary

The Clawd token contract implements a standard ERC-20 token with advanced tax, anti-bot, and automated liquidity features. While it incorporates some security best practices like SafeMath and reentrancy guards, it exhibits significant centralization risks due to extensive owner privileges. Critical issues include the potential for honeypot scenarios and the risk of permanently locking accidentally sent ETH. The complexity of the tax logic also introduces potential for unintended behavior.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement a timelock for all sensitive owner-controlled functions, or transfer ownership to a multi-signature wallet, to reduce centralization and prevent malicious or accidental actions. A `receive()` or `fallback()` function should be added to prevent ETH from being permanently locked if sent directly to the contract. The tax calculation logic should be simplified and thoroughly documented to enhance clarity and reduce the potential for errors. Additionally, ensure all critical state changes emit appropriate events for transparency and off-chain monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | 7.1 Architecture: The contract follows a standard ERC-20 token architecture with added tax and anti-bot mechanisms. 7.2 Code Security: It utilizes SafeMath for arithmetic operations and a… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token's economic model includes dynamic buy/sell taxes, max transaction limits, and anti-whale measures. These features are highly configurable by the owner. 7.5 Governance: The… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades: The contract is not designed with upgradeability in mind, meaning its logic is immutable once deployed. This eliminates risks associated with proxy patterns or upgrade mechanisms… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Extreme Centralization and Potential Honeypot Vector  *(Severity: Critical · Status: Unresolved)*

The contract owner possesses extensive control over critical parameters and functionalities, including the ability to: set all tax rates (buy, sell, transfer), enable/disable trading, enable/disable automatic liquidity swaps, set max transaction and wallet size limits, and add/remove addresses from the `bots` mapping (effectively blacklisting them). This level of control allows the owner to manipulate trading conditions, potentially creating a honeypot scenario where users can buy but are prevented from selling (e.g., by setting sell tax to 100% or blacklisting specific addresses). This poses a severe risk to user funds and trust in the protocol.

**Recommendation:** Implement a timelock for all sensitive owner-controlled functions (e.g., setting taxes, modifying trading status, updating bot list) to introduce a delay before changes take effect. Consider transferring ownership to a multi-signature wallet to distribute control and require consensus for critical operations. Clearly communicate the extent of owner privileges to users.


### `H-01` — Missing `receive()` or `fallback()` Function - Stuck ETH  *(Severity: High · Status: Unresolved)*

The contract does not implement a `receive()` or `fallback()` payable function. This means that if any Ether is sent directly to the contract address without calling a specific payable function (e.g., `addLiquidityETH`), it will be permanently locked within the contract and become irrecoverable. While the contract is designed to handle ETH through specific functions, accidental direct transfers are a common occurrence.

**Recommendation:** Add a `receive() external payable {}` function to the contract to allow it to accept direct Ether transfers. If direct ETH transfers are not intended, consider adding a `fallback() external payable { revert("ETH not accepted"); }` to explicitly prevent them and inform users.


### `M-01` — Complex and Potentially Ambiguous Tax Logic  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function contains multiple conditional blocks for calculating `taxAmount` based on `_buyCount`, `from`, and `to` addresses. The interaction between the general `if(_buyCount==0)` / `if(_buyCount>0)` blocks and the specific `if (from == uniswapV2Pair)` (buy) / `if(to == uniswapV2Pair)` (sell) blocks is complex and could lead to unintended tax applications or make the logic difficult to reason about. For instance, the `_buyCount==0` and `_buyCount>0` conditions might be overridden by the buy/sell specific conditions, leading to confusion.

**Recommendation:** Refactor the `_transfer` function's tax calculation logic to be clearer and more modular. Use a single, well-defined flow for determining the applicable tax based on the transaction type (buy, sell, general transfer). Add comprehensive inline comments and external documentation to explain the exact tax application rules under different scenarios.


### `L-01` — Lack of Event Emission for Critical State Changes  *(Severity: Low · Status: Unresolved)*

The contract defines events such as `MaxTxAmountUpdated` and `TransferTaxUpdated`, but these events are not emitted when the corresponding state variables (`_maxTxAmount`, `_transferTax`) are modified by the owner. This lack of event emission hinders off-chain monitoring, transparency, and the ability for external applications or users to track critical changes to the token's parameters.

**Recommendation:** Ensure that all functions that modify critical state variables (e.g., `setMaxTxAmount`, `setTransferTax`, `setInitialBuyTax`, `setFinalBuyTax`, etc.) emit appropriate events to signal these changes. This improves transparency and allows for better off-chain tracking and auditing.


### `I-01` — Unused State Variables  *(Severity: Informational · Status: Unresolved)*

The state variables `sellCount` and `lastSellBlock` are declared within the contract but are not utilized anywhere in the provided source code. This suggests either incomplete functionality, vestigial code from a previous iteration, or a potential oversight.

**Recommendation:** Review the purpose of `sellCount` and `lastSellBlock`. If they are intended for future functionality, ensure they are properly implemented. If they are no longer needed, remove them to reduce contract size and improve code clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x29bb...1bcd`](https://etherscan.io/address/0x29bbace690d8f70dd161fcafcc2f028f49131bcd) |
| **Network** | Ethereum |
| **Price** | $0.0001769 |
| **24h Volume** | $116.9K |
| **Liquidity** | $26.3K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 36.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 247 buys / 197 sells |

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

### Is Clawd a scam?

Based on the provided security data, Clawd (CLAWD) exhibits several characteristics that mitigate common scam patterns. The contract is verified, ownership is renounced, and no mint function exists, preventing arbitrary token creation or owner control. Liquidity is locked, mitigating rug pull risks. These factors contribute to its assessed low-risk profile (0/100), indicating a reduced likelihood of a technical scam via contract manipulation. However, due diligence beyond technical aspects is always recommended.

### Is Clawd safe to buy?

While Clawd (CLAWD) presents a low technical risk score (0/100) due to its verified contract, renounced ownership, absence of a mint function, and locked liquidity, no investment is entirely without risk. Key factors to consider include the top 10 holders controlling 36.2% of the supply, which could lead to market volatility if large positions are moved. Furthermore, the relatively low liquidity ($26,326) compared to daily volume ($116,947) suggests potential for price impact on larger trades. Investors should conduct their own research.

### Has Clawd been audited?

The provided data confirms that the Clawd (CLAWD) contract is verified on the Ethereum blockchain. Contract verification means its source code is publicly available and matches the deployed bytecode, allowing anyone to inspect it. However, verification is distinct from a formal security audit by a specialized third-party firm, which involves a deeper, expert review for vulnerabilities, logical flaws, and potential attack vectors.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x37f31c174f5594dc1fa527af7cdf933bb0ac37cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/clawd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-20*
