---
token: gust
ticker: GUST
network: solana
risk_score: 21
status: low
date: 2026-10-23
---

# gust (GUST) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gust-sol)

---

## Audit Summary

The GUST token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, the liquidity is fully burned, preventing rug-pull risks from the creator. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should be aware that the high volume-to-liquidity ratio may not reflect organic demand and could indicate artificial trading activity. Monitor the token's price stability and slippage before executing large trades.

Verify the current supply and holder distribution periodically using block explorers to ensure no unexpected concentration develops. As the mint and freeze authorities are revoked, the token's supply and transfer rules are immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics show low holder concentration, with the top 10 holders controlling 14.11% of supply. 7.6 External market data indicates a volume/liquidity ratio of 22.04… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are fixed; the token metadata is immutable, and no authority exists to modify the token's core parameters. The mint is permanently locked, preventing future supply… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 22.04, exceeding the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading volume as a signal of organic interest.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.8% of supply. Of that, 1.8% locked, 13.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.1% in wallets, 0.0% in other contracts. 1,316 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,316 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $841K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $35K of DEX liquidity across 13 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`z1gC6K...pump`](https://solscan.io/account/z1gC6KiMdhnp5RjRtH63JjXhrWKpqK1qaDVBLfCpump) |
| **Network** | Solana |
| **Price** | $0.0001394 |
| **24h Volume** | $724.8K |
| **Liquidity** | $31.8K |
| **Volume / Liquidity** | 22.8× |
| **Token Age** | 2h |
| **Top-10 Holders** | 29.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9772 buys / 7416 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hchm41tyxtjmfwmdak4ifmvkasr7uq13uppxj5g6v3hc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gust-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
