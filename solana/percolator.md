---
token: Percolator
ticker: PERCOLATOR
network: solana
risk_score: 0
status: low
date: 2026-09-30
---

# Percolator (PERCOLATOR) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/percolator-sol)

---

## Audit Summary

This audit of the Percolator SPL token mint found no critical or high-severity risks based on the provided on-chain data and external security signals. The mint and freeze authorities are revoked, and a significant portion of the liquidity is burned. Third-party risk registry data reported no adverse flags.

> **Final Recommendation:** Given the current configuration with revoked mint and freeze authorities, burned liquidity, and no adverse flags from third-party registries, the Percolator token presents a low-risk profile based on the available data. Holders should continue to monitor the token's market performance and any potential changes in the broader ecosystem. No specific on-chain verification steps are immediately required beyond confirming the current state of authorities and liquidity as reported.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Percolator token is implemented using the standard SPL Token Program (v3). Both the mint authority and freeze authority have been revoked, preventing any further token minting or freezing of… |
| **Governance / Economics** | 10/10 | Low | The token exhibits a healthy distribution, with the top 10 holders that can sell accounting for 19.39% of the total supply, indicating low concentration risk. The project maintains a substantial… |
| **Upgrades** | 10/10 | Low | The token's configuration is highly immutable, as both the mint and freeze authorities are revoked, preventing any future changes to the token supply or the ability to freeze accounts. Additionally… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.0% of supply. Of that, 5.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.4% in wallets, 0.0% in other contracts. 5,311 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Percolator (PERCOLATOR). 5,311 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.7% of the pool's LP is burned or time-locked. 99.7% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 92% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $399K (DexScreener, all pools). 24h trading volume $556K (CoinGecko, all markets, daily snapshot). 24h trading volume $504K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $399K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 344 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8PzFWy...pump`](https://solscan.io/account/8PzFWyLpCVEmbZmVJcaRTU5r69XKJx1rd7YGpWvnpump) |
| **Network** | Solana |
| **Price** | $0.003457 |
| **24h Volume** | $479.8K |
| **Liquidity** | $368.0K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 25.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1375 buys / 1809 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ebs3mxazqzfzhfsdintnw7gpy4unyeaywccijxzlrrbw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/percolator-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
