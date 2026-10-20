---
token: French Goku Hero
ticker: PIERRE
network: solana
risk_score: 17
status: low
date: 2026-10-19
---

# French Goku Hero (PIERRE) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/french-goku-hero-sol)

---

## Audit Summary

The primary risk identified is a high 24-hour volume-to-liquidity ratio of 52.57, which reflects trading activity strongly associated with artificial wash volume. Administrative mint and freeze authorities are permanently revoked, and pool liquidity is fully burned. Note that chain-native RPC holder distribution data was unavailable during this evaluation.

> **Final Recommendation:** Inspect decentralized exchange transaction signatures on a block explorer to determine whether swap flow originates from genuine distinct participants or automated looping routines. Regularly monitor liquidity levels and holder account balances as secondary on-chain holder distribution RPC endpoints become accessible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized raw supply of 949,423,592,396,650 across 6 decimals. Both mint authority and freeze authority are revoked (None), disallowing… |
| **Governance / Economics** | 8/10 | Low | Top 10 sell-capable holders account for 16.13% of supply, while DEX pool reserves hold 9.00%. Total DEX liquidity is $65,337, with 100.0% of LP tokens permanently burned to eliminate liquidity… |
| **Upgrades** | 10/10 | Low | Administrative control is nullified because both mint and freeze keys have been permanently revoked. No configurable transfer hook or transfer fee upgrade vectors exist on the mint account. Token… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 52.57x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Scrutinize trading volume distribution on-chain to assess genuine market interest before executing trades.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.1% of supply. Of that, 9.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.1% in wallets, 0.0% in other contracts. 4,636 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,636 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 51% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $128K (DexScreener, all pools). 24h trading volume $5.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $128K of DEX liquidity across 26 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`D3S6J9...pump`](https://solscan.io/account/D3S6J9s1byrNBt3ZKwEDiPsNRqHtoEP8zQKdhyBdpump) |
| **Network** | Solana |
| **Price** | $0.0004241 |
| **24h Volume** | $3.47M |
| **Liquidity** | $65.1K |
| **Volume / Liquidity** | 53.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 25.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19288 buys / 17424 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hrmcdd9xawgtxh6qkbzs1mtiwyjtfg4bdmrl5dcjwxnb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/french-goku-hero-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
