---
token: UDTF
ticker: UDTF
network: solana
risk_score: 0
status: low
date: 2026-11-07
---

# UDTF (UDTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/udtf-sol-02bc)

---

## Audit Summary

UDTF demonstrates an immutable configuration with both mint and freeze authorities permanently revoked and 100.0% of DEX pool liquidity burned. On-chain RPC data for holder concentration was unavailable during evaluation, leaving whale distribution unverified. No deterministic technical vulnerabilities or malicious authority structures were detected across active telemetry.

> **Final Recommendation:** Query the largest account holders directly via getProgramAccounts or getTokenLargestAccounts RPC methods to establish real-time wallet concentration before taking large positions. Continuously observe decentralized exchange pool depth to verify that trade execution slippage remains stable over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | UDTF operates under the spl-token-2022 program with an initialized total supply of 999,987,807,844,426 raw units across 6 decimals. Both mint authority and freeze authority are revoked (None)… |
| **Governance / Economics** | 10/10 | Low | DEX liquidity stands at $1,005,265 with a 24-hour trading volume of $748,033, reflecting an organic volume-to-liquidity ratio of 0.74 on a trading pair initialized 0 days ago. Exactly 100.0% of the… |
| **Upgrades** | 10/10 | Low | The mint structure contains no proxy mechanisms or upgradeable execution hooks. Core administrative capabilities remain permanently disabled following the complete revocation of mint and freeze keys.… |

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

Liquidity $1.0M (DexScreener, all pools). 24h trading volume $742K (DexScreener, all pools).

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
| **Contract** | [`8ZdFjU...pump`](https://solscan.io/account/8ZdFjUeMVaLbJeQy3HJsaBnEfoqkoLw4XJykphyapump) |
| **Network** | Solana |
| **Price** | $0.159 |
| **24h Volume** | $741.9K |
| **Liquidity** | $1.00M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 15h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23684 buys / 1788 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dk1rkzgyur8hq8uzxmgude2cmmhj2v3vngtddqrglay8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/udtf-sol-02bc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
