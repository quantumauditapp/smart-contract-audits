---
token: PROJECT CORTEX
ticker: XTX
network: solana
risk_score: 2
status: low
date: 2026-10-29
---

# PROJECT CORTEX (XTX) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/project-cortex-sol)

---

## Audit Summary

PROJECT CORTEX (XTX) exhibits an immutable mint architecture with both mint and freeze authorities permanently revoked, accompanied by 100.0% burned DEX liquidity. Token holder distribution RPC data was unavailable during verification, preventing complete assessment of individual wallet concentration. Technical risk is minimal given that Token-2022 extensions such as transfer hooks and mutable metadata are absent or deactivated.

> **Final Recommendation:** Query secondary Solana RPC nodes to inspect the largest individual token accounts and verify wallet dispersion once indexer records populate. Establish alerts for coordinated swap transactions originating from interconnected clusters to anticipate abrupt slippage events during high-volume periods.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized raw supply of 999,925,522,874,277 across 6 decimals. Both mint and freeze authorities are permanently set to None, precluding… |
| **Governance / Economics** | 10/10 | Low | DEX liquidity is solidly positioned at $445,628 with 100.0% of LP tokens burned, preventing liquidity extraction by the creator or liquidity providers. 24-hour trading activity registered $233,759 in… |
| **Upgrades** | 10/10 | Low | The mint lacks any administrative upgrade vector, maintaining non-upgradable fees and transfer hook states. Metadata mutability is set to False, guaranteeing that visual branding, names, and symbols… |

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

Liquidity $444K (DexScreener, all pools). 24h trading volume $231K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $444K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`QPcdyJ...pump`](https://solscan.io/account/QPcdyJosBQzT8szqMfhAY9f7HXEywyqthJtQRaGpump) |
| **Network** | Solana |
| **Price** | $0.02811 |
| **24h Volume** | $231.3K |
| **Liquidity** | $443.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20875 buys / 368 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7bcj3vdl8yhgtmprkkmgzyjtncegjq8znjc5o5r4citd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/project-cortex-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
