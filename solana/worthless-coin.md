---
token: Worthless Coin
ticker: WORTHLESS
network: solana
risk_score: 22
status: low
date: 2026-10-19
---

# Worthless Coin (WORTHLESS) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/worthless-coin-sol)

---

## Audit Summary

The token operates on the spl-token-2022 program with both mint and freeze authorities permanently revoked, and 100.0% of DEX pool liquidity burned. However, DEX activity shows a critical wash trading anomaly with a 24-hour volume of $1,427,221 against only $50,822 in liquidity (volume-to-liquidity ratio of 28.08). Note that chain-native RPC holder distribution data was unavailable during this evaluation.

> **Final Recommendation:** Query getProgramAccounts or an indexer directly to confirm that no unindexed private wallets hold dominating portions of the non-pool circulating supply. Monitor real-time transaction graphs on DEX pools to verify whether the $1.42M daily volume stems from automated circular churn across linked wallets before committing capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint is initialized under the spl-token-2022 standard with 6 decimals and a fixed supply of 960,481,006,284,992 raw base units. Core access control is secured as both the mint authority and… |
| **Governance / Economics** | 7/10 | Low | Total DEX liquidity is established at $50,822, with 100.0% of LP tokens permanently burned so liquidity cannot be removed. However, trading activity exhibits extreme inorganic turnover with a 24h… |
| **Upgrades** | 10/10 | Low | The token features no upgradable components or administrative backdoors. Both mint and freeze authorities are irrevocably revoked, preventing arbitrary token minting or account freezing. Metadata… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 28.08x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Inspect trading logs for circular bot transactions designed to manufacture false liquidity and volume metrics before trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $45K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $45K of DEX liquidity across 14 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`87sEXK...pump`](https://solscan.io/account/87sEXKPMBeoryaqFQQnq1Yq6mUvjeNzhiFGxJbRjpump) |
| **Network** | Solana |
| **Price** | $0.0002442 |
| **24h Volume** | $1.40M |
| **Liquidity** | $44.0K |
| **Volume / Liquidity** | 31.9× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13299 buys / 7989 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hnjy1mvocfbpnxwtanscceqnr5t2ackyfyuskwjhee3j)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/worthless-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
