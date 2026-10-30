---
token: CRIME
ticker: CRIME
network: solana
risk_score: 40
status: medium
date: 2026-10-30
---

# CRIME (CRIME) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crime-sol)

---

## Audit Summary

The CRIME token is a Token-2022 asset with revoked mint and freeze authorities, providing a secure foundation for supply and transfer operations. However, the token exhibits high holder concentration and is flagged by a third-party registry for potential copycat behavior and single-holder ownership risks. All sources were successfully retrieved for this assessment.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs given the 50.87% concentration. Verify the token's authenticity against official project channels to mitigate risks associated with the 'copycat' classification from third-party registries.

Perform on-chain checks to confirm that no new authority-related extensions have been initialized. Use caution when trading due to the low liquidity, which may result in significant slippage for larger orders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). No transfer… |
| **Governance / Economics** | 7/10 | Low | The top 10 holders control 50.87% of the supply, indicating significant concentration (7.4 Economic). Liquidity is $11,659 and is fully burned, preventing rug pulls via liquidity withdrawal (7.5… |
| **Upgrades** | 8/10 | Low | Metadata is immutable, and no upgradeable extensions are present (7.7 Upgrades). The token state is fixed as per the revoked authority status (7.8 Operations). |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 50%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell control 50.87% of the total supply. This concentration increases the risk of price volatility if these holders coordinate a sell-off.

**Recommendation:** Monitor the top 10 holder wallets for large movements and diversify holdings to mitigate exposure to individual whale activity.


### `M-01` — Flagged by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

The token is flagged by a third-party risk registry for single-holder ownership and being a potential copycat token.

**Recommendation:** Verify the project's legitimacy through official channels and exercise caution, as these flags often correlate with higher risk of abandonment or malicious intent.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 71.7% of supply. Of that, 20.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 50.9% in wallets, 0.0% in other contracts. 194 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

194 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $80K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 4 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BN4Z5N...pump`](https://solscan.io/account/BN4Z5NtntHhu6p3atEqkeAVi8Bn9Ri2QTv8FD7iupump) |
| **Network** | Solana |
| **Price** | $0.00004242 |
| **24h Volume** | $57.0K |
| **Liquidity** | $16.3K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 1h |
| **Top-10 Holders** | 71.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 920 buys / 584 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/39sj3dqezdkpul8stn9qzwr5uwvhsuqcxxtugmndvjfe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crime-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
