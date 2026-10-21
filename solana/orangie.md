---
token: ORANGIE
ticker: ORANGIE
network: solana
risk_score: 24
status: low
date: 2026-10-21
---

# ORANGIE (ORANGIE) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orangie-sol)

---

## Audit Summary

The ORANGIE token is a Token-2022 asset with revoked mint and freeze authorities, providing a secure foundation for supply and transfer control. However, the token is flagged as high-risk by a third-party registry due to developer history and exhibits strong indicators of wash trading. Holder concentration data is unavailable, limiting the ability to assess distribution risks.

> **Final Recommendation:** Investors should exercise extreme caution due to the third-party risk registry flags regarding developer history. Monitor the token's trading volume on-chain to verify if the high volume/liquidity ratio persists, as this is a primary indicator of wash trading.

Before interacting, verify the mint and freeze authority status using a block explorer to ensure they remain null. Given the lack of holder distribution data, avoid large positions that could be subject to sudden price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, which supports advanced extensions. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics indicate significant risk. The volume/liquidity ratio of 34.34 suggests artificial trading activity. While 100% of liquidity is burned, protecting against rug… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not support proxy-based upgrades. Metadata and extension configurations are immutable, ensuring long-term consistency. 7.8 Operations are stable… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset, specifically citing developer history.

**Recommendation:** Do not interact with this token.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume is 34.34x the available liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the potential lack of genuine market depth when assessing price stability.


### `H-02` — Holder Concentration Risk  *(Severity: High · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder concentration, indicating potential for significant price manipulation.

**Recommendation:** Monitor top holder wallets for coordinated sell-off activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $539K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 8 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CdXHgb...pump`](https://solscan.io/account/CdXHgb7CboQfbTRZwH2AFnmVnDKuwkrPUFp4jt53pump) |
| **Network** | Solana |
| **Price** | $0.00003638 |
| **24h Volume** | $460.6K |
| **Liquidity** | $15.2K |
| **Volume / Liquidity** | 30.3× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7000 buys / 5125 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3tsgyldawndyvpy4x6cg4pyy9yayjs2h1e5j4kuqo9bt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orangie-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
