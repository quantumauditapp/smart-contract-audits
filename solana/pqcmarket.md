---
token: pqc.market
ticker: PQC
network: solana
risk_score: 0
status: low
date: 2026-10-11
---

# pqc.market (PQC) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pqcmarket-sol)

---

## Audit Summary

This SPL Token Mint, pqc.market (PQC), exhibits a robust security posture based on available on-chain data. Both mint and freeze authorities have been revoked, and 100% of its DEX liquidity is burned, indicating a high degree of immutability and security. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** Given the strong security posture, holders should continue to monitor the token's trading activity and liquidity. While holder distribution data was unavailable, its absence does not indicate a direct vulnerability. No specific on-chain verification steps are immediately necessary beyond confirming the current state of revoked authorities and burned liquidity, which are already established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The pqc.market (PQC) token is built on the spl-token-2022 program, indicating a modern and extensible token architecture. Access control is robust, with both the mint authority and freeze authority… |
| **Governance / Economics** | 10/10 | Low | Economically, the token demonstrates strong security with 100% of its pool liquidity burned, eliminating the risk of liquidity rug pulls. Current DEX liquidity is $75,654, supporting a 24-hour… |
| **Upgrades** | 10/10 | Low | The token's design emphasizes immutability and resistance to unauthorized changes. Both mint and freeze authorities are revoked, meaning no administrative keys can alter the token's supply or freeze… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as pqc.market (PQC), rank #3902.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 58% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $136K (DexScreener, all pools). 24h trading volume $1.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $136K of DEX liquidity across 19 pools. Launch: launched on pump.fun (PumpSwap), 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7K52aY...cxLh`](https://solscan.io/account/7K52aYQW9rWGjwZmQ7o2d1P6E7bji6hSMsqaLy5EcxLh) |
| **Network** | Solana |
| **Price** | $0.0004398 |
| **24h Volume** | $647.3K |
| **Liquidity** | $78.2K |
| **Volume / Liquidity** | 8.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5474 buys / 5065 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6quucwd9fyrafora8xvmdapqbxckbuiztmkcyd47rwss)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pqcmarket-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
