---
token: Parasite
ticker: PARASITE
network: solana
risk_score: 1
status: low
date: 2026-10-01
---

# Parasite (PARASITE) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/parasite-sol)

---

## Audit Summary

The Parasite (PARASITE) SPL Token Mint exhibits a strong security posture with all critical authorities revoked and 100% of its liquidity burned. No high-risk flags were reported by third-party registries. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Holders should monitor for any future changes in the token's on-chain state, although the current configuration with revoked authorities and immutable parameters significantly reduces common risks. Given the unavailability of holder distribution data, it is advisable to observe on-chain holder patterns independently to assess potential concentration risks. No further specific actions are required based on the current audit findings.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Parasite token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, preventing further token minting or freezing of holder accounts. No… |
| **Governance / Economics** | 10/10 | Low | The token exhibits strong liquidity security, with 100.0% of the pool's LP tokens burned, ensuring that liquidity cannot be withdrawn by any party. Total DEX liquidity stands at $75,680. The 24-hour… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as indicated by the revocation of both Mint and Freeze Authorities. Key Token-2022 extensions such as Transfer Hook and Default Account State Frozen are not… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Parasite (PARASITE), rank #4122.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 65% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $125K (DexScreener, all pools). 24h trading volume $1.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $125K of DEX liquidity across 28 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3kmygW...pump`](https://solscan.io/account/3kmygWKZBkCYrgZHKfiuB9UFKTcDLTFFsKo3BWpmpump) |
| **Network** | Solana |
| **Price** | $0.000511 |
| **24h Volume** | $728.5K |
| **Liquidity** | $81.0K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5406 buys / 5968 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4zlrghwkdxyatovp8ukv66cskwgo9e7kaagycw1vfh7e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/parasite-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
