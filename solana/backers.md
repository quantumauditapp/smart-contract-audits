---
token: Backers
ticker: BACKERS
network: solana
risk_score: 1
status: low
date: 2026-10-22
---

# Backers (BACKERS) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/backers-sol)

---

## Audit Summary

The Backers (BACKERS) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the on-chain technical configuration is secure, a third-party risk registry has flagged the creator's history as high-risk, necessitating caution. Liquidity is fully burned, ensuring the pool cannot be drained by the creator.

> **Final Recommendation:** Investors should monitor the token's price volatility given the high volume-to-liquidity ratio. While the on-chain authorities are revoked, the third-party risk registry flag regarding the creator's history should be considered as a non-technical risk factor.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain null. Exercise caution when interacting with tokens associated with developers flagged by security registries, regardless of the current technical security of the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust as both… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics show healthy distribution, with the top 10 holders controlling 15.34% of the supply. Liquidity is $44,343 and is 100% burned, preventing rug-pulls via… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not utilize proxy patterns. Metadata is immutable, and extension configurations such as transfer fees and hooks are locked, preventing future… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on the developer's historical activity.

**Recommendation:** Exercise extreme caution and perform independent due diligence on the project team before interacting with this token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.5% of supply. Of that, 15.7% locked, 12.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.3% in wallets, 0.0% in other contracts. 2,602 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Backers (BACKERS), rank #4679. 2,602 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $52K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $310K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $52K of DEX liquidity across 4 pools. Launch: launched on pump.fun, 17 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CBLx6C...pump`](https://solscan.io/account/CBLx6CRcCTtbmgTdxpqnF2dP1MpWbMUjngtNbFTApump) |
| **Network** | Solana |
| **Price** | $0.0001739 |
| **24h Volume** | $277.1K |
| **Liquidity** | $45.4K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 17d |
| **Top-10 Holders** | 43.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1772 buys / 2066 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/p977g14fukdl3aoh97mamqq4v7ecav5azkhtpn21ehc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/backers-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
