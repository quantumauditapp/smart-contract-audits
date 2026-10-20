---
token: NPCs
ticker: NPC
network: solana
risk_score: 0
status: low
date: 2026-09-29
---

# NPCs (NPC) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/npcs-sol)

---

## Audit Summary

The audit of the NPCs (NPC) SPL Token Mint reveals a Medium overall risk level, primarily due to the very recent launch of its DEX pair. Key technical controls, such as mint and freeze authorities, are appropriately revoked. However, holder distribution data was unavailable, preventing a full assessment of supply concentration risk.

> **Final Recommendation:** Prospective holders should monitor the token's market activity closely, particularly its trading volume and liquidity, as the pair is very new. It is crucial to verify on-chain that the mint and freeze authorities remain revoked to ensure the token's supply and transferability are not subject to unilateral changes. Future assessments would benefit from complete holder distribution data to assess concentration risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The NPCs (NPC) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, preventing further token creation or freezing of holder accounts.… |
| **Governance / Economics** | 10/10 | Low | The token's DEX pair is very new, having been created only 5 days ago, which limits the track record for assessing market behavior. Current liquidity stands at $55,812, with a 24-hour volume of… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both the mint and freeze authorities are revoked. No Token-2022 extensions that allow for upgradability, such as transfer fee upgradability or transfer… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

The DEX pair was created 5 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution due to the token's nascent market presence. Monitor the token's performance and community activity over a longer period before making significant investments.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NPCs (NPC), rank #5089.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $63K (DexScreener, all pools). 24h trading volume $315K (CoinGecko, all markets, daily snapshot). 24h trading volume $403K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00492 on 2026-09-25; the price is now 95.8135% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $63K of DEX liquidity across 22 pools. Launch: launched on pump.fun, 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7GUnr7...pump`](https://solscan.io/account/7GUnr7krtQhJwd6ASY2VUprd9t4c64zcgCsjdmZepump) |
| **Network** | Solana |
| **Price** | $0.0002318 |
| **24h Volume** | $372.2K |
| **Liquidity** | $56.8K |
| **Volume / Liquidity** | 6.6× |
| **Token Age** | 5d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3309 buys / 2814 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/brjma8ualnp3ditkhfdean5riqrypoayez7khywd4oes)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/npcs-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
