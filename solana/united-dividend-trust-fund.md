---
token: United Dividend Trust Fund🔥
ticker: UDTF
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# United Dividend Trust Fund🔥 (UDTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-sol)

---

## Audit Summary

The UDTF token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, and metadata is immutable, significantly reducing central control risks. While third-party registries flag high holder correlation, the overall security posture is robust due to the absence of administrative backdoors.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate short-term price volatility. No further on-chain action is required regarding authority management, as the mint is fully renounced.

Verify the current circulating supply and holder distribution via block explorers to ensure alignment with project documentation. Monitor the DEX pool for any unexpected changes in liquidity depth, although the current 100% burn status provides strong protection against rug-pulls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program (7.1 Architecture). 7.2 Code Security is maintained by the standard, audited SPL program. 7.3 Access Control is optimal as both mint and freeze… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $149,400 in liquidity, which is 100% burned (7.6 External). 7.5 Governance is decentralized as no single entity holds significant supply, with the top 10… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, preventing branding changes. All authority-related extensions are locked, ensuring the token… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by related entities.

**Recommendation:** Monitor on-chain wallet activity for coordinated movements or sell-offs.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 0.7% of supply. Of that, 0.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.4% in wallets, 0.0% in other contracts. 2,779 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,779 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $357K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AwpzNp...pump`](https://solscan.io/account/AwpzNpDnUuMqgZVB9Q2trhWpx6ZragdWgS95UNW2pump) |
| **Network** | Solana |
| **Price** | $0.3222 |
| **24h Volume** | $356.8K |
| **Liquidity** | $1.56M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 0.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26056 buys / 1571 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5dnezejxysaoxddkhdzye3zeftqg6dzfsbcq4naqvcxl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
