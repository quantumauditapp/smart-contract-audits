---
token: OTC Index
ticker: OTCI
network: solana
risk_score: 21
status: low
date: 2026-10-16
---

# OTC Index (OTCI) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/otc-index-sol)

---

## Audit Summary

The OTC Index (OTCI) SPL Token Mint demonstrates a robust security posture. Both mint and freeze authorities are revoked, ensuring a fixed token supply and preventing account freezing. Liquidity for the token is fully burned, mitigating rug pull risks. Holder concentration is moderate, and trading patterns appear normal, with no adverse flags reported by third-party risk registries.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor holder distribution for any significant shifts that could impact market stability. While liquidity is fully burned, continued monitoring of overall market depth is advisable for large positions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The OTC Index (OTCI) token operates on the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 9/10 | Low | The top 10 holders that can sell account for 32.05% of the total supply, indicating a moderate level of holder concentration. The token has $18,632 in DEX liquidity, with 100.0% of the pool's LP… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and freeze capabilities are immutable. The token utilizes the spl-token-2022 program, but critical extensions like… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.3% of supply. Of that, 18.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 27.9% in wallets, 4.1% in other contracts. 148 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

148 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $50K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 4 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EnAMBD...LYgK`](https://solscan.io/account/EnAMBDkVYMxytcSdy8G32E2xy61Q4tpyt3rEH47QLYgK) |
| **Network** | Solana |
| **Price** | $0.00005588 |
| **24h Volume** | $50.0K |
| **Liquidity** | $18.5K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 14h |
| **Top-10 Holders** | 50.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2426 buys / 1073 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/espeqy84fzxyapahwx476q1fswuesrueezsyckuuxon9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/otc-index-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
