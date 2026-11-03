---
token: Bingus
ticker: BINGUS
network: solana
risk_score: 22
status: low
date: 2026-11-03
---

# Bingus (BINGUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bingus-sol)

---

## Audit Summary

The Bingus token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While liquidity is fully locked, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, as it may not reflect genuine market demand. Monitor the token's trading activity on DEX platforms to ensure liquidity remains stable and that the volume is not solely driven by automated wash-trading bots.

Verify the current holder distribution using block explorers to ensure that supply is not overly concentrated among a few wallets, as this could lead to significant price volatility despite the locked liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 7/10 | Low | Liquidity is 100% locked in a verified LP locker, preventing rug pulls via liquidity withdrawal (7.4 Economic). However, the 24h volume-to-liquidity ratio of 26.92 exceeds the 20x threshold… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns in the SPL Token program (7.8 Operations). The mint… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 26.92, which exceeds the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading patterns for signs of automated volume manipulation before executing large trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $45K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $45K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2HbNwn...Loat`](https://solscan.io/account/2HbNwnhiL8HBK5mkdrcB9nbDxknPqGmJdXrtuH5fLoat) |
| **Network** | Solana |
| **Price** | $0.00004634 |
| **24h Volume** | $979.0K |
| **Liquidity** | $44.7K |
| **Volume / Liquidity** | 21.9× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10955 buys / 7729 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bv8fw9m6dt51sdasbepppmvhhj4cffdg5rkayfoantzt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bingus-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
