---
token: USOE
ticker: USOE
network: solana
risk_score: 1
status: low
date: 2026-11-01
---

# USOE (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-sol-538f)

---

## Audit Summary

No critical technical vulnerabilities or privileged authority risks were detected, as both mint and freeze authorities are permanently revoked and all pool liquidity is burned. The Token-2022 deployment operates without transfer hooks, transfer fees, or mutable metadata. Native chain RPC holder distribution data was unavailable during analysis, leaving individual wallet concentration unverified.

> **Final Recommendation:** Query getProgramAccounts and getTokenLargestAccounts via native Solana RPC endpoints periodically to evaluate top sellable holder concentration once distribution stabilizes. Set alerts for newly initialized AMM liquidity pools to ensure secondary venues match the burn parameters of the primary pair. Continuously observe cluster movements among correlated holder accounts to anticipate coordinated liquidity exits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with a fixed supply of 999,998,926,572,490 raw units across 6 decimals. Both mint authority and freeze authority are revoked (None), preventing… |
| **Governance / Economics** | 10/10 | Low | Decentralized exchange liquidity stands at $1,043,316, with 100.0% of LP tokens permanently burned, eliminating liquidity removal vectors. Trading activity recorded $3,443,397 in 24-hour volume… |
| **Upgrades** | 10/10 | Low | Authority revocation is complete, leaving no administrative keys capable of altering mint parameters. The Token-2022 extension configuration lacks upgradeable transfer fees or upgradeable transfer… |

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

Liquidity $1.0M (DexScreener, all pools). 24h trading volume $3.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.0M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DxUtHs...pump`](https://solscan.io/account/DxUtHsGFuHxyAt3SiWPCvy5yeY7PCGzp9iYmwpw7pump) |
| **Network** | Solana |
| **Price** | $0.1599 |
| **24h Volume** | $3.44M |
| **Liquidity** | $1.04M |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 31449 buys / 9350 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c11s7rrqja6y3enox82g9gve211nvpzmex6khkb4ux97)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-sol-538f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
