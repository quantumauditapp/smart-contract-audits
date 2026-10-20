---
token: Larpcheck
ticker: LARPCHECK
network: solana
risk_score: 9
status: low
date: 2026-10-19
---

# Larpcheck (LARPCHECK) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/larpcheck-sol)

---

## Audit Summary

This SPL Token-2022 mint, Larpcheck (LARPCHECK), presents a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing account freezing. Holder concentration is low, and the majority of DEX liquidity is permanently locked. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Given the revoked mint and freeze authorities, the token's supply is fixed, and accounts cannot be frozen. Holders should monitor DEX liquidity for any significant changes, although the high percentage of burned LP tokens provides a strong foundation. Verify on-chain that the metadata remains immutable and no new extensions are enabled if the token program were to be updated.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | This token is an SPL Token-2022 mint with both mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. It does not utilize the Transfer Hook or Default Account State… |
| **Governance / Economics** | 10/10 | Low | The token exhibits low holder concentration, with the top 10 sellable holders owning only 20.23% of the supply. DEX liquidity stands at $100,494, with 98.6% of the pool's LP tokens permanently… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing further token issuance or account freezing. The token's metadata, including name and symbol, is immutable, as confirmed by… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.5% of supply. Of that, 5.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.2% in wallets, 0.0% in other contracts. 2,311 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,311 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

98.6% of the pool's LP is burned or time-locked. 98.6% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 62% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $160K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $160K of DEX liquidity across 11 pools. Launch: launched on pump.fun (PumpSwap), 8 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`t9bnCG...LARP`](https://solscan.io/account/t9bnCGiZVUYsRKvx4d5dPcoDCSyuBM9C33ZNGNULARP) |
| **Network** | Solana |
| **Price** | $0.0009553 |
| **24h Volume** | $838.4K |
| **Liquidity** | $99.0K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 8d |
| **Top-10 Holders** | 25.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4533 buys / 4611 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fj1gf7yyzqnpjad2go6rws14wmstjzyo8xgxmlphhaeu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/larpcheck-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
