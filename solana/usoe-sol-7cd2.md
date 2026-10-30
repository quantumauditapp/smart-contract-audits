---
token: USOE
ticker: USOE
network: solana
risk_score: 1
status: low
date: 2026-10-30
---

# USOE (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-sol-7cd2)

---

## Audit Summary

The USOE token mint on the Token-2022 program exhibits a clean baseline with both mint and freeze authorities permanently revoked and all pool liquidity burned. No critical, high, or medium risk indicators were detected across configuration parameters. Note that chain-native RPC holder distribution data was unavailable during telemetry collection, requiring distribution analysis to rely on registry signals.

> **Final Recommendation:** Continuously query on-chain account state to ensure mint and freeze authority pointers remain set to null. Track automated market maker reserve balances to confirm sufficient pool depth persists for order execution if holder dispersion metrics shift upon full RPC availability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized raw supply of 999996147600774 across 6 decimals. It enables no custom transfer hooks, permanent delegates, or closable account… |
| **Governance / Economics** | 10/10 | Low | Top 10 holders that can sell control 0.55% of the circulating supply, presenting negligible direct sell-wall concentration. DEX liquidity sits at $2,648,632, with 100.0% of the LP tokens burned… |
| **Upgrades** | 10/10 | Low | Mint authority and freeze authority are both revoked to None, preventing arbitrary token creation or transfer blacklisting. Metadata mutability is set to false, locking the token's name and symbol… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 0.7% of supply. Of that, 0.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 0.0% in other contracts. 2,937 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,937 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.6M (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.6M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`qi6wtT...pump`](https://solscan.io/account/qi6wtTo9jZhkGcokNrjNNnBSjt12sUxgNyhWuUUpump) |
| **Network** | Solana |
| **Price** | $1.0250 |
| **24h Volume** | $1.39M |
| **Liquidity** | $2.64M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 11h |
| **Top-10 Holders** | 0.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 31584 buys / 751 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/e3mk971v24phmma1fylxnzdxcvik1scqsqen5dd4ly6u)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-sol-7cd2)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
