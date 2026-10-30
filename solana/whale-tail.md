---
token: Whale Tail
ticker: WTAIL
network: solana
risk_score: 71
status: high
date: 2026-10-30
---

# Whale Tail (WTAIL) — Smart Contract Security Analysis | Solana

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/whale-tail-sol)

---

## Audit Summary

The token exhibits critical risks due to the pool creator retaining full control over liquidity and a third-party registry flagging the developer for previous rug-pull activity. While mint and freeze authorities are revoked, the lack of locked liquidity and negative developer history present a high probability of loss. Third-party risk registry data was successfully retrieved.

> **Final Recommendation:** Do not interact with this token due to the high risk of liquidity withdrawal by the pool creator and the developer's history of malicious activity. If you must monitor the asset, track the creator wallet (5hxxeQ…Ajp8) on a block explorer to observe any sudden removal of liquidity from the DEX pool.

Verify the current metadata on-chain before any transaction to ensure the branding has not been altered to impersonate other projects. Given the lack of locked liquidity, assume all funds deposited into the liquidity pool are at risk of permanent loss.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are sound as both Mint and Freeze authorities are revoked. 7.2 Code Security is standard for the SPL… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are extreme as 100% of liquidity is held by the pool creator (5hxxeQ…Ajp8) and is not locked. 7.6 External signals indicate a history of malicious activity by… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL mints; however, 7.8 Operations include mutable metadata. The token name, symbol, or image can be modified by the owner at any time. |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history and previous rug-pull activity.

**Recommendation:** Do not interact with this token.


### `H-01` — Pool Creator Can Withdraw Liquidity  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is held, unlocked, by the wallet that created the pool (5hxxeQ…Ajp8). It can remove that liquidity at any moment and leave holders unable to sell.

**Recommendation:** Watch that wallet's liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the wallet that created this pool (5hxxeQ…Ajp8) — it can pull that liquidity at any moment. This is the rug-pull path.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $36K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HBFxk7...7SZM`](https://solscan.io/account/HBFxk72r4xVqhT8yK8ZFXEEGvpfkoeeSTQXiewZP7SZM) |
| **Network** | Solana |
| **Price** | $0.0001032 |
| **24h Volume** | $35.7K |
| **Liquidity** | $17.4K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4300 buys / 3915 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3sd4zwqnpclfmenqbscqvspxbatkwkupbv7hm7dy7y3z)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/whale-tail-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
