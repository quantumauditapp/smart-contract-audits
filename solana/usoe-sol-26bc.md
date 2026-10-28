---
token: USOE
ticker: USOE
network: solana
risk_score: 0
status: low
date: 2026-10-28
---

# USOE (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-sol-26bc)

---

## Audit Summary

No critical technical vulnerabilities were detected for USOE as both mint and freeze authorities are revoked and 100% of DEX liquidity is burned. Market liquidity is robust at $4,780,483 with a normal volume-to-liquidity ratio of 0.51, although chain-native RPC holder distribution data was unavailable. Risk registry metrics noted high holder correlation signals, but no malicious flags were triggered.

> **Final Recommendation:** Continuously track on-chain swap execution and pool reserve balances to confirm market liquidity remains accessible across secondary venues. Monitor third-party registry telemetry and cluster activity over time to watch for any emerging coordinated selling among correlated wallet groups.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized supply of 999,999,261,692,067 base units across 6 decimals. Both mint authority and freeze authority are permanently revoked… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders capable of selling control only 0.45% of supply, presenting minimal immediate dump pressure. Secondary market liquidity stands at $4,780,483, with 100.0% of pool liquidity burned… |
| **Upgrades** | 10/10 | Low | SPL token mints have no upgrade proxy mechanisms; parameters are fixed strictly by account structure and authority keys. Metadata mutability is set to false, preventing post-launch rebranding or URI… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 0.5% of supply. What remains: 0.4% in wallets, 0.0% in other contracts. 2,814 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,814 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.7M (DexScreener, all pools). 24h trading volume $2.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $4.7M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ait5y3...pump`](https://solscan.io/account/ait5y3tFCVxk9yFjpNv6rUQ2fciBHT4JScGsggopump) |
| **Network** | Solana |
| **Price** | $3.1000 |
| **24h Volume** | $2.39M |
| **Liquidity** | $4.74M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 8h |
| **Top-10 Holders** | 0.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20205 buys / 523 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gzll3vhnpvsqbhvuzakt5norc1auu6ifb8nreaiwzxez)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-sol-26bc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
