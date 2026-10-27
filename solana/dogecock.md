---
token: Dogecock
ticker: DOCK
network: solana
risk_score: 22
status: low
date: 2026-10-27
---

# Dogecock (DOCK) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogecock-sol)

---

## Audit Summary

The Dogecock (DOCK) token is a Token-2022 implementation with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the RPC sources.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which often indicates artificial market activity rather than organic demand. Monitor the token's price stability relative to the $24,663 liquidity pool.

Verify the current holder distribution using a block explorer to ensure no single wallet controls a majority of the circulating supply. Since the mint and freeze authorities are revoked, the token's supply and transfer mechanics are immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or default… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured as 100% of LP tokens are burned (7.4 Economic). However, the 24h volume-to-liquidity ratio of 81.69 indicates significant wash trading activity (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). No upgradeable extensions or balance-mutating authorities are present (7.8 Operations). The mint state is… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 81.69, which significantly exceeds the 20x threshold typically associated with organic trading activity.

**Recommendation:** Monitor market activity for signs of artificial volume inflation before executing large trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $2.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (doge); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 11 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FYUyPW...pump`](https://solscan.io/account/FYUyPWNLQtF4nNQ8nSHwpmwQ4j41UqAUz8gWEeWWpump) |
| **Network** | Solana |
| **Price** | $0.0001111 |
| **24h Volume** | $1.95M |
| **Liquidity** | $30.1K |
| **Volume / Liquidity** | 64.8× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16792 buys / 15178 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7yuhuk4znynheuirsqw7amkvv7t7pacd88udqwvrtxyi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogecock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
