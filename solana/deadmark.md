---
token: Deadmark
ticker: DMRK
network: solana
risk_score: 26
status: low
date: 2026-10-17
---

# Deadmark (DMRK) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/deadmark-sol)

---

## Audit Summary

The Deadmark (DMRK) SPL token mint exhibits a high concentration of tokens among its top holders, with 73.03% of the sellable supply controlled by the ten largest wallets. This poses a significant risk of price manipulation through large sell-offs. Third-party registry data reported no adverse flags, but chain-native RPC data for full holder distribution was unavailable.

> **Final Recommendation:** Prospective holders should exercise caution due to the high concentration of tokens among the top holders, which presents a risk of market manipulation. Monitor the wallets of the largest holders for any significant movements that could indicate an impending sell-off. While the liquidity is locked, the potential for large dumps remains a primary concern.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Deadmark (DMRK) token is an SPL token operating under the `spl-token` program. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 8/10 | Low | A significant economic risk is present due to high holder concentration, as the top 10 holders that can sell control 73.03% of the supply. This concentration could lead to price volatility from large… |
| **Upgrades** | 10/10 | Low | The token mint's core authorities, Mint Authority and Freeze Authority, are both revoked, meaning no further changes can be made to the token's supply or account freeze status. The token's metadata… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 73.03% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to potential large sell orders from concentrated holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.0% of supply. What remains: 21.7% in wallets, 51.3% in other contracts. 74 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

74 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 90.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. 10.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $63K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DMRKsp...a95h`](https://solscan.io/account/DMRKspYf38RCq9M6RSHP2CRhXVAPEkPLN9E7MwTfa95h) |
| **Network** | Solana |
| **Price** | $0.0000023 |
| **24h Volume** | $62.9K |
| **Liquidity** | $16.9K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 9h |
| **Top-10 Holders** | 73.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 452 buys / 393 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6a7vi4emgselfinoip5mu4o7okducby3dyxzihqpcklb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/deadmark-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
