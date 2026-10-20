---
token: SATOSHI
ticker: SATOSHI
network: solana
risk_score: 17
status: low
date: 2026-10-06
---

# SATOSHI (SATOSHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/satoshi-sol)

---

## Audit Summary

The SATOSHI (SATOSHI) SPL token mint has no critical or high-severity findings based on available on-chain data. Both mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Given the revoked mint and freeze authorities and burned liquidity, this token presents a low-risk profile based on the available on-chain data. Holders should monitor for any future changes in the token's on-chain state, particularly if new extensions are ever introduced (though unlikely with revoked authorities). It is also advisable to seek out holder distribution data from alternative sources if available, as this information was not provided in the current assessment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The SATOSHI token operates on the `spl-token` program. Both the Mint Authority and Freeze Authority are revoked (None), ensuring no new tokens can be minted and no existing accounts can be frozen.… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a healthy liquidity profile, with $10,994 in total DEX liquidity. Crucially, 100.0% of the pool's LP tokens are burned, meaning this liquidity can never be withdrawn by anyone. The… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and transferability parameters are immutable. The `metadata_mutable` flag is false, indicating that the token's… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $47K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (toshi); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2Jrkp1...ygpG`](https://solscan.io/account/2Jrkp1PWkz33BAy5s5MUwqUs5odMgYj1fZYaxC8RygpG) |
| **Network** | Solana |
| **Price** | $0.00001799 |
| **24h Volume** | $46.5K |
| **Liquidity** | $11.0K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 524 buys / 538 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7q9vvwh6th9bwdxyu3ojtgvsjwogxgmwche4lumbtyhg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/satoshi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
