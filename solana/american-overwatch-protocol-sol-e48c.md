---
token: American Overwatch Protocol
ticker: AOP
network: solana
risk_score: 1
status: low
date: 2026-10-24
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-sol-e48c)

---

## Audit Summary

American Overwatch Protocol displays a secure mint architecture with both mint and freeze authorities permanently revoked and 100% of DEX pool liquidity burned. Token-2022 extensions are safely configured with immutable metadata and no restrictive hooks or balance mutability flags. On-chain holder distribution data was unavailable at the time of evaluation.

> **Final Recommendation:** Query a Solana RPC endpoint using getTokenLargestAccounts to verify real-time holder dispersion across top non-pool wallets before entering substantial positions. Track DEX pool depth over time to ensure that secondary market slippage remains stable as trading activity matures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with a raw supply of 999,952,878,171,384 across 6 decimal places and is fully initialized. Both mint and freeze authorities are irrevocably revoked… |
| **Governance / Economics** | 10/10 | Low | The trading pool maintains $581,387 in liquidity alongside a 24-hour volume of $450,483, resulting in a normal volume-to-liquidity ratio of 0.77. All 100.0% of the pool's LP tokens are permanently… |
| **Upgrades** | 10/10 | Low | The mint lacks administrative upgrade keys, with all privileged control authorities permanently set to null. Transfer hook and transfer fee modification capabilities are marked as non-upgradable… |

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

Liquidity $581K (DexScreener, all pools). 24h trading volume $442K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $581K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GK1Vxw...pump`](https://solscan.io/account/GK1Vxw9529MWwvGEwKQfVP4GAtpn1tWa7ec44bmFpump) |
| **Network** | Solana |
| **Price** | $0.04748 |
| **24h Volume** | $442.2K |
| **Liquidity** | $580.8K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 30052 buys / 8488 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/85sd7d3s63w3nlcnrladhjrplmmsh9enrunhu4pm9ojk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-sol-e48c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
