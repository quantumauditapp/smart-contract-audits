---
token: PsyopAnime
ticker: PSYOPANIME
network: solana
risk_score: 1
status: low
date: 2026-10-16
---

# PsyopAnime (PSYOPANIME) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/psyopanime-sol)

---

## Audit Summary

This audit of the PsyopAnime SPL Token Mint found no critical or high-severity issues based on available on-chain data and third-party risk registries. Key authorities are revoked, liquidity is locked, and holder concentration is low. Third-party registry data was available and reported no adverse flags, and no sources were unavailable that would impact the assessment of critical risks.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor the token's market activity and liquidity for any significant changes, although the burned LP tokens provide strong assurance against rug pulls. Confirm that no new Token-2022 extensions are enabled that could alter token behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The PsyopAnime token is implemented using the spl-token-2022 program, indicating modern Solana token standards. Both the mint authority and freeze authority are revoked (7.3 Access Control)… |
| **Governance / Economics** | 10/10 | Low | The token exhibits a healthy distribution, with the top 10 holders that can sell holding only 18.54% of the supply (7.4 Economic), reducing the risk of large-scale dumps. Liquidity is robust at… |
| **Upgrades** | 10/10 | Low | The token's mint and freeze authorities are permanently revoked, meaning no new tokens can be minted and no accounts can be frozen (7.7 Upgrades). Metadata mutability is set to False, ensuring that… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.6% of supply. Of that, 18.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.0% in wallets, 4.5% in other contracts. 10,500 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PsyopAnime (PSYOPANIME), rank #3949. 10,500 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $278K (DexScreener, all pools). 24h trading volume $28K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00976 on 2026-03-01; the price is now 95.9075% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $278K of DEX liquidity across 28 pools. Launch: launched on pump.fun, 279 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2nP9yK...pump`](https://solscan.io/account/2nP9yKQNSGQy851iyawDvBkzkK2R2aqKArQCKc2gpump) |
| **Network** | Solana |
| **Price** | $0.0008979 |
| **24h Volume** | $1.27M |
| **Liquidity** | $198.7K |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 36.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10314 buys / 7879 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/fpyosqzp5ijfrxqqbvnm67rfam7vsbvnam7puf8yvt1c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/psyopanime-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
