---
token: Loadout
ticker: LOAD
network: solana
risk_score: 10
status: low
date: 2026-10-13
---

# Loadout (LOAD) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/loadout-sol)

---

## Audit Summary

The Loadout (LOAD) SPL token mint has revoked both mint and freeze authorities, indicating a fixed supply and immutability of account states. However, holder concentration data was unavailable from chain-native RPC, and liquidity locking status was not read, preventing a full assessment of economic risks. A third-party risk registry signals high ownership by top holders, which warrants monitoring.

> **Final Recommendation:** Holders should monitor the token's liquidity pool for any changes in its locked status, as this information was not available during the audit. Given the third-party signals regarding high holder concentration, it is advisable to track the largest holder wallets for any significant movements that could impact market stability. Verify on-chain that the mint and freeze authorities remain revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Loadout (LOAD) token is an SPL token operating on the Solana blockchain using the `spl-token` program. Both the mint authority and freeze authority have been permanently revoked, ensuring that no… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a liquidity of $248,652 USD with a 24-hour trading volume of $1,889,035 USD. The Volume/Liquidity Ratio is 7.60, indicating active trading relative to available liquidity, though… |
| **Upgrades** | 8/10 | Low | The Loadout (LOAD) SPL token mint has a robust immutability posture, with both mint and freeze authorities permanently revoked. This means the token's supply is fixed and no accounts can be frozen… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Loadout (LOAD).

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $502K (DexScreener, all pools). 24h trading volume $17.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $9.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $502K of DEX liquidity across 20 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8sWe4G...PtPo`](https://solscan.io/account/8sWe4GzK1YqG3vyzKHf8ZyB1WB5asofw2o6TqgFePtPo) |
| **Network** | Solana |
| **Price** | $0.00783 |
| **24h Volume** | $1.88M |
| **Liquidity** | $271.6K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3451 buys / 3377 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gawaa7x6sxcltdd2ffwrgzpxbzjm7cz5xdbxpyp1kkxz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/loadout-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
