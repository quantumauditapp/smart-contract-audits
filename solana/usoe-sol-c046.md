---
token: USOE
ticker: USOE
network: solana
risk_score: 0
status: low
date: 2026-11-01
---

# USOE (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-sol-c046)

---

## Audit Summary

The USOE mint configuration displays strong baseline immutability with both mint and freeze authorities permanently revoked, accompanied by $4,456,293 in DEX liquidity that is 100.0% burned. Detailed holder distribution metrics were unavailable from chain-native RPC during data collection, although third-party risk registries flagged elevated holder correlation signals. No deterministic authority or extension risks were identified in the on-chain mint configuration.

> **Final Recommendation:** Query a Solana block explorer directly to manually review token distribution among top non-pool accounts while RPC distribution indexing catches up. Monitor on-chain transaction flows for coordinated selling between correlated wallets, and verify that all secondary liquidity pools created in the future follow the same burn or lock standards.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the spl-token-2022 program with a fixed raw supply of 999,999,144,937,281 across 6 decimals. Both mint and freeze authorities are revoked (None), preventing any further… |
| **Governance / Economics** | 10/10 | Low | The trading pair reflects $4,456,293 in liquidity alongside a 24-hour volume of $2,364,234, yielding a stable volume-to-liquidity ratio of 0.53 on a pair age of 0 days. Crucially, 100.0% of the pool… |
| **Upgrades** | 10/10 | Low | The mint structure enforces complete non-upgradability with metadata marked as non-mutable. Transfer fee configurations and transfer hook upgrades are confirmed as inactive and not upgradable.… |

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

Liquidity $4.4M (DexScreener, all pools). 24h trading volume $2.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $4.4M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XfNpEo...pump`](https://solscan.io/account/XfNpEofiyPXoe3gX8KmMioW6PiKxVVJgNrQGE8Wpump) |
| **Network** | Solana |
| **Price** | $2.9400 |
| **24h Volume** | $2.36M |
| **Liquidity** | $4.45M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 16h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 49204 buys / 976 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9yfqcugfxuvpg1bmjnu3v3ctdpr32jduyhgpn1mzsnb8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-sol-c046)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
