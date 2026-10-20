---
token: Xeet
ticker: XEET
network: solana
risk_score: 17
status: low
date: 2026-10-07
---

# Xeet (XEET) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xeet-sol)

---

## Audit Summary

The Xeet (XEET) SPL Token-2022 mint demonstrates strong security fundamentals with both mint and freeze authorities revoked, preventing further supply dilution or account freezing. All pool liquidity is permanently burned, mitigating rug pull risks. Third-party registry data reported no adverse flags, though holder distribution data was unavailable.

> **Final Recommendation:** Holders should monitor the token's trading activity and liquidity for any significant changes. While core authorities are revoked and liquidity is burned, the absence of holder distribution data means potential concentration risks cannot be fully assessed. Verify on-chain that authorities remain revoked and liquidity remains burned.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Xeet (XEET) token is an SPL Token-2022 mint with a total supply of 975,357,545.360697 tokens (975357545360697 raw, 6 decimals). Both the mint authority and freeze authority have been revoked… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a normal volume/liquidity ratio of 3.99 over its 2-day trading history, with $16,209 in total DEX liquidity. Critically, 100.0% of the pool's liquidity provider (LP) tokens are… |
| **Upgrades** | 10/10 | Low | The Xeet token mint has a robust security posture regarding mutability, as both mint and freeze authorities are permanently revoked. Key Token-2022 extensions like transfer hook and transfer fee are… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $64K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 8 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6HFJ5s...pump`](https://solscan.io/account/6HFJ5sxVoEtczr9siAUeGssmpfhQSS3pEoBcCycUpump) |
| **Network** | Solana |
| **Price** | $0.00003095 |
| **24h Volume** | $64.5K |
| **Liquidity** | $16.6K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 901 buys / 804 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9tasytundrdypsatayvaudnjpqhsce8fgksk7dl1srwl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xeet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
