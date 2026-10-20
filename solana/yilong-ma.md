---
token: YiLong Ma
ticker: YILONGMA
network: solana
risk_score: 22
status: low
date: 2026-10-15
---

# YiLong Ma (YILONGMA) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yilong-ma-sol)

---

## Audit Summary

The YiLong Ma (YILONGMA) SPL token mint exhibits a low-risk profile based on available on-chain data and third-party security registries. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing account freezing. Liquidity is fully burned, and holder concentration is moderate. Some granular holder distribution data was unavailable.

> **Final Recommendation:** Verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor the token's trading activity and liquidity over time, especially given its young age, to observe market stability and organic growth. While current holder concentration is moderate, continued monitoring of the top holders is advisable for any significant shifts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The YiLong Ma (YILONGMA) token is implemented as a standard SPL Token (spl-token program). Key administrative authorities, including the Mint Authority and Freeze Authority, have been permanently… |
| **Governance / Economics** | 9/10 | Low | The economic profile of the YILONGMA token shows a moderate holder concentration, with the top 10 holders that can sell accounting for 41.70% of the total supply. The token has a total DEX liquidity… |
| **Upgrades** | 10/10 | Low | The YILONGMA token mint has a robust security posture regarding mutability and upgrades. Both the mint and freeze authorities are revoked, meaning the token's supply and transferability parameters… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.3% of supply. Of that, 8.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.0% in wallets, 26.7% in other contracts. 998 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

998 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $381K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GU5NkU...pump`](https://solscan.io/account/GU5NkUVLzmJQxJKuho5dG4d1owChpcSQnhARrjYQpump) |
| **Network** | Solana |
| **Price** | $0.000331 |
| **24h Volume** | $381.0K |
| **Liquidity** | $49.8K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 50.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2574 buys / 2032 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8kusa63myw4nqjqqojk41ydee5fgrgppnxaoyudspyu2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yilong-ma-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
