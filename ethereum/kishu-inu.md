---
token: Kishu Inu
ticker: KISHU
network: ethereum
risk_score: 43
status: medium
date: 2026-10-11
---

# Kishu Inu (KISHU) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kishu-inu-eth)

---

## Audit Summary

The KishuInu contract is an ERC-20 compatible token with custom transfer mechanisms and significant owner-controlled features. The audit identified a high-severity centralization risk where the owner can directly manipulate user balances, alongside other low-severity issues related to owner control over transfer limits and a minor rounding error. The contract is not upgradeable, ensuring immutability but preventing on-chain fixes.

> **Final Recommendation:** To enhance the security and decentralization of the KishuInu token, it is strongly recommended to review and potentially reduce the extensive privileges held by the contract owner. Consider implementing multi-signature requirements or time-locks for critical functions that directly affect user balances or core tokenomics. Transparent communication with token holders regarding the current level of owner control is also crucial.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The KishuInu contract implements standard ERC-20 functionality, including `transfer` and `transferFrom` functions, which are well-defined (7.2 Code Security). It incorporates custom logic for… |
| **Governance / Economics** | 5/10 | Medium | The contract exhibits significant centralization, with the owner retaining extensive control over critical token mechanics (7.3 Access Control). The owner can directly manipulate token holders'… |
| **Upgrades** | 7/10 | Low | The KishuInu contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, providing certainty regarding its long-term behavior and eliminating… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 89.8% |
| **LP Locked** | 89.8% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 3 Informational_

### `CP-02` — Owner Can Manipulate Token Holders' Balances  *(Severity: High · Status: Unresolved)*

The contract owner has the ability to directly change the token balances of any holder. This means the owner can move tokens out of a user's wallet or effectively burn them without the user's consent, by calling functions like `excludeAccount(address)` and `includeAccount(address)`. This poses a significant risk to token holder funds.

**Recommendation:** Token holders should be aware that the contract owner possesses the power to modify their token balances. To mitigate this, the project should consider renouncing ownership or transferring it to a secure, multi-signature wallet with a high threshold, and ideally, remove the ability to directly manipulate balances.


### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

89.8% of the pool's LP is burned or time-locked. 89.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 9.8% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $785K (DexScreener, all pools). 24h trading volume $112K (CoinGecko, all markets, daily snapshot). 24h trading volume $43K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.75e-08 on 2021-05-14; the price is now 99.6022% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CD-01` — Potential Rounding Loss in Calculations  *(Severity: Low · Status: Unresolved)*

A calculation within the `_getTValues` function performs division before multiplication. In Solidity, integer division truncates any decimal part, which can lead to a small loss of precision or 'rounding loss' if the numbers are not perfectly divisible. While often minor, this could accumulate over many transactions or affect very small amounts.

**Recommendation:** While this issue is generally minor, it's best practice to perform multiplication before division to maintain precision in Solidity. The project should review the `_getTValues` function and reorder operations to `(amount.mul(numerator)).div(denominator)` where possible.


### `CP-08` — Owner Can Change Transfer Limits  *(Severity: Low · Status: Unresolved)*

The contract owner can modify rules that govern how many tokens can be transferred in a single transaction. The `setMaxTxPercent` function allows the owner to set a maximum percentage of the total supply that can be transferred, which could impact the liquidity and tradability of the token.

**Recommendation:** Token holders should be aware that the owner can change transaction limits. To reduce this centralized control, the project could consider implementing a time-lock for changes to these parameters or transferring ownership to a community-controlled governance mechanism.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.1% of supply. Of that, 3.5% burned, 5.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.1% in wallets, 1.6% in other contracts. 281,829 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Kishu Inu (KISHU), market cap $7M, rank #1498. 281,829 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: 2% on buy, 1.76% on sell. Market: $785K of DEX liquidity across 8 pools. Launch: 2002 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa2b4...817d`](https://etherscan.io/address/0xa2b4c0af19cc16a6cfacce81f192b024d625817d) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $43.2K |
| **Liquidity** | $783.7K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 29.1% of supply |
| **Buy / Sell Tax** | 2.0% / 1.8% |
| **24h Transactions** | 98 buys / 91 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf82d8ec196fb0d56c6b82a8b1870f09502a49f88)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kishu-inu-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
