---
token: Tesla
ticker: TSLA
network: solana
risk_score: 27
status: low
date: 2026-10-31
---

# Tesla (TSLA) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tesla-sol)

---

## Audit Summary

The token mint and freeze authorities are successfully revoked, preventing supply inflation and account freezing. However, the token exhibits extreme wash-trading signals and lacks any locked liquidity, posing a high risk to capital. Third-party risk registry data is unavailable for this asset.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and high volume-to-liquidity ratio. Verify the pool's liquidity status on-chain before attempting any trades, as the current liquidity is fully withdrawable by the pool creator.

Monitor the token's trading activity for signs of artificial volume. Given the absence of holder distribution data, avoid large positions that may be subject to high slippage or sudden liquidity removal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply changes or account freezing (7.3 Access Control).… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is critically low at $57,280 with 0% locked or burned (7.4 Economic). The volume/liquidity ratio of 349.77 indicates significant wash-trading activity (7.6 External). Holder concentration… |
| **Upgrades** | 8/10 | Low | The mint is immutable with no upgrade paths for metadata or transfer logic (7.7 Upgrades). Operations are restricted to standard token transfers (7.8 Operations). No further changes to the mint… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — High Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The volume/liquidity ratio is 349.77, which significantly exceeds the 20x threshold, indicating artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the pool creator can withdraw all liquidity at any time.

**Recommendation:** Treat the pool as highly volatile and subject to sudden removal of liquidity.


### `M-01` — Holder Concentration Data Unavailable  *(Severity: Medium · Status: Unresolved)*

Holder distribution data could not be retrieved, preventing the identification of potential whale concentration.

**Recommendation:** Perform manual analysis of the top token accounts via a block explorer before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $17.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $85K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2ddb5K...Hwuc`](https://solscan.io/account/2ddb5K4uujdLH83REn8Yj6JvHdkyb14QGBcJzBm7Hwuc) |
| **Network** | Solana |
| **Price** | $0.0001293 |
| **24h Volume** | $17.88M |
| **Liquidity** | $84.5K |
| **Volume / Liquidity** | 211.6× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17865 buys / 12267 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4yzjoyndls1ibu4czevfxazf4gacqbmr1q2er6ulmcxf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tesla-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
