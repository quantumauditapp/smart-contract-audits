---
token: National Oil Dividend Fund
ticker: NODF
network: solana
risk_score: 0
status: low
date: 2026-10-22
---

# National Oil Dividend Fund (NODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-sol-66f4)

---

## Audit Summary

The token mint features revoked mint and freeze authorities alongside 100.0% burned pool liquidity across $1,222,458 in total DEX backing. Critical Token-2022 extensions such as transfer hooks, balance mutability, and default frozen states are entirely disabled. Chain-native RPC data for holder concentration was unavailable at the time of data collection, leaving wallet distribution unverified.

> **Final Recommendation:** Query Solana RPC getProgramAccounts or getTokenLargestAccounts directly to map top holder distribution and detect any whale clustering before executing large swaps. Continuously verify that swap routing exclusively utilizes the primary pool with burned LP tokens rather than newly created unverified pairs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized supply of 999,987,837,630,089 raw units across 6 decimals. Mint and freeze authorities are completely revoked (None), ensuring… |
| **Governance / Economics** | 10/10 | Low | DEX liquidity is recorded at $1,222,458 with 100.0% of LP tokens burned, preventing any creator liquidity removal. Trading volume over 24 hours stands at $681,415, reflecting a normal… |
| **Upgrades** | 10/10 | Low | Administrative capabilities have been permanently relinquished with null mint and freeze authorities. Metadata mutability is set to False, locking token naming, symbol, and visual branding against… |

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

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $679K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`zDCwvt...pump`](https://solscan.io/account/zDCwvt2HxLiNhVegZaR1b5zcHDJaT9qpK1rqWKGpump) |
| **Network** | Solana |
| **Price** | $0.2042 |
| **24h Volume** | $678.8K |
| **Liquidity** | $1.22M |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35583 buys / 639 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dq5wbjrvv1iq4xdtbbwae3qj4s383gs4d425mgkfeptz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-sol-66f4)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
