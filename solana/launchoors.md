---
token: Launchoors
ticker: LAUNCHOORS
network: solana
risk_score: 17
status: low
date: 2026-10-28
---

# Launchoors (LAUNCHOORS) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/launchoors-sol)

---

## Audit Summary

The Launchoors token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. However, the token is flagged as high-risk by a third-party registry due to developer history, and the metadata remains mutable. Holder concentration data is unavailable.

> **Final Recommendation:** Investors should exercise caution due to the third-party registry flag regarding developer history. Verify the current token metadata on-chain before trading to ensure it matches expected branding.

Monitor the token's liquidity and volume metrics periodically. Since holder concentration data is unavailable, avoid large positions that could be impacted by sudden, non-transparent sell-offs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default… |
| **Governance / Economics** | 9/10 | Low | Liquidity is $58,179 and is 100% locked in a permanent locker (7.4 Economic). The volume/liquidity ratio of 6.01 suggests moderate trading activity (7.6 External). Holder concentration data is… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing future supply inflation or account freezing (7.7 Upgrades). However, the token metadata is mutable, allowing the creator to change… |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history and liquidity provider metrics.

**Recommendation:** Conduct independent due diligence on the project team and historical project performance.


### `M-02` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the creator at any time.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Holder Concentration Data Unavailable  *(Severity: Low · Status: Unresolved)*

The distribution of tokens among the top holders cannot be verified due to missing data.

**Recommendation:** Monitor on-chain explorer data for large wallet movements that may indicate potential market manipulation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $45K (DexScreener, all pools). 24h trading volume $217K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $45K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AWvvUN...ASFV`](https://solscan.io/account/AWvvUNraPXGSwRnRos81ScCdJ7TzkuenYxWfS37qASFV) |
| **Network** | Solana |
| **Price** | $0.0002833 |
| **24h Volume** | $217.1K |
| **Liquidity** | $45.4K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2588 buys / 1881 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6vhr8pmbjkjrhwfwx6efnho6ck59t78r9lojraidresa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/launchoors-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
