---
token: Over the Counter
ticker: OTC
network: solana
risk_score: 20
status: low
date: 2026-10-29
---

# Over the Counter (OTC) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/over-the-counter-sol)

---

## Audit Summary

The OTC token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. However, the token is flagged as high-risk by a third-party registry due to the creator's history of deploying rugged projects. Holder concentration data is unavailable, and the token exhibits a high volume-to-liquidity ratio.

> **Final Recommendation:** Exercise extreme caution due to the third-party registry's negative assessment of the creator's history. Before interacting, verify the mint address directly on a block explorer to ensure no unauthorized minting has occurred despite the revoked status.

Monitor the token's trading activity for signs of artificial volume. Given the high-risk classification, do not allocate capital that cannot be fully lost, as the project's provenance is highly suspect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the spl-token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics are concerning due to a high volume-to-liquidity ratio of 18.55, suggesting potential wash trading. While 100% of liquidity is burned, mitigating 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are secure as metadata is immutable and balance-mutating authorities are disabled. The token configuration is static, preventing post-launch changes to branding or… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Flagged High-Risk by Third-Party Registry  *(Severity: High · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset, specifically citing the developer's history of rugged tokens and the project's status as a copycat.

**Recommendation:** Do not interact with this token.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $34K (DexScreener, all pools). 24h trading volume $573K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $34K of DEX liquidity across 7 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Fa24xN...pump`](https://solscan.io/account/Fa24xN13pzjmcx1dtKP9nBMMFCwLtXCJrtP5hSPKpump) |
| **Network** | Solana |
| **Price** | $0.0001711 |
| **24h Volume** | $518.5K |
| **Liquidity** | $34.1K |
| **Volume / Liquidity** | 15.2× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8384 buys / 5788 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6wfuyx4dvkykpnganguajii7or1a4xmr5m8dnn2bdh1t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/over-the-counter-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
