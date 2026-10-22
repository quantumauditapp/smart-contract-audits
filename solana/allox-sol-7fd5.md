---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 28
status: low
date: 2026-10-22
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-7fd5)

---

## Audit Summary

The AlloX token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the token exhibits high-risk economic indicators, including a volume-to-liquidity ratio suggesting wash trading and 100% of pool liquidity remaining unlocked. Third-party registry data indicates a high concentration of unlocked liquidity and low provider diversity.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows for potential sudden removal of the trading pool. Monitor the liquidity provider addresses on-chain to identify if a single entity controls the majority of the pool.

Verify that the high trading volume is organic before committing capital, as the current volume-to-liquidity ratio is highly anomalous. Do not treat the token as a long-term store of value until liquidity is demonstrably locked or burned.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, preventing further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume-to-liquidity ratio of 270.56, significantly exceeding the 20x threshold for wash-trading signals (7.4 Economic). 100% of pool liquidity is unlocked and potentially… |
| **Upgrades** | 8/10 | Low | The token uses the standard SPL Token program which does not support upgradeability (7.7 Upgrades). Metadata is immutable, ensuring branding consistency (7.8 Operations). No further authority… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 270.56, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Verify trading activity through independent block explorers to confirm organic volume.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the entire liquidity pool is currently withdrawable by anonymous holders.

**Recommendation:** Avoid providing liquidity or trading until a significant portion of the pool is locked via a reputable time-lock program.


### `M-01` — High-Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags the token for having a large amount of unlocked liquidity and a low number of liquidity providers.

**Recommendation:** Perform additional due diligence on the project's liquidity management strategy.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $334K (DexScreener, all pools). 24h trading volume $90.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $334K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`nB41Bq...Wwdw`](https://solscan.io/account/nB41BqzvvFoRAus2x3WCv55jpvyvpWLwV4GRGRMWwdw) |
| **Network** | Solana |
| **Price** | $0.00002459 |
| **24h Volume** | $90.48M |
| **Liquidity** | $333.9K |
| **Volume / Liquidity** | 271.0× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 42612 buys / 38876 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5awynycazeudmrb5bzxbw6dcofypjgghceuisknpvjdh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-7fd5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
