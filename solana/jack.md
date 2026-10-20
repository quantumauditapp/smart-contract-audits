---
token: JACK
ticker: JACK
network: solana
risk_score: 15
status: low
date: 2026-09-29
---

# JACK (JACK) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jack-sol)

---

## Audit Summary

The JACK token mint has revoked its mint and freeze authorities, providing a fixed supply and preventing account freezing. However, the DEX trading pair is very new, established only 2 days ago, which limits the track record for assessing market behavior. Third-party risk registry data and holder distribution information were unavailable for a comprehensive assessment.

> **Final Recommendation:** Monitor the token's market activity closely over the coming weeks to establish a track record beyond its current 2-day age. Pay attention to liquidity trends and holder behavior as more data becomes available. Verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable status.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, which prevents further token creation and ensures that no holder accounts… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $28,532 USD, with a 24-hour trading volume of $132,268 USD. The Volume/Liquidity Ratio is 4.64, which is considered normal and does not indicate wash trading.… |
| **Upgrades** | 10/10 | Low | The token's core authorities, Mint and Freeze, are both revoked, indicating a fixed supply and unfreezable accounts. It utilizes the spl-token-2022 program but does not have a Transfer Hook or… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

The DEX pair for JACK was created only 2 days ago. This short operational period provides an insufficient track record to assess the team's long-term behavior or the stability of holder dynamics.

**Recommendation:** Exercise caution due to the nascent nature of the trading pair. Monitor the token's performance, liquidity, and holder activity over a longer period to gain a clearer understanding of its market stability and community engagement.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $143K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $28K of DEX liquidity across 11 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`J1yxV5...sYzJ`](https://solscan.io/account/J1yxV53EmVRmt9RUj6PPufMfdAYUbtgwXCuNYTBTsYzJ) |
| **Network** | Solana |
| **Price** | $0.00005258 |
| **24h Volume** | $138.6K |
| **Liquidity** | $26.1K |
| **Volume / Liquidity** | 5.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1743 buys / 1571 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/aqb9ihwudzy364jist8jccurse8wcsyg7wu7glz6ngqn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jack-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
