---
token: startupSI
ticker: STARTUPSI
network: solana
risk_score: 15
status: low
date: 2026-10-19
---

# startupSI (STARTUPSI) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/startupsi-sol)

---

## Audit Summary

The primary risk identified is an elevated volume-to-liquidity ratio of 22.11 ($10,762,179 24-hour volume against $486,689 liquidity), presenting an active wash trading signal. Core mint parameters remain secure, with both mint and freeze authorities permanently revoked and 100.0% of pool liquidity burned. Chain-native RPC holder distribution data was unavailable during analysis.

> **Final Recommendation:** Inspect decentralized exchange transaction logs to observe whether trade flow originates from distinct retail accounts or automated repeating circular transactions. Monitor liquidity pool reserves and independent registry telemetry continuously before executing high-volume swaps.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint is initialized under the spl-token-2022 program with a raw supply of 996,160,778,564,593 across 6 decimals. Both mint authority and freeze authority are revoked (None), ensuring the total… |
| **Governance / Economics** | 8/10 | Low | The decentralized exchange pool holds $486,689 in total liquidity, with 100.0% of LP tokens permanently burned. Top 10 holders that can sell account for only 0.90% of the token supply, representing… |
| **Upgrades** | 10/10 | Low | All primary authorities over the token mint are revoked, preventing administrative interventions or supply adjustments. Metadata mutability is set to False, ensuring token details such as name and… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 22.11x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for potentially artificial trading activity when assessing genuine token velocity and demand.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.8% of supply. Of that, 0.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.9% in wallets, 0.0% in other contracts. 14,529 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

14,529 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $466K (DexScreener, all pools). 24h trading volume $10.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $466K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EKosQw...pump`](https://solscan.io/account/EKosQw4oJFbXmeJ4qRnbH1quGFRTc3Eok6nwnFKDpump) |
| **Network** | Solana |
| **Price** | $0.02301 |
| **24h Volume** | $10.69M |
| **Liquidity** | $466.0K |
| **Volume / Liquidity** | 22.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | 1.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 105539 buys / 29245 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ascpffyzxmnhhfhqqwawtcrmasguzcjtwyu6os6cqd2r)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/startupsi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
