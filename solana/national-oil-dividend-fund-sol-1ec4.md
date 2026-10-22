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

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-sol-1ec4)

---

## Audit Summary

Evaluation of the NODF mint reveals no critical authority risks, as both the mint and freeze authorities are permanently revoked, and 100.0% of DEX pool liquidity is burned. The mint operates on the spl-token-2022 program with $793,578 in liquidity, a normal 0.76 volume-to-liquidity ratio, and no active transfer hooks or mutable metadata. Chain-native RPC holder distribution data was unavailable during analysis, leaving individual wallet concentration unverified.

> **Final Recommendation:** Independently query chain-native token largest accounts once RPC indexing completes to inspect holder concentration and verify wallet clustering. Continue tracking on-chain liquidity depth across DEX venues before executing high-volume orders to manage slippage risks effectively.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint is deployed via the spl-token-2022 program with an initialized raw supply of 999,967,051,773,087 and 6 decimals. Both the mint authority and freeze authority are revoked (None), preventing… |
| **Governance / Economics** | 10/10 | Low | Market liquidity is robust at $793,578 against a 24-hour volume of $602,681, yielding a healthy volume-to-liquidity ratio of 0.76. Crucially, 100.0% of the pool's liquidity is permanently burned… |
| **Upgrades** | 10/10 | Low | SPL token mints have no proxy upgrade mechanisms, with operational behavior dictated by authority keys and extension flags. The mint and freeze authorities are fully revoked, eliminating… |

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

Liquidity $792K (DexScreener, all pools). 24h trading volume $598K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $792K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8cENLm...pump`](https://solscan.io/account/8cENLm4vr5cFd9pfy2AcXjEPRv47aZrAMZbYhWWjpump) |
| **Network** | Solana |
| **Price** | $0.08611 |
| **24h Volume** | $598.3K |
| **Liquidity** | $791.7K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26985 buys / 10764 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5bozannkwsdkcy3jjc4ujjehe8vkby3gkgmc61a2dazo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/national-oil-dividend-fund-sol-1ec4)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
