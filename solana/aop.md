---
token: AOP
ticker: AOP
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# AOP (AOP) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aop-sol)

---

## Audit Summary

The token exhibits severe economic anomalies with DEX liquidity of only $1,988 and an extreme volume-to-liquidity ratio of 816.94 indicative of artificial trading activity. Technically, the token parameters are immutable with both mint and freeze authorities permanently revoked and 100.0% of LP tokens burned. Chain-native RPC holder distribution data was unavailable during this evaluation.

> **Final Recommendation:** Avoid executing standard market orders due to severe slippage hazards inherent to sub-$10,000 liquidity pools. Query Solana RPC getProgramAccounts or getTokenLargestAccounts directly to verify holder concentration once data becomes available, and avoid treating the elevated 24-hour volume as organic trading interest.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the Token-2022 program with a raw supply of 999,987,848,383,336 and 6 decimals. Both mint authority and freeze authority are revoked (set to null), permanently fixing the… |
| **Governance / Economics** | 10/10 | Low | Total DEX liquidity is severely constrained at $1,988, though 100.0% of the pool's LP tokens are permanently burned, preventing creator withdrawal. DEX market data indicates 24-hour volume of… |
| **Upgrades** | 10/10 | Low | Both mint and freeze authorities have been irrevocably renounced, ensuring that supply and account mechanics cannot be altered post-initialization. All configurable Token-2022 extensions are… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $1,988. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for severe price impact before executing trades; verify on-chain pool depth expands substantially before committing capital.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 816.94x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Do not rely on 24-hour transaction volume metrics to infer genuine market liquidity or token adoption.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.4M (DexScreener, all pools). 24h trading volume $926K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.4M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2BFm3h...pump`](https://solscan.io/account/2BFm3hSAKN5tfou7mK2VxqftqMGkSYNrJ1dXYrQdpump) |
| **Network** | Solana |
| **Price** | $0.2551 |
| **24h Volume** | $926.3K |
| **Liquidity** | $1.38M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 20h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 31731 buys / 1412 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hfdwjqgsabj1z1vexgxdmbp29gfs2vkogihrhijfkrjb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aop-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
