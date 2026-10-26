---
token: Squad Champion Series
ticker: SCS
network: solana
risk_score: 22
status: low
date: 2026-10-26
---

# Squad Champion Series (SCS) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/squad-champion-series-sol)

---

## Audit Summary

The Squad Champion Series (SCS) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token is flagged as a 'Copycat token' by a third-party registry and exhibits trading patterns consistent with wash trading. All data sources were successfully retrieved.

> **Final Recommendation:** Investors should exercise caution regarding the token's market activity, as the high volume-to-liquidity ratio and 'Copycat' classification suggest speculative or artificial trading behavior. Verify the token's identity against official project channels to ensure it is not an impersonation of a legitimate asset.

Monitor the top holder distribution periodically to ensure that the 15.13% concentration does not increase significantly, which could lead to price manipulation. No further on-chain action is required regarding authority management as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL-2022… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is supported by 100% of pool liquidity being burned, preventing rug pulls via withdrawal. 7.5 Governance is decentralized due to the lack of administrative authorities.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is immutable, and extension configurations such as transfer fees are not upgradable, ensuring long-term consistency of the token's… |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 22.55, exceeding the threshold of 20. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and avoid relying on volume as a metric for liquidity or interest.


### `L-01` — Flagged as Copycat Token  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged this token as a 'Copycat token', indicating it may be impersonating another project.

**Recommendation:** Verify the token address against official project documentation before interacting.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.5% of supply. Of that, 5.6% locked, 10.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.1% in wallets, 0.0% in other contracts. 971 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

971 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4U6Qvb...pump`](https://solscan.io/account/4U6QvbLXyTpJTiU9HbgaN9yGa6CQ7gXFnWL1HFaWpump) |
| **Network** | Solana |
| **Price** | $0.0002622 |
| **24h Volume** | $1.03M |
| **Liquidity** | $44.0K |
| **Volume / Liquidity** | 23.4× |
| **Token Age** | 10h |
| **Top-10 Holders** | 31.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9407 buys / 9803 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/z9dvrydunsrx2ahj9dhyq7ubaqthvzg2ozvcyyrxkun)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/squad-champion-series-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
