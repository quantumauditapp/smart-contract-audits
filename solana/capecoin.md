---
token: Capecoin
ticker: CAPE
network: solana
risk_score: 21
status: low
date: 2026-10-22
---

# Capecoin (CAPE) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/capecoin-sol)

---

## Audit Summary

Capecoin is an SPL Token-2022 asset with revoked mint and freeze authorities, providing strong technical security regarding supply and transfer control. However, the token is flagged as high-risk by a third-party registry due to the creator's history of malicious activity, and the trading data exhibits strong indicators of wash trading. Holder concentration data is currently unavailable.

> **Final Recommendation:** Exercise extreme caution due to the third-party risk registry flag regarding the developer's history. Monitor the token's trading volume on-chain to verify if the high activity is organic or artificial.

Verify the current supply and authority status using a block explorer to ensure no unexpected changes have occurred. Do not rely on the token's branding, as the creator's history suggests a high probability of malicious intent despite the current technical configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics are concerning due to a volume/liquidity ratio of 33.91, suggesting artificial trading. 7.6 External signals indicate a high-risk creator history. Liquidity is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable. Metadata is immutable, and no balance-mutating authorities exist. |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on the developer's history of rugged tokens.

**Recommendation:** Do not interact with this token.


### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,561. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 33.91x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Be aware that reported volume may not reflect genuine market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $401K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 4 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GMDaSA...pump`](https://solscan.io/account/GMDaSAbntf9ZTGvnAj53Vn3pSRVo6oe6NaiKLYy9pump) |
| **Network** | Solana |
| **Price** | $0.00004383 |
| **24h Volume** | $303.2K |
| **Liquidity** | $17.1K |
| **Volume / Liquidity** | 17.8× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4503 buys / 3249 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/49iufsmzzfpxbjpg854p9jrujwccjeb9weqqzc37qw4c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/capecoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
