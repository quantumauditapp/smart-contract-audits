---
token: Evrynth
ticker: EVYN
network: solana
risk_score: 28
status: low
date: 2026-10-21
---

# Evrynth (EVYN) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/evrynth-sol)

---

## Audit Summary

Evrynth (EVYN) is a Token-2022 asset with both mint and freeze authorities successfully revoked. The project demonstrates moderate holder concentration and sufficient liquidity, with all pool liquidity permanently burned. No third-party risk registry flags were identified.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs, as they control over 50% of the supply. Given the moderate concentration, position sizing should be managed accordingly.

Verify the current holder distribution periodically using on-chain explorers to ensure that no single entity is accumulating a dominant share of the circulating supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or account freezing capabilities. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis shows the top 10 holders control 57.91% of the supply, which presents a moderate concentration risk. 7.6 External market data indicates $19,631 in liquidity, which is fully… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint as it lacks proxy patterns or upgradeable logic. Metadata and balance-mutating authorities are disabled, ensuring the token's core properties… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 57.91% of the supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor the top 10 holder addresses for unusual activity or large transfers to exchanges.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 57.9% of supply. What remains: 20.9% in wallets, 37.1% in other contracts. 131 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Evrynth (EVYN), rank #6486. 131 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $163K (CoinGecko, all markets, daily snapshot). 24h trading volume $176K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9m5hwL...pump`](https://solscan.io/account/9m5hwLG4brTyZkEhtKvkzgFAbA7YxVvwPY1XuSpupump) |
| **Network** | Solana |
| **Price** | $0.00006576 |
| **24h Volume** | $175.9K |
| **Liquidity** | $20.6K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 6d |
| **Top-10 Holders** | 57.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1247 buys / 1372 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6luersvtnqsbhhtxjtr346rvouazhtzbtwzvrbtn1llj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/evrynth-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
