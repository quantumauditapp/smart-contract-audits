---
token: Peace Coin
ticker: PEACE
network: solana
risk_score: 14
status: low
date: 2026-11-02
---

# Peace Coin (PEACE) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/peace-coin-sol)

---

## Audit Summary

Peace Coin (PEACE) is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against administrative abuse. The primary risk identified is a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise caution regarding the high trading volume relative to liquidity, as this often indicates artificial market activity. Monitor the asset for organic volume growth before committing significant capital.

Verify the current supply and holder distribution using a block explorer to ensure the token distribution aligns with expectations, as on-chain concentration data was not available at the time of this audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, ensuring modern standard compliance. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as both mint… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show $36,043 in liquidity, which is fully burned, preventing rug pulls via liquidity withdrawal. 7.5 Governance is decentralized due to authority revocation. However, 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. Metadata is immutable, and extension configurations are locked. No administrative backdoors exist to modify token parameters… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 72.20, exceeding the 20x threshold, which is a strong indicator of artificially inflated trade volume.

**Recommendation:** Monitor the token for organic trading patterns and avoid relying on volume metrics as a proxy for genuine market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 67% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $54K (DexScreener, all pools). 24h trading volume $3.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $54K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BngAfL...pump`](https://solscan.io/account/BngAfLZxaWN2QvpFhRbUHydYGr8zA7YTSA178G8Epump) |
| **Network** | Solana |
| **Price** | $0.0001703 |
| **24h Volume** | $2.55M |
| **Liquidity** | $36.5K |
| **Volume / Liquidity** | 70.0× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33556 buys / 25394 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b9kecyvzxsvvy56ussxfiyt6gd7a4w7wepkb9tnyq7sz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/peace-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
