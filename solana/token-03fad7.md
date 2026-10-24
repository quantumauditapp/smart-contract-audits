---
token: ███
ticker: ███
network: solana
risk_score: 20
status: low
date: 2026-10-24
---

# ███ (███) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-03fad7-sol)

---

## Audit Summary

The mint EWX2...pump operates under Token-2022 with all privileged authorities permanently revoked and pool liquidity 100% burned. The principal observed concern is an extreme volume-to-liquidity ratio of 57.69x ($1,152,892 24-hour volume against $19,984 liquidity), indicating potential wash trading. Chain-native RPC holder distribution data was unavailable at audit time, precluding sell-concentration analysis.

> **Final Recommendation:** Inspect decentralized exchange trade logs for circular wash-trading patterns and recurring routing wallets before entering positions. Query chain-native RPC directly to inspect token largest accounts once endpoint access is restored to confirm non-creator wallet distribution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard spl-token-2022 program with an initialized supply of 973,578,940,340,801 base units across 6 decimals. Both mint authority and freeze authority are verified… |
| **Governance / Economics** | 7/10 | Low | Pool liquidity stands at $19,984 with 100.0% of the LP tokens permanently burned, guaranteeing that liquidity cannot be unilaterally pulled by its creator. However, DEX market data reveals $1,152,892… |
| **Upgrades** | 10/10 | Low | Privileged control structures are nullified across the mint parameters, with neither mint nor freeze authorities active. All Token-2022 extension upgrade flags—including transfer hook upgradability… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 57.69x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Review individual swap transactions on-chain to verify genuine organic user demand versus repetitive programmatic wash trading before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 8 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EwX2T1...pump`](https://solscan.io/account/EwX2T1p2PmgTsSq2Bi6XtQYxPC5krR4P2fxPfN4Qpump) |
| **Network** | Solana |
| **Price** | $0.00009419 |
| **24h Volume** | $1.14M |
| **Liquidity** | $26.3K |
| **Volume / Liquidity** | 43.3× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16186 buys / 10856 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9sy4amm2rfpsbq1qgcqtxcjfvhmfj9k4d2j5xfm1k75m)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-03fad7-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
