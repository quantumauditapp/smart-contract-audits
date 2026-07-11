---
token: Clawd
ticker: CLAWD
network: ethereum
risk_score: 57
status: high
date: 2026-06-20
---

# Clawd (CLAWD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clawd-eth)

---

## Audit Summary

The Clawd token contract implements standard ERC-20 functionality with custom tax mechanisms, transaction limits, and anti-bot features. A critical issue identified is the truncation of the `_transfer` function in the provided source code, which prevents a complete and accurate security assessment of the token's core logic. Furthermore, the contract exhibits extreme centralization, granting the owner extensive control over critical parameters, posing significant honeypot and manipulation risks. The economic model includes high initial transaction taxes and dynamic tax adjustments, which add complexity and potential for unexpected behavior.

> **Final Recommendation:** The audit reveals critical concerns primarily due to the provided `_transfer` function being truncated, rendering a full security assessment impossible. Beyond this, the contract design exhibits extreme centralization, granting the owner extensive control over tokenomics and user access, which poses significant honeypot and manipulation risks. A complete and verifiable source code is essential for any meaningful audit. We recommend a comprehensive re-evaluation with the full source code and a redesign of the access control and economic parameters to reduce centralization. For projects prioritizing security and long-term viability, a Premium Deploy option offers continuous monitoring and expert support to mitigate evolving threats.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract implements an ERC-20 token with custom tax mechanisms, max transaction/wallet limits, and anti-bot features. It utilizes `SafeMath` (redundant in Solidity 0.8.23) and integrates with… |
| **Governance / Economics** | 4/10 | Medium | The contract exhibits extreme centralization, with the `owner` possessing extensive control over critical parameters such as tax rates, transaction limits, and the ability to block users (7.3 Access… |
| **Upgrades** | 8/10 | Low | The contract is not designed with an upgradeability pattern, meaning its logic is immutable post-deployment. While this eliminates risks associated with proxy implementations or upgrade mechanisms… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incomplete `_transfer` Function Logic  *(Severity: Critical · Status: Unresolved)*

The provided `_transfer` function is truncated, specifically ending mid-calculation for `taxAmount` in the sell-side block. This prevents a complete analysis of the token's core transfer and tax mechanisms, making it impossible to verify correct functionality, especially for sell taxes, and introduces a high risk of contract malfunction or unexpected behavior. Without the full implementation, the contract's fundamental operations cannot be guaranteed secure or correct.

**Recommendation:** Provide the complete and untruncated source code for the `_transfer` function to allow for a thorough security audit. Ensure all branches of the transfer logic, including buy, sell, and peer-to-peer transfers, are fully implemented and correctly handle tax calculations and other tokenomics.


### `C-02` — Extreme Owner Centralization & Honeypot Potential  *(Severity: Critical · Status: Unresolved)*

The `owner` has extensive control over critical contract parameters, including the ability to set buy/sell taxes (potentially to 100%), modify max transaction/wallet sizes, enable/disable trading, and arbitrarily block users via the `bots` mapping. This centralization (7.3 Access Control) creates a significant risk of rug pull, honeypot, or malicious manipulation, as the owner can unilaterally alter the contract's economic rules or prevent users from selling their tokens (7.4 Economic).

**Recommendation:** Implement a multi-signature wallet for critical administrative functions or introduce a time-locked mechanism for sensitive parameter changes. Consider decentralizing control through a governance module or by transferring ownership to a community-controlled DAO. Clearly document the owner's capabilities and their impact on token holders.


### `H-01` — Arbitrary User Blocking via `bots` Mapping  *(Severity: High · Status: Unresolved)*

The `addBot` and `delBot` functions allow the owner to arbitrarily prevent any address from participating in transfers. This mechanism, while potentially intended for bot prevention, can be abused to blacklist legitimate users, censor transactions, or prevent specific holders from selling their tokens, leading to a denial of service for affected users (7.3 Access Control, 7.4 Economic).

**Recommendation:** Re-evaluate the necessity of an arbitrary user blocking mechanism. If deemed essential, implement a more transparent and auditable process for adding/removing addresses, potentially involving a multi-sig approval or a community governance vote. Clearly define the criteria for an address to be considered a 'bot' and ensure these criteria are publicly verifiable.


### `H-02` — Complex and Dynamic Tax System  *(Severity: High · Status: Unresolved)*

The contract implements a multi-layered and dynamic tax system with `_initialBuyTax`, `_finalBuyTax`, `_transferTax`, and reduction mechanisms based on `_buyCount`. The interaction between these variables and their application in different transfer scenarios (buy from LP, sell to LP, peer-to-peer transfer) is complex and prone to misinterpretation or unexpected behavior, potentially leading to incorrect tax calculations or user confusion (7.4 Economic, 7.2 Code Security).

**Recommendation:** Simplify the tax structure to improve clarity and predictability. Provide comprehensive documentation and flowcharts explaining how taxes are calculated and applied in all scenarios. Conduct extensive testing to ensure the tax logic behaves as intended under various conditions. Consider using a fixed tax rate or a more straightforward dynamic model.


### `M-01` — High Initial Transaction Taxes  *(Severity: Medium · Status: Unresolved)*

The initial buy and sell taxes are set at 18%. Such high transaction fees can significantly deter legitimate trading activity, reduce liquidity, and make the token unattractive for long-term holding or use, impacting the token's overall economic viability (7.4 Economic).

**Recommendation:** Reconsider the initial tax rates. High taxes often discourage participation and can lead to a 'dead' token. Evaluate the impact of high taxes on trading volume and liquidity provision. Consider starting with lower taxes and gradually adjusting them based on community feedback or a well-defined economic model.


### `L-01` — Redundant `SafeMath` Library  *(Severity: Low · Status: Unresolved)*

The contract uses the `SafeMath` library for arithmetic operations. While `SafeMath` is beneficial for older Solidity versions, Solidity 0.8.x and later include native overflow and underflow checks, rendering the explicit use of `SafeMath` redundant. This adds unnecessary code complexity without providing additional security benefits in this compiler version (7.2 Code Security).

**Recommendation:** Remove the `SafeMath` library and its `using` directive. Rely on Solidity's native overflow/underflow protection for arithmetic operations, which simplifies the codebase and reduces gas costs slightly.


### `I-01` — Lack of Upgradeability  *(Severity: Informational · Status: Unresolved)*

The contract is not designed with an upgradeability pattern (e.g., proxy). This means that once deployed, its logic cannot be modified or updated. Any discovered vulnerabilities, bugs, or desired feature enhancements would necessitate a complete redeployment of the contract, losing its history and requiring users to migrate (7.7 Upgrades).

**Recommendation:** Consider implementing an upgradeable proxy pattern (e.g., UUPS or Transparent) if future modifications or bug fixes are anticipated. This allows for contract logic updates without changing the contract address, preserving user balances and history. However, upgradeability also introduces its own set of risks that must be carefully managed.

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
