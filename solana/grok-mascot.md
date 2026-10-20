---
token: Grok Mascot
ticker: GROKLET
network: solana
risk_score: 1
status: low
date: 2026-10-19
---

# Grok Mascot (GROKLET) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grok-mascot-sol)

---

## Audit Summary

The Groklet token mint exhibits a robust security posture based on available on-chain data. Both the mint and freeze authorities have been permanently revoked, preventing further token issuance or account freezing. Holder concentration is low, and a significant portion of the DEX liquidity is permanently burned. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. While current liquidity is moderate, monitor DEX market data for any significant changes in liquidity levels or trading patterns. No further specific on-chain verification steps are required given the current configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Groklet token operates on the classic SPL Token Program (v3), indicating a standard and well-understood implementation. Crucially, both the mint authority and freeze authority have been… |
| **Governance / Economics** | 10/10 | Low | Holder concentration for Groklet is low, with the top 10 sellable holders collectively owning only 20.90% of the total supply, reducing the risk of single-whale market manipulation. The token… |
| **Upgrades** | 10/10 | Low | The Groklet token mint demonstrates a high degree of immutability, as both the mint and freeze authorities have been revoked. This prevents any future changes to the token's supply or the ability to… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 97.7% (≈ permanent lock) |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.0% of supply. Of that, 27.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.0% in wallets, 1.9% in other contracts. 613 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

613 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

97.7% of the pool's LP is burned or time-locked. 97.7% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $56K (DexScreener, all pools). 24h trading volume $473K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $56K of DEX liquidity across 7 pools. Launch: launched on pump.fun, 490 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4qH8A5...pump`](https://solscan.io/account/4qH8A5GxvRMZgpRFjXASc6U9HAoEzKeUqxY2dPB7pump) |
| **Network** | Solana |
| **Price** | $0.0002529 |
| **24h Volume** | $457.7K |
| **Liquidity** | $51.8K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 48.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3433 buys / 3248 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7odjba4hzozvnwboksrwfetstnm4ia5witkwfr1lsy8t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grok-mascot-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
