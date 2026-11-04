---
token: Always Moist Downstairs
ticker: AMD
network: solana
risk_score: 0
status: low
date: 2026-11-04
---

# Always Moist Downstairs (AMD) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/always-moist-downstairs-sol-b19b)

---

## Audit Summary

The token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating withdrawal risks. A third-party registry flags this asset as a 'Copycat token', and holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise caution regarding the 'Copycat' classification provided by third-party registries, as this often indicates potential brand impersonation. Verify the token mint address directly against official project channels before interacting.

Monitor the token's market activity for signs of volatility, as the lack of holder distribution data prevents a full assessment of potential whale influence. No further on-chain actions are required to secure the mint itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL-2022… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by 100% of pool liquidity being burned, ensuring it cannot be withdrawn. 7.5 Governance is decentralized due to the lack of minting authority. 7.6 External signals… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are stable, with metadata and extension parameters set to immutable, preventing post-launch changes to token branding or logic. |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — Flagged as Copycat Token  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as a copycat, suggesting it may be attempting to impersonate another project.

**Recommendation:** Verify the token's authenticity through official project social media and documentation before trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $64K (DexScreener, all pools). 24h trading volume $514K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $64K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5tdWkb...pump`](https://solscan.io/account/5tdWkbqhTqVyPmksqX8WVKrHbjjqmvQfrMGwZoZPpump) |
| **Network** | Solana |
| **Price** | $0.0005988 |
| **24h Volume** | $514.4K |
| **Liquidity** | $63.8K |
| **Volume / Liquidity** | 8.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33442 buys / 1192 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/e9wpfxjqvwvdjkculu2xs742t6ehbn2cnzv2ps24fz14)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/always-moist-downstairs-sol-b19b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
