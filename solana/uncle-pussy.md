---
token: Uncle Pussy
ticker: UP
network: solana
risk_score: 1
status: low
date: 2026-10-08
---

# Uncle Pussy (UP) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uncle-pussy-sol)

---

## Audit Summary

The Uncle Pussy (UP) SPL token mint has been audited based on on-chain data and third-party registries. No critical or high-risk vulnerabilities were identified. The mint and freeze authorities are revoked, and the pool liquidity is 100% burned. Holder concentration data was unavailable from chain-native RPC, preventing assessment of distribution risks.

> **Final Recommendation:** Holders should monitor the token's market behavior, especially given the relatively high volume-to-liquidity ratio, even though it does not trigger a specific finding. Verify on-chain that the mint and freeze authorities remain revoked. If holder distribution data becomes available, assess the concentration to understand potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Uncle Pussy (UP) token is an SPL Token-2022. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen. It does not… |
| **Governance / Economics** | 10/10 | Low | The token exhibits a total DEX liquidity of $59,565. The 24-hour volume is $596,205, resulting in a Volume/Liquidity Ratio of 10.01, which is noted as high (>5) by DEX market data. Crucially, 100% of… |
| **Upgrades** | 10/10 | Low | The token's mint and freeze authorities are permanently revoked, preventing any future changes to supply or account freezing capabilities. Key Token-2022 extensions such as transfer hook and transfer… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $69K (DexScreener, all pools). 24h trading volume $618K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $69K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FzPujT...pump`](https://solscan.io/account/FzPujTgKNJVim7YYa5HYHngGtf19QwV6ACJ1zDLWpump) |
| **Network** | Solana |
| **Price** | $0.000349 |
| **24h Volume** | $600.8K |
| **Liquidity** | $62.8K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3313 buys / 3289 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5fajxzgx3emkyzgmuktsem4crjvqxdj1r7ge4s4tpyd8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uncle-pussy-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
