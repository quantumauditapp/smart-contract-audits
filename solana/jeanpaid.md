---
token: JEANPAID
ticker: JEANPAID
network: solana
risk_score: 13
status: low
date: 2026-09-29
---

# JEANPAID (JEANPAID) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jeanpaid-sol)

---

## Audit Summary

The JEANPAID token mint presents a Medium overall risk, primarily due to its very recent launch and a high volume-to-liquidity ratio, which can indicate artificial trading activity. While core minting and freezing authorities are revoked, holder concentration data was unavailable, preventing a full assessment of distribution risk. A third-party risk registry also signals high holder correlation.

> **Final Recommendation:** Prospective holders should exercise caution due to the token's nascent age and the high volume-to-liquidity ratio, which may suggest artificial trading. It is crucial to monitor the token's liquidity growth and observe its trading patterns over a longer period. Verify on-chain that the Mint and Freeze Authorities remain revoked to ensure supply and transfer stability. Continuously monitor holder distribution as this data becomes available to assess potential concentration risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The JEANPAID token is an SPL Token-2022 mint with a total supply of 971,691,658,178,172 tokens and 6 decimals. The Mint Authority and Freeze Authority have both been revoked, indicating that no new… |
| **Governance / Economics** | 9/10 | Low | The token exhibits very low liquidity, with total DEX liquidity at $36,806. The 24-hour trading volume is $281,868, resulting in a high Volume/Liquidity Ratio of 7.66, which can be a signal of wash… |
| **Upgrades** | 10/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, have been revoked, preventing any future changes to the token supply or the ability to freeze accounts. The token does not have a… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

The DEX pair for JEANPAID was created 0 days ago. This indicates an insufficient track record to assess the team's long-term commitment or typical holder behavior.

**Recommendation:** Exercise increased caution with very new pairs. Monitor the project's activity, community engagement, and liquidity trends over several weeks before making significant investments.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $294K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4Exc9S...pump`](https://solscan.io/account/4Exc9SfSRRButkzTT456SPa6sTzQCb8pnfqcUECGpump) |
| **Network** | Solana |
| **Price** | $0.0001778 |
| **24h Volume** | $280.8K |
| **Liquidity** | $37.1K |
| **Volume / Liquidity** | 7.6× |
| **Token Age** | 15h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3285 buys / 2175 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ejda4ai1ws8uimefupvmzyaamluyp8gvltvwvlqcicgv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jeanpaid-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
