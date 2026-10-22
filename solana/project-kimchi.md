---
token: project kimchi
ticker: KIMCHI
network: solana
risk_score: 24
status: low
date: 2026-10-22
---

# project kimchi (KIMCHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/project-kimchi-sol)

---

## Audit Summary

The project kimchi token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio indicative of wash trading, and a third-party registry has flagged high holder concentration. Holder distribution data was unavailable for independent verification.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which suggests potential wash trading. Monitor the token on-chain to verify that no new accounts are created with excessive supply concentration.

Verify the current holder distribution using block explorers to assess the impact of the reported high concentration. Ensure that trading strategies account for the high volatility often associated with tokens exhibiting these volume patterns.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics show 100% of liquidity is burned, ensuring permanent pool availability. However, 7.6 External signals indicate a high volume-to-liquidity ratio of 199.77… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the permanent revocation of mint and freeze authorities. Metadata is immutable, preventing post-launch branding changes. |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 199.77, which significantly exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market demand.


### `M-01` — High Holder Concentration  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder concentration, which may lead to significant price volatility if large holders divest.

**Recommendation:** Monitor top holder wallets for large sell-offs and evaluate the risk of price manipulation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $9.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 24 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B1Y2fJ...pump`](https://solscan.io/account/B1Y2fJW8rtirrBuUcda14pSaeiASHaGqTxQdxU8Mpump) |
| **Network** | Solana |
| **Price** | $0.000177 |
| **24h Volume** | $8.76M |
| **Liquidity** | $39.7K |
| **Volume / Liquidity** | 220.5× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 38115 buys / 33955 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7xart3gratfp1kfrarqwujyjicbxnkuis6bgi225ga5g)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/project-kimchi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
