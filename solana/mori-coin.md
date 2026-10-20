---
token: MORI COIN
ticker: MORI
network: solana
risk_score: 0
status: low
date: 2026-10-01
---

# MORI COIN (MORI) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mori-coin-sol)

---

## Audit Summary

The MORI COIN SPL token mint demonstrates a robust security posture regarding its core mint and freeze authorities, which are permanently revoked. However, a minor portion (0.4%) of the DEX pool's liquidity remains unlocked and is held by an address other than the pool creator, presenting a potential, albeit small, withdrawal risk. Third-party risk registry data reported no adverse flags, and key security-relevant flags like `balance_mutable` and `metadata_mutable` are false, indicating a standard and immutable token configuration. Chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** Holders should monitor the address(es) that control the 0.4% of unlocked liquidity to observe any potential withdrawal actions. While the majority of the liquidity is secured, vigilance regarding this smaller, unlocked portion is prudent. No further on-chain verification steps are required for the core token mint, given its immutable authorities and configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard `spl-token` program (v3). Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder accounts can be frozen.… |
| **Governance / Economics** | 8/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 17.25% of the supply. The token has a liquidity of $370,551 USD, with 99.6% of the pool's liquidity locked for good in… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are revoked, preventing any future changes to the token's supply or the ability to freeze accounts. The token is based on the `spl-token` program (v3) and does not… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Raydium Lock |
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

Only 99.6% of the pool's liquidity is burned or locked; the remaining 0.4% is held, unlocked, by 1 address(es) other than the pool's creator. This portion of liquidity can be withdrawn at any moment by its holder(s).

**Recommendation:** Monitor the address(es) holding the unlocked liquidity for potential withdrawal.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.6% of supply. Of that, 10.0% locked, 5.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.1% in wallets, 4.1% in other contracts. 21,012 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as MORI COIN (MORI), market cap $3M, rank #2206. 21,012 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.6% of the pool's LP is burned or time-locked. 99.6% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. 0.4% is held, unlocked, by 1 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $380K (DexScreener, all pools). 24h trading volume $5.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $727K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.2 on 2025-07-06; the price is now 98.7075% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $380K of DEX liquidity across 9 pools. Launch: 462 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8ZHE4o...Df5e`](https://solscan.io/account/8ZHE4ow1a2jjxuoMfyExuNamQNALv5ekZhsBn5nMDf5e) |
| **Network** | Solana |
| **Price** | $0.003568 |
| **24h Volume** | $721.4K |
| **Liquidity** | $373.0K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 32.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2322 buys / 1969 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9nxanmd7k78a9rmd2l3w8kqt5u9i7gsvv5ahiz78scc2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mori-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
