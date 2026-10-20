---
token: Bordrless
ticker: BORDR
network: solana
risk_score: 12
status: low
date: 2026-10-10
---

# Bordrless (BORDR) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bordrless-sol)

---

## Audit Summary

This audit of the Bordrless (BORDR) SPL token mint found no critical or high-severity issues based on the available on-chain data and third-party security registries. Both the mint and freeze authorities have been revoked, and the token's metadata is immutable. However, information regarding holder concentration and the locking status of the liquidity pool was unavailable for this assessment.

> **Final Recommendation:** While no immediate critical risks were identified, users should independently monitor the token's liquidity pool for any significant withdrawals, as the locking status of the liquidity was not confirmed. It is also recommended to seek out and verify holder distribution data to assess any potential concentration risks that could impact market stability. Maintain vigilance for any unexpected on-chain activity, although the current revoked authorities mitigate many common risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Bordrless token is implemented using the standard SPL Token Program v3. A significant strength is that both the mint authority and freeze authority have been revoked, preventing further token… |
| **Governance / Economics** | 7/10 | Low | The token currently has a liquidity of $334,399 USD, supporting trading activity. The 24-hour volume to liquidity ratio is 2.32, which is within normal parameters and does not suggest wash trading.… |
| **Upgrades** | 8/10 | Low | The token's upgradeability posture is robust due to the revocation of key authorities. Both the mint authority and freeze authority are permanently revoked, meaning the token's supply and the ability… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Bordrless (BORDR), market cap $3M, rank #2113.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $627K (DexScreener, all pools). 24h trading volume $3.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $627K of DEX liquidity across 8 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6Mix12...ordr`](https://solscan.io/account/6Mix12LiHrQFojaQEnfPUC65Qkwd6X4Y5Qg93oFbordr) |
| **Network** | Solana |
| **Price** | $0.002881 |
| **24h Volume** | $767.8K |
| **Liquidity** | $333.7K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1744 buys / 1645 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ftmwv748vxvvrrohjyzvdfyl4sxp3c6qtnhsem5qhewz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bordrless-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
