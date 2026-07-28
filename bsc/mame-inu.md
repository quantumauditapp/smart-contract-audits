---
token: Mame Inu
ticker: MAME
network: bsc
risk_score: 30
status: medium
date: 2026-07-26
---

# Mame Inu (MAME) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 30/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mame-inu-bsc)

---

## Audit Summary

The MAMEINU token contract implements an ERC-20 standard with reflection mechanics, dynamic transaction fees, and an automated swap-and-distribute mechanism for collected fees. While the contract utilizes modern Solidity features and includes reentrancy protection, a critical vulnerability was identified regarding the lack of slippage protection in its token swap function. Additionally, the contract exhibits high centralization of control under the owner, and its dynamic fee structure includes extremely high initial taxes, posing significant economic and governance risks.

> **Final Recommendation:** It is critical to address the lack of slippage protection in the token swap function to prevent significant value loss during fee processing. Implementing a minimum output amount for swaps is essential. Furthermore, consider decentralizing control over critical contract parameters by adopting multi-signature wallets or time-lock mechanisms for sensitive operations to mitigate the risks associated with a single point of failure. Clearly communicate the dynamic fee structure to users to manage expectations and avoid confusion.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good practices such as using Solidity 0.8.25 for checked arithmetic and implementing a reentrancy guard (`_inSwap`) for critical swap operations. The ERC-20 standard… |
| **Governance / Economics** | 6/10 | Medium | The MAMEINU token incorporates a dynamic fee structure with extremely high initial transaction taxes (up to 90%), designed to deter bots but potentially impacting legitimate users. The contract's… |
| **Upgrades** | 9/10 | Low | The MAMEINU contract is not designed with an upgrade mechanism, meaning its logic is immutable once deployed. This eliminates upgrade-related risks such as proxy implementation vulnerabilities or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Lack of Slippage Protection in Token Swaps  *(Severity: Critical · Status: Unresolved)*

The `_swapTokensForEth` function, responsible for converting collected fees into BNB, calls `router.swapExactTokensForETHSupportingFeeOnTransferTokens` without specifying an `amountOutMin` parameter. This omission means the swap can execute with arbitrary slippage, potentially resulting in a significant loss of value for the marketing and team wallets, especially during periods of high volatility or low liquidity. An attacker could front-run these transactions to cause extreme slippage and drain value.

**Recommendation:** Implement a minimum output amount (`amountOutMin`) for `swapExactTokensForETHSupportingFeeOnTransferTokens` to protect against excessive slippage and front-running attacks. This value should be carefully calculated based on current market conditions or a reasonable tolerance, potentially configurable by the owner.


### `H-01` — High Centralization of Owner Privileges  *(Severity: High · Status: Unresolved)*

The contract grants extensive control to the `owner` address, including the ability to set marketing and team wallets, change swap thresholds, enable/disable swaps, exclude/include addresses from fees and rewards, open trading, and rescue any foreign ERC20 tokens or stuck BNB. This high degree of centralization introduces a single point of failure and relies heavily on the owner's integrity and security. A compromised owner key could lead to significant fund loss or manipulation of the token's economic parameters (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for critical owner functions or introducing a time-lock mechanism for sensitive parameter changes to reduce the risk associated with a single point of control and enhance governance transparency.


### `H-02` — Dynamic and High Initial Transaction Taxes  *(Severity: High · Status: Unresolved)*

The token implements a dynamic fee structure where transaction taxes are extremely high during the initial phase (`PHASE1_START_BPS` is 90% for the first 300 seconds). While this might be intended as an anti-bot measure, such high taxes can severely deter legitimate trading, create significant price impact, and lead to user confusion or unexpected losses for early buyers who are unaware of the rapidly decreasing tax (7.4 Economic).

**Recommendation:** Clearly communicate the dynamic fee structure and its implications to users through official documentation and interfaces. Evaluate if such an extreme initial tax is truly necessary, as it can negatively impact legitimate trading and user perception. Ensure the fee calculation logic is robust and thoroughly tested.


### `M-01` — Potential for Manipulation of Excluded Addresses  *(Severity: Medium · Status: Unresolved)*

The `owner` can exclude any address from fees (`_isExcludedFromFee`) and rewards (`_isExcludedFromReward`). While there's a `MAX_EXCLUDED` limit of 30 for the reward exclusion list, the fee exclusion list has no such explicit limit on its size. This power, if misused, could allow the owner to grant preferential treatment to certain addresses or manipulate the fee collection mechanism, potentially impacting the token's economics or creating an unfair advantage (7.3 Access Control, 7.4 Economic).

**Recommendation:** Review the necessity of excluding addresses from fees without a clear limit. If exclusions are critical, consider implementing a more transparent and auditable process for managing these lists, or further restricting the owner's ability to arbitrarily add/remove addresses.


### `L-01` — Unused `_tFeeTotal` Variable  *(Severity: Low · Status: Unresolved)*

The `_tFeeTotal` variable is incremented in the `_reflectFee` function, but its value is only exposed via the `totalFees()` view function and does not appear to be used in any core logic that affects token supply, reflection calculations, or fee distribution. This variable consumes storage without a clear functional purpose within the token's mechanics (7.2 Code Security).

**Recommendation:** Either remove the `_tFeeTotal` variable if it serves no functional purpose, or clarify its intended use and integrate it into the contract's logic if it is meant to play a role in the tokenomics.


### `I-01` — Hardcoded Router and Factory Addresses  *(Severity: Informational · Status: Unresolved)*

The contract hardcodes the addresses for the PancakeSwap V2 Router (`ROUTER`) and Factory (`FACTORY`). While these are standard addresses on BSC, hardcoding them means the contract cannot adapt to potential future changes in the DEX infrastructure (e.g., if PancakeSwap upgrades its router to a new address or if the project decides to migrate to a different DEX) (7.6 External).

**Recommendation:** For future flexibility, consider making the router and factory addresses configurable by the owner (e.g., via an `onlyOwner` function) during deployment or post-deployment, while ensuring proper validation of new addresses.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe92f...2302`](https://bscscan.com/address/0xe92f7fe3eaf61df28b7b75f3faab199333c42302) |
| **Network** | BNB Chain |
| **Price** | $0.005159 |
| **24h Volume** | $113.7K |
| **Liquidity** | $712.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 48.0% of supply |
| **Buy / Sell Tax** | 0.1% / 0.1% |
| **24h Transactions** | 1194 buys / 372 sells |

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

### Is Mame Inu a scam?

Based on automated analysis, Mame Inu scores 67/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Mame Inu safe to buy?

Our scanner flagged a risk score of 67/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Mame Inu been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x924f1a4422a89900faafa3f886721fdccd6e086a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mame-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
