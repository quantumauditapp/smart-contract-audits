---
token: CatoXsol
ticker: CATO
network: solana
risk_score: 27
status: low
date: 2026-11-03
---

# CatoXsol (CATO) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catoxsol-sol)

---

## Audit Summary

The CATO token exhibits significant risk factors despite having revoked mint and freeze authorities. Third-party registry data indicates a history of malicious activity by the creator and highly suspicious trading patterns. Holder distribution data is unavailable, limiting transparency regarding supply concentration.

> **Final Recommendation:** Do not interact with this token. The combination of a creator history of rug-pulling and extreme wash-trading signals suggests a high probability of malicious intent. 

Verify the token's status on-chain using a block explorer to confirm the revoked authority status, but prioritize the third-party risk registry warnings regarding developer history over the technical configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals a highly suspicious Volume/Liquidity ratio of 57,404,936, indicating extreme wash trading. 7.5 Governance is opaque due to unavailable holder distribution data. 7.6… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, and there are no upgradable transfer hooks or fees. The token configuration is static. |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history and suspicious LP movements.

**Recommendation:** Do not interact with this token.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume to liquidity ratio is 57,404,936, which is significantly above the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Account for the lack of genuine market depth in any swap calculation.


### `H-02` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $0. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Avoid trading due to the inability to execute orders without total price impact.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $76K (DexScreener, all pools). 24h trading volume $15.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $76K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9ApPnF...nH1N`](https://solscan.io/account/9ApPnFjdpLocJLLTQuCuX3gu4bcNVA224tgGaqsKnH1N) |
| **Network** | Solana |
| **Price** | $0.0001317 |
| **24h Volume** | $15.77M |
| **Liquidity** | $75.8K |
| **Volume / Liquidity** | 208.2× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14861 buys / 11245 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/455arlbzlrpu51ncal1zcuioqnkrqtk9nkj2mjgavsar)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catoxsol-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
