---
token: Moby AI
ticker: MOBY
network: solana
risk_score: 0
status: low
date: 2026-10-13
---

# Moby AI (MOBY) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moby-ai-sol)

---

## Audit Summary

The Moby AI (MOBY) SPL token mint has been audited based on on-chain data and third-party security registries. No critical or high-severity vulnerabilities were identified. The mint and freeze authorities are revoked, and metadata is immutable. Holder concentration is low, and liquidity is substantial with a normal volume-to-liquidity ratio. Third-party risk registry data reported no adverse flags.

> **Final Recommendation:** Given the revoked mint and freeze authorities, and immutable metadata, the token's core parameters are fixed. Holders should continue to monitor DEX liquidity and trading volume for any significant changes that could impact market depth. While the LP tokens are burned, general market conditions and project developments should be considered for long-term holding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Moby AI (MOBY) token operates on the classic `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing accounts can… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a healthy distribution, with the top 10 holders that can sell holding only 17.07% of the total supply, indicating low concentration risk. The DEX liquidity stands at $445,076… |
| **Upgrades** | 8/10 | Low | The Moby AI (MOBY) token mint has a robust security posture regarding mutability. Both the mint and freeze authorities are permanently revoked, preventing any future changes to the token supply or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.5% of supply. Of that, 9.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.1% in wallets, 0.0% in other contracts. 21,891 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Moby AI (MOBY), market cap $2M, rank #2193. 21,891 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $451K (DexScreener, all pools). 24h trading volume $11.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.1M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.192 on 2025-01-22; the price is now 98.6971% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: AI Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $451K of DEX liquidity across 15 pools. Launch: launched on pump.fun, 637 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Cy1GS2...pump`](https://solscan.io/account/Cy1GS2FqefgaMbi45UunrUzin1rfEmTUYnomddzBpump) |
| **Network** | Solana |
| **Price** | $0.002384 |
| **24h Volume** | $1.11M |
| **Liquidity** | $426.6K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 26.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7588 buys / 7411 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/aemyrzmjryzaq9z4rlfublnpruy5ecooc94ejvemfti4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moby-ai-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
