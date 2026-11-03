---
token: HEDGE
ticker: HEDGE
network: solana
risk_score: 17
status: low
date: 2026-11-03
---

# HEDGE (HEDGE) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hedge-sol)

---

## Audit Summary

The HEDGE token mint is fully decentralized with both mint and freeze authorities revoked. While liquidity is fully locked, the high volume-to-liquidity ratio suggests potential wash trading. Holder concentration data is unavailable.

> **Final Recommendation:** Monitor the token's trading volume to determine if the high ratio is persistent or indicative of short-term manipulation. Since holder distribution data is unavailable, users should exercise caution regarding potential whale concentration.

Verify that the liquidity lock remains active via the specific Raydium locker address. Do not rely on volume metrics as a proxy for organic demand given the current wash-trading signals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (7.1 Architecture). Security is robust as both mint and freeze authorities are revoked (7.3 Access Control). No advanced extensions like transfer… |
| **Governance / Economics** | 8/10 | Low | Liquidity is 100% locked, preventing rug pulls via liquidity withdrawal (7.4 Economic). However, the volume-to-liquidity ratio of 27.15 indicates suspicious trading activity (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint is immutable with metadata locked (7.7 Upgrades). There are no upgradeable components or mutable authorities (7.8 Operations). |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 27.15, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and order book depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $57K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $57K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`wDSAqt...eYhf`](https://solscan.io/account/wDSAqt4tEZpDAwB9XY6ejkZvMFuT1zUMjUh67txeYhf) |
| **Network** | Solana |
| **Price** | $0.00007474 |
| **24h Volume** | $1.50M |
| **Liquidity** | $56.7K |
| **Volume / Liquidity** | 26.5× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14892 buys / 11330 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ishesmywetrsksuafp9xc16zy1w3ujv3idwacsnyric)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hedge-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
