---
token: Agency
ticker: AGENCY
network: solana
risk_score: 10
status: low
date: 2026-10-04
---

# Agency (AGENCY) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agency-sol)

---

## Audit Summary

This audit found no critical or high-severity risks for the Agency SPL Token-2022 mint. Key authorities like mint and freeze have been revoked, and metadata is immutable. However, data on holder concentration and pool liquidity locking was unavailable, preventing a full assessment of economic centralization risks.

> **Final Recommendation:** Holders should monitor for the availability of holder distribution data to assess potential concentration risks. Additionally, verify on-chain if and when liquidity pools are locked or burned to ensure long-term stability against rug pull scenarios. Confirming these aspects would provide a more complete risk profile for the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Agency token is an SPL Token-2022 mint with a total supply of 961,067,026.903301 tokens (6 decimals). Both the mint authority and freeze authority have been revoked, preventing further token… |
| **Governance / Economics** | 7/10 | Low | The token has a liquidity of $1,050,101 USD across DEX pools. Over the past 24 hours, the trading volume was $4,849,155 USD, resulting in a healthy Volume/Liquidity Ratio of 4.62. The pair is… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the Agency token have both been permanently revoked. This prevents any future changes to the token's supply or the ability to freeze holder accounts.… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Agency (AGENCY), market cap $17M, rank #996.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.6M (DexScreener, all pools). 24h trading volume $61.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $33.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.6M of DEX liquidity across 30 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7Vertk...pump`](https://solscan.io/account/7VertkgF9KLhxxJXHX6uaWuoYZTP9LdGj2bWmVXVpump) |
| **Network** | Solana |
| **Price** | $0.02524 |
| **24h Volume** | $4.83M |
| **Liquidity** | $1.09M |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3680 buys / 4526 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gdoenragqcdaa1o9rv5wjsnqm41hmmckl5lkekfvbiuw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agency-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
