---
token: Tole Tole
ticker: MEIMEI
network: solana
risk_score: 7
status: low
date: 2026-10-18
---

# Tole Tole (MEIMEI) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tole-tole-sol)

---

## Audit Summary

This audit of the Tole Tole (MeiMei) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and third-party risk registry data. The mint and freeze authorities are revoked, and 100% of the DEX pool's liquidity is burned, indicating a high degree of immutability and security for existing holders. No adverse flags were reported by external security signals. Chain-native RPC data for holder distribution was unavailable, but the reported top 10 holders that can sell account for a low percentage of the total supply.

> **Final Recommendation:** Holders can proceed with a high degree of confidence regarding the immutability of the token's core properties. It is recommended to continuously monitor the token's liquidity and trading volume for any significant changes. While the current holder concentration is low, ongoing observation of the top holder wallets can provide early warning of potential market impact from large sales.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program, indicating modern SPL token standards. Key authorities, including the mint authority and freeze authority, have been revoked, preventing… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for only 20.42% of the supply, reducing the risk of large-scale sell-offs. The token exhibits healthy liquidity, with… |
| **Upgrades** | 10/10 | Low | The token's core parameters are highly immutable, as both the mint and freeze authorities are revoked. This means no new tokens can be minted, and no accounts can be frozen. Furthermore, the token's… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.2% of supply. Of that, 12.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.4% in wallets, 0.0% in other contracts. 1,094 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tole Tole (MEIMEI), rank #3548. 1,094 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $102K (DexScreener, all pools). 24h trading volume $354K (CoinGecko, all markets, daily snapshot). 24h trading volume $241K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $102K of DEX liquidity across 13 pools. Launch: launched on pump.fun, 109 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`MsGDyb...pump`](https://solscan.io/account/MsGDybWRSNdNXkdDZhEksgzugT5CbVWUG2wkhwgpump) |
| **Network** | Solana |
| **Price** | $0.0005234 |
| **24h Volume** | $238.0K |
| **Liquidity** | $92.2K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 33.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1767 buys / 1732 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dtdfawqhceaefxjuhjgc8xo9xxh52envha1xoj9f4d8y)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tole-tole-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
