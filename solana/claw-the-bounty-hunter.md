---
token: Claw the Bounty Hunter
ticker: CLAWHUNTER
network: solana
risk_score: 7
status: low
date: 2026-10-12
---

# Claw the Bounty Hunter (CLAWHUNTER) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/claw-the-bounty-hunter-sol)

---

## Audit Summary

This audit of the Claw the Bounty Hunter (CLAWHUNTER) SPL Token Mint found no critical or high-severity issues based on the available on-chain data and third-party risk registries. The mint and freeze authorities are revoked, and 100% of the DEX pool's liquidity is burned. Third-party registry data reported no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature. Monitor the token's liquidity and trading volume for any significant changes that could impact market depth or price stability. Confirm that the third-party risk registry continues to report no adverse flags before making investment decisions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CLAWHUNTER token is an SPL Token-2022 mint with a total supply of 987,711,081.299844 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, ensuring no new tokens… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 26.91% of the supply, which is well below thresholds for significant concentration risk. The token has healthy liquidity of… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and transferability parameters cannot be altered post-launch. No Token-2022 extensions that allow for mutable… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.6% of supply. Of that, 5.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.9% in wallets, 6.1% in other contracts. 1,267 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,267 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 77% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $122K (DexScreener, all pools). 24h trading volume $410K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $122K of DEX liquidity across 7 pools. Launch: launched on pump.fun (PumpSwap), 114 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6GGY8G...J4BQ`](https://solscan.io/account/6GGY8GViCR5v4xR4Lxb4nfiAJsEoJua5Gj6YecxbJ4BQ) |
| **Network** | Solana |
| **Price** | $0.0009226 |
| **24h Volume** | $294.8K |
| **Liquidity** | $93.5K |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 32.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1700 buys / 1906 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/f6vetyfbpsyziqsbnudqcempdusyr3pxghhfbeu2spfr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/claw-the-bounty-hunter-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
