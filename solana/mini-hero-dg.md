---
token: Mini Hero DG
ticker: MHDG
network: solana
risk_score: 51
status: medium
date: 2026-10-17
---

# Mini Hero DG (MHDG) — Smart Contract Security Analysis | Solana

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mini-hero-dg-sol)

---

## Audit Summary

The Mini Hero DG (MHDG) token mint is an SPL Token-2022 with critical authorities, including mint and freeze, successfully revoked, ensuring a fixed supply and unfreezable accounts. However, a significant risk is identified due to high holder concentration, with the top 10 wallets controlling 70.55% of the sellable supply. Third-party registry data on detailed holder distribution was unavailable.

> **Final Recommendation:** Holders should monitor the activity of the top 10 wallets to assess potential selling pressure due to the high concentration of tokens. While core authorities are revoked, understanding the behavior of these large holders is crucial for evaluating market stability and potential price impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Mini Hero DG (MHDG) token is implemented using the spl-token-2022 program, indicating support for modern token extensions. Both the mint authority and freeze authority have been revoked, ensuring… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits high holder concentration, with the top 10 wallets holding 70.55% of the sellable supply, posing a risk of price volatility from large sell-offs. Liquidity is $31,906, with a… |
| **Upgrades** | 8/10 | Low | The token's core parameters are immutable, as both the mint and freeze authorities have been revoked. No transfer hook is present, and metadata is also immutable, preventing changes to the token's… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 70.55% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to potential large-scale sell-offs by concentrated holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.6% of supply. Of that, 11.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 70.5% in wallets, 0.0% in other contracts. 733 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

733 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $148K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2fk5eG...pump`](https://solscan.io/account/2fk5eGwAch1wGhsK3XhRUZpopXFGyRbFUn6XL4Yxpump) |
| **Network** | Solana |
| **Price** | $0.0001491 |
| **24h Volume** | $147.6K |
| **Liquidity** | $31.7K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 81.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2353 buys / 1279 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4gpuuquque9yzirtmwpzjtnyxcbb2ezj8mwkaqysorap)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mini-hero-dg-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
