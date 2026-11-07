---
token: scamsem
ticker: SCAMSEM
network: solana
risk_score: 14
status: low
date: 2026-11-07
---

# scamsem (SCAMSEM) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/scamsem-sol)

---

## Audit Summary

The scamsem token utilizes the Token-2022 program with all primary authorities (Mint and Freeze) successfully revoked. While liquidity is fully burned, the token exhibits high wash-trading signals and is flagged by a third-party registry for high holder concentration. Holder distribution data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's volume patterns, as the high ratio relative to liquidity suggests artificial activity. Given the third-party registry flag regarding holder concentration, exercise caution regarding potential price manipulation by early holders.

Verify the current holder distribution using block explorers to confirm if a small number of wallets control a majority of the supply. Do not rely solely on the burned liquidity status as a guarantee of price stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the Token-2022 program (7.1 Architecture). Both Mint and Freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). No… |
| **Governance / Economics** | 10/10 | Low | Liquidity is $66,251 and is 100% burned, preventing creator withdrawal (7.4 Economic). However, the 24h volume/liquidity ratio of 21.43 indicates potential wash-trading (7.8 Operations). A… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgrade paths exist for transfer hooks or fees (7.7 Upgrades). The mint configuration is static and cannot be modified post-deployment. |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 21.43, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of automated or non-organic volume before executing large orders.


### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk due to high holder concentration.

**Recommendation:** Conduct independent due diligence on the token's distribution and developer history.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 61% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $121K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $121K of DEX liquidity across 29 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`41WpXn...pump`](https://solscan.io/account/41WpXn15fxQXEGhiKnkqHcoJn14tNXXgmymLKE57pump) |
| **Network** | Solana |
| **Price** | $0.0006509 |
| **24h Volume** | $1.35M |
| **Liquidity** | $73.6K |
| **Volume / Liquidity** | 18.3× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16573 buys / 12479 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7xfy46cx3ierdux2denyam4plxpqecouvcaz9n3gyh76)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/scamsem-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
