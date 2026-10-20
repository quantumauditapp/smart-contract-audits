---
token: godspeed
ticker: GODSPEED
network: solana
risk_score: 29
status: low
date: 2026-10-19
---

# godspeed (GODSPEED) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/godspeed-sol)

---

## Audit Summary

The audit identified an anomalous volume-to-liquidity ratio of 59.63, indicating probable wash trading on DEX markets despite 100% burned liquidity. Technical mint controls are secure, with both mint and freeze authorities revoked and no custodial Token-2022 extensions active. Chain-native RPC holder distribution data was partially unavailable during factual extraction.

> **Final Recommendation:** Verify real-time on-chain swap events and individual wallet transaction flows on DEX market feeds to distinguish authentic trading volume from automated circular wash trading. Monitor pool depth and slippage parameters prior to executing trades, ensuring position sizes remain proportional to the available pool liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed using the spl-token-2022 program with an initialized supply of 972,046,256.400110 across 6 decimals. Both the mint authority and freeze authority are fully revoked (set to… |
| **Governance / Economics** | 7/10 | Low | Top 10 holders that can sell represent 20.32% of total supply, demonstrating low sellable whale concentration. The DEX liquidity pool holds $15,458 in liquidity, with 100.0% of LP tokens burned… |
| **Upgrades** | 10/10 | Low | All core administrative controls are permanently disabled, as mint and freeze authorities are revoked with no upgrade capabilities. Under the Token-2022 standard, extensions such as transfer hook and… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 59.63x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating DEX market activity, as elevated trading volume relative to pool reserves often indicates artificial churn rather than organic market interest.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.0% of supply. Of that, 25.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.3% in wallets, 0.0% in other contracts. 2,359 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,359 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 29 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ArpPse...pump`](https://solscan.io/account/ArpPsesHXKbGeJsHdquM6acT3uNs7BChyetJjiNYpump) |
| **Network** | Solana |
| **Price** | $0.00003058 |
| **24h Volume** | $1.06M |
| **Liquidity** | $15.8K |
| **Volume / Liquidity** | 67.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 46.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11911 buys / 9893 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ckeezkjpcro2dep8rxjpsyfjf3tpoijmh8xvgueaxoue)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/godspeed-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
