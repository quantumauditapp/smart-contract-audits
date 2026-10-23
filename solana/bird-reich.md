---
token: Bird Reich
ticker: FALCONS
network: solana
risk_score: 24
status: low
date: 2026-10-23
---

# Bird Reich (FALCONS) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bird-reich-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Monitor the token's trading volume on decentralized exchanges to determine if the high volume-to-liquidity ratio persists, as this is often indicative of artificial activity. Since holder distribution data is unavailable, exercise caution regarding potential whale concentration.

Verify the token's mint address on a block explorer to confirm the 'revoked' status of authorities before proceeding with any significant liquidity provision or acquisition.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $23,143 in liquidity, which is fully burned and immutable. 7.5 Governance is decentralized due to the lack of minting capabilities. However, 7.6 External market data… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, preventing post-launch branding changes. The token configuration is finalized and cannot be altered… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 45.04, exceeding the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating market demand, as the reported volume may not reflect organic trading activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6LxrUW...p3Uw`](https://solscan.io/account/6LxrUWiuYSrF3ZAEMR7u2g8jDvDBFn5q4zFxWFQup3Uw) |
| **Network** | Solana |
| **Price** | $0.00005575 |
| **24h Volume** | $1.04M |
| **Liquidity** | $19.6K |
| **Volume / Liquidity** | 52.8× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12086 buys / 9552 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/d2bavsqgswxbzj1sknyyuxk9rdnigbx3zda9pov7tvcr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bird-reich-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
