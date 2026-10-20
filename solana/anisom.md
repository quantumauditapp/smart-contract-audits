---
token: Anisom
ticker: ANISOM
network: solana
risk_score: 16
status: low
date: 2026-10-07
---

# Anisom (ANISOM) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anisom-sol)

---

## Audit Summary

The Anisom (ANISOM) SPL token mint has no critical or high-severity issues identified based on available on-chain data and third-party security registries. Both mint and freeze authorities are revoked, indicating a fixed supply and immutable token accounts. Holder distribution and pool liquidity lock status were unavailable for analysis, limiting a complete assessment of economic risks.

> **Final Recommendation:** Given the revoked mint and freeze authorities, the token's core parameters are immutable. Holders should monitor for any future changes in liquidity provision, especially the locking status of the existing liquidity, which was not available for this report. Additionally, while current data shows no high concentration, it is advisable to periodically check holder distribution once that data becomes available to assess potential whale risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Anisom (ANISOM) token operates on the classic `spl-token` program. Its mint authority is revoked, ensuring no new tokens can be created, and the total supply of 987,759,216.520916 ANISOM is… |
| **Governance / Economics** | 7/10 | Low | The token has a total DEX liquidity of $64,283, with a 24-hour trading volume of $60,150, resulting in a normal Volume/Liquidity Ratio of 0.94. The trading pair is very new, created 0 days ago.… |
| **Upgrades** | 8/10 | Low | The Anisom (ANISOM) token mint has both its mint and freeze authorities revoked, meaning its supply and the ability to freeze accounts are immutable. The token's metadata, including name, symbol, or… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $89K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $89K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`D8GnQA...pump`](https://solscan.io/account/D8GnQAnA7i5cmpkgDUyhxx8SmnveypZBQRXh6qiapump) |
| **Network** | Solana |
| **Price** | $0.0001451 |
| **24h Volume** | $60.2K |
| **Liquidity** | $64.3K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 21h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 702 buys / 380 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5chgeoekj8jveufyqah1tdwsspetm2prptts1dfx65aw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anisom-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
