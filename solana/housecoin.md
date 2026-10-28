---
token: Housecoin
ticker: HOUSECOIN
network: solana
risk_score: 17
status: low
date: 2026-10-28
---

# Housecoin (HOUSECOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/housecoin-sol)

---

## Audit Summary

Housecoin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against supply inflation and account freezing. The primary risk identified is a high volume-to-liquidity ratio suggesting potential wash trading, alongside the unavailability of holder concentration data. Third-party registry data indicates no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the high trading volume relative to liquidity, as this often indicates artificial market activity. Monitor the asset on-chain to ensure no unexpected changes in market depth.

Verify the current supply and holder distribution using a block explorer to assess if the lack of concentration data masks significant whale holdings. Do not rely solely on the lack of adverse registry flags when evaluating market entry.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints, as no custom logic is present. 7.3… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis reveals a volume-to-liquidity ratio of 45.16, exceeding the 20x threshold for wash-trading signals. 7.6 External data confirms 100% of pool liquidity is burned, preventing… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and extension configurations are locked, ensuring long-term consistency of token parameters. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 45.16, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity can lead to misleading price signals and difficulty in executing large trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 52% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $135K (DexScreener, all pools). 24h trading volume $2.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $135K of DEX liquidity across 29 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DUKEjs...pump`](https://solscan.io/account/DUKEjskPBoszW4xEowcSWptekuUZpwLFv6nTt5Cmpump) |
| **Network** | Solana |
| **Price** | $0.0005867 |
| **24h Volume** | $2.45M |
| **Liquidity** | $70.6K |
| **Volume / Liquidity** | 34.8× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 25908 buys / 20095 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/92gxaewxdsz3svugo8jmezy1fcxvwznaebksmpewp2k9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/housecoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
