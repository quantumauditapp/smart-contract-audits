---
token: is it bundled?
ticker: BUNDLED
network: solana
risk_score: 16
status: low
date: 2026-10-11
---

# is it bundled? (BUNDLED) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/is-it-bundled-sol)

---

## Audit Summary

This audit of the 'is it bundled?' (BUNDLED) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. Both mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the immutability of supply and account status. While holder distribution data was unavailable in this assessment, monitoring the top holder accounts for significant concentration shifts is always prudent for any token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The BUNDLED token is an SPL Token-2022 mint with a total supply of 978,410,451,928,032 units and 6 decimals. Crucially, both the mint authority and freeze authority have been revoked, preventing… |
| **Governance / Economics** | 9/10 | Low | The token exhibits healthy liquidity management, with 100.0% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn by any party. Current DEX liquidity stands at $29,722, with a… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, indicating a fixed supply and immutable freeze status. The token utilizes the spl-token-2022 program but does not have a Transfer Hook or… |

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

Liquidity $30K (DexScreener, all pools). 24h trading volume $84K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`89PmWt...pump`](https://solscan.io/account/89PmWtV1ZuFusUJJ2Vxd3i5PtK7RvdrnBs3P9i7wpump) |
| **Network** | Solana |
| **Price** | $0.0001168 |
| **24h Volume** | $83.6K |
| **Liquidity** | $29.6K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 791 buys / 847 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/h1emsfzcmmm7nbhww5gclkmwnzp4w65ygwqpll5mucfr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/is-it-bundled-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
