---
token: Sitting Dog
ticker: SDOG
network: solana
risk_score: 2
status: low
date: 2026-09-29
---

# Sitting Dog (SDOG) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sitting-dog-sol)

---

## Audit Summary

The Sitting Dog (SDOG) SPL token mint exhibits a low technical risk profile with both mint and freeze authorities revoked, and no active transfer hooks or mutable metadata. However, the DEX trading pair is very new, having been created only 5 days ago, which introduces uncertainty regarding market stability and team behavior. Holder distribution data was unavailable, preventing a full assessment of supply concentration risk.

> **Final Recommendation:** Given the very recent launch of the DEX pair, prospective holders should exercise caution and monitor the token's market behavior closely over the coming weeks. Observe trading patterns, liquidity trends, and any announcements from the project team. Regularly check for updates on holder distribution once that data becomes available to assess potential concentration risks. Verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The SPL Token Mint for Sitting Dog (SDOG) is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, indicating that no new tokens can be minted… |
| **Governance / Economics** | 10/10 | Low | The economic profile of the Sitting Dog (SDOG) token shows a total DEX liquidity of $112,343, which is sufficient for moderate trading. The 24-hour trading volume is $663,539, resulting in a… |
| **Upgrades** | 10/10 | Low | The Sitting Dog (SDOG) SPL token mint demonstrates a high degree of immutability regarding its core parameters. The mint authority has been revoked, preventing any further supply increases.… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 5 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Account for the limited history when evaluating the token's stability and long-term viability.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $132K (DexScreener, all pools). 24h trading volume $761K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $132K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`yFcTuQ...pump`](https://solscan.io/account/yFcTuQJCMsd1Asya15GZ7h4KGdxsujRLcUiTWWXpump) |
| **Network** | Solana |
| **Price** | $0.001252 |
| **24h Volume** | $658.3K |
| **Liquidity** | $118.5K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 5d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2950 buys / 3711 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cbnbzf7o1hz2eaiqycsvktxrbnf8blkunex65mppd41c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sitting-dog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
