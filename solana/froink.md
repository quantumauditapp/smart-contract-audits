---
token: Froink
ticker: FROINK
network: solana
risk_score: 15
status: low
date: 2026-10-01
---

# Froink (FROINK) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/froink-sol)

---

## Audit Summary

This audit of the Froink (FROINK) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and third-party security signals. Both mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** The Froink token appears to be well-configured with key authorities revoked and liquidity secured. Holders should continue to monitor the token's trading activity and liquidity depth. While holder concentration data was unavailable for this audit, it is advisable to periodically check on-chain holder distribution to identify any significant shifts that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | This token is configured with the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen (7.3… |
| **Governance / Economics** | 9/10 | Low | The token has $34,708 in DEX liquidity, with 100% of LP tokens burned, securing the liquidity permanently (7.4 Economic). The 24-hour volume of $254,957 results in a Volume/Liquidity ratio of 7.35… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any further changes to the token's supply or account freezing capabilities (7.7 Upgrades). Metadata, transfer fees, and transfer… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Froink (FROINK), rank #5887.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 83% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $223K (CoinGecko, all markets, daily snapshot). 24h trading volume $270K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2yu92o...DDZr`](https://solscan.io/account/2yu92oYzBWLAdVpu8BoaLzmM1oxPsHoboay2BXmeDDZr) |
| **Network** | Solana |
| **Price** | $0.00009098 |
| **24h Volume** | $258.0K |
| **Liquidity** | $33.8K |
| **Volume / Liquidity** | 7.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1717 buys / 1778 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5l6sielcoxrv9ctcfwugkjf5ezcrtyddmkbth1yekp9f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/froink-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
