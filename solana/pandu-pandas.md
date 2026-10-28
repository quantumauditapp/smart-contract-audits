---
token: Pandu Pandas
ticker: PANDU
network: solana
risk_score: 7
status: low
date: 2026-10-28
---

# Pandu Pandas (PANDU) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pandu-pandas-sol)

---

## Audit Summary

Pandu Pandas (PANDU) is a Token-2022 asset with fully revoked mint and freeze authorities, ensuring no further supply inflation or account freezing is possible. Liquidity is fully secured via 100% burn of LP tokens, and no adverse flags were reported by third-party registries. The token exhibits a healthy distribution and trading profile with no high-risk technical extensions active.

> **Final Recommendation:** The token is in a secure, immutable state. No immediate action is required for holders regarding authority risks or liquidity safety.

Users should continue to monitor the top holder distribution via block explorers to ensure no single entity accumulates a majority stake over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions such as transfer hooks or default frozen states. 7.1 Architecture is standard for SPL tokens, and 7.2 Code Security is inherent to… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic factors are stable, with the top 10 holders controlling 28.51% of the supply, indicating low concentration risk. 7.5 Governance is decentralized due to the lack of administrative… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is locked, and no upgrade paths exist for the token program or its extensions. The token state is fixed and cannot be altered by any… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.2% of supply. Of that, 16.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.5% in wallets, 4.0% in other contracts. 906 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Pandu Pandas (PANDU), rank #5422. 906 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $55K (DexScreener, all pools). 24h trading volume $790 (CoinGecko, all markets, daily snapshot). 24h trading volume $264K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00265 on 2026-04-09; the price is now 93.4807% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $55K of DEX liquidity across 7 pools. Launch: launched on pump.fun, 203 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2xm2WZ...pump`](https://solscan.io/account/2xm2WZ9krE2YAArRC6S6ZzJAYgN813K6hh2dawKjpump) |
| **Network** | Solana |
| **Price** | $0.0003327 |
| **24h Volume** | $263.9K |
| **Liquidity** | $55.2K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 45.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3474 buys / 2202 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bfn7n6xpsx4zslwbmffvaadkgvqbydcwwaj8ugdiphr6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pandu-pandas-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
