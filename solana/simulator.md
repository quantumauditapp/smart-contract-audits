---
token: simulator
ticker: SIMULATOR
network: solana
risk_score: 15
status: low
date: 2026-10-17
---

# simulator (SIMULATOR) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/simulator-sol)

---

## Audit Summary

The simulator token mint has revoked both mint and freeze authorities, indicating a fixed supply and unfreezable accounts. Holder concentration is low, and liquidity is substantial. However, information regarding the locking status of the pool's liquidity was unavailable, which prevents a full assessment of liquidity risk.

> **Final Recommendation:** Holders should monitor the token's trading activity and liquidity over time, especially given its very recent creation. It is crucial to verify the locking status of the DEX pool's liquidity once that information becomes available, as this was not readable at the time of audit. This information is vital for a complete assessment of liquidity rug-pull risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The simulator token is an SPL Token-2022 mint (7.1 Architecture). Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing accounts can be… |
| **Governance / Economics** | 7/10 | Low | The top 10 holders that can sell account for 24.51% of the total supply, indicating a relatively decentralized distribution among major holders (7.4 Economic). The token has $151,312 in DEX liquidity… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account freeze capabilities are immutable (7.7 Upgrades). The token does not have a transfer hook, nor is its… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.6% of supply. Of that, 19.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.5% in wallets, 0.0% in other contracts. 874 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

874 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $335K (DexScreener, all pools). 24h trading volume $7.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $335K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 200 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8hnMfF...Hje4`](https://solscan.io/account/8hnMfF4XL717GVwzDmvqjJvULozKW6w7BhHFABjvHje4) |
| **Network** | Solana |
| **Price** | $0.001279 |
| **24h Volume** | $964.8K |
| **Liquidity** | $154.8K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 43.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3731 buys / 3804 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gfkksyqkfs4ndlq46mt9mhbda2ihvy39fjeayu9ikafu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/simulator-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
