---
token: Goatseus Maximus
ticker: GOAT
network: solana
risk_score: 17
status: low
date: 2026-10-16
---

# Goatseus Maximus (GOAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/goatseus-maximus-sol)

---

## Audit Summary

The Goatseus Maximus (GOAT) SPL token mint demonstrates a robust security posture with both mint and freeze authorities revoked, preventing further token creation or account freezing. The token has substantial DEX liquidity of over $1.5M USD, with 99.73% of its liquidity pool tokens burned. No critical or high-risk flags were identified by third-party registries, and no deterministic vulnerabilities were found based on the provided on-chain facts.

> **Final Recommendation:** Holders should regularly monitor the token's holder distribution for any significant shifts in concentration that could impact market stability. While the liquidity is largely secured by burned LP tokens, continuous monitoring of the remaining unlocked liquidity and trading volume is advisable. Verify on-chain that the mint and freeze authorities remain revoked to ensure the fixed supply and unfreezable nature of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL Token Program v3 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no existing accounts can be frozen. The token does… |
| **Governance / Economics** | 6/10 | Medium | The token exhibits moderate holder concentration, with the top 10 holders that can sell controlling 43.18% of the supply. DEX liquidity is robust at $1,535,860 USD, and the 24-hour volume of… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing any further changes to the token's supply or account freezing capabilities. The token's metadata is immutable ('metadata_mutable… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.7% (≈ permanent lock) |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.1% of supply. Of that, 4.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 40.5% in wallets, 2.7% in other contracts. 76,670 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Goatseus Maximus (GOAT), market cap $15M, rank #977. 76,670 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.7% of the pool's LP is burned or time-locked. 99.7% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $13.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.8M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.35 on 2024-11-17; the price is now 98.8586% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: AI Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 29 pools. Launch: launched on pump.fun, 735 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CzLSuj...pump`](https://solscan.io/account/CzLSujWBLFsSjncfkh59rUFqvafWcY5tzedWJSuypump) |
| **Network** | Solana |
| **Price** | $0.01548 |
| **24h Volume** | $2.73M |
| **Liquidity** | $1.54M |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 2y |
| **Top-10 Holders** | 48.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6682 buys / 7486 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9tb2ohu5p16bpbarqd3n27wnkf51ukfs8z1gzzldxvzw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/goatseus-maximus-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
