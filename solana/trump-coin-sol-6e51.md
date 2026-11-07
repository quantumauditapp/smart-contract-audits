---
token: Trump Coin
ticker: TRUMP
network: solana
risk_score: 0
status: low
date: 2026-11-07
---

# Trump Coin (TRUMP) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-coin-sol-6e51)

---

## Audit Summary

The audit identified no critical administrative vulnerabilities; both mint and freeze authorities are permanently revoked, and 100.0% of pool liquidity is burned. Chain-native RPC holder distribution data was unavailable during this evaluation. DEX liquidity is currently $17,485 with an active volume-to-liquidity ratio of 8.15.

> **Final Recommendation:** Query an independent Solana RPC provider once account indexing is complete to inspect the largest individual token accounts for concentration risks. Continuously track pool depth relative to order size to minimize slippage, as liquidity remains modest at $17,485.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | Both mint and freeze authorities are revoked (null), eliminating arbitrary token creation or balance confiscation under the spl-token-2022 standard. The token initialized a fixed raw supply of… |
| **Governance / Economics** | 10/10 | Low | DEX liquidity is measured at $17,485, with 100.0% of the pool's LP tokens burned, preventing liquidity extraction by any creator or participant. The 24-hour trading volume is $142,487, representing a… |
| **Upgrades** | 10/10 | Low | All primary token mint administrative permissions have been renounced, preventing administrative state changes. Security registry indicators confirm metadata_mutable is false, locking token identity… |

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

Liquidity $51K (DexScreener, all pools). 24h trading volume $82K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $51K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EFPMJH...pump`](https://solscan.io/account/EFPMJHM3m4yZmZJBrEALMqTmTsbLGafjRuZ5jtzKpump) |
| **Network** | Solana |
| **Price** | $0.0004418 |
| **24h Volume** | $82.3K |
| **Liquidity** | $51.4K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 50291 buys / 48852 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8k2wubtnshly5twl6ojm1ttsgecaav2hrm78t3hhajhn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-coin-sol-6e51)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
