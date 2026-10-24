---
token: Digital Oil Trust Fund
ticker: DOTF
network: solana
risk_score: 1
status: low
date: 2026-10-24
---

# Digital Oil Trust Fund (DOTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/digital-oil-trust-fund-sol)

---

## Audit Summary

The Digital Oil Trust Fund (DOTF) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls. Holder concentration data is unavailable, and a third-party registry flags high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's holder distribution as it becomes available to assess the impact of the flagged high holder correlation. No further technical action is required regarding authority management as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the spl-token-2022 program. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are set to null. 7.2 Code Security is maintained by… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $164,693 in liquidity, which is 100% burned, preventing withdrawal by the creator. 7.5 Governance and 7.6 External factors include a healthy volume/liquidity… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is an immutable SPL token mint. 7.8 Operations are secure due to the revocation of all administrative authorities. Metadata is immutable, ensuring branding… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, which may indicate centralized control despite the revocation of administrative authorities.

**Recommendation:** Monitor on-chain wallet activity for coordinated movements among the largest holders.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $164K (DexScreener, all pools). 24h trading volume $339K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $164K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3w9tQE...pump`](https://solscan.io/account/3w9tQEQsrLdEVpHZq8rJrnGwagFUmyySwZbKuefWpump) |
| **Network** | Solana |
| **Price** | $0.003785 |
| **24h Volume** | $339.4K |
| **Liquidity** | $164.3K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26241 buys / 13466 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9deacnsw3uhkdt1vkxwbv6z3zpbj2ggi5qduukrbeflh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/digital-oil-trust-fund-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
