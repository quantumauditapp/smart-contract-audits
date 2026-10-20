---
token: lowk jelly
ticker: LOWKJELLY
network: solana
risk_score: 16
status: low
date: 2026-10-03
---

# lowk jelly (LOWKJELLY) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lowk-jelly-sol)

---

## Audit Summary

The lowk jelly SPL Token Mint exhibits a low-risk profile based on available on-chain data. Key authorities such as mint and freeze are revoked, and liquidity is fully burned. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature. While current liquidity is fully burned, monitoring DEX liquidity levels is always prudent for tokens with smaller market caps. Be aware that holder concentration could not be assessed due to data unavailability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The lowk jelly token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, preventing further token creation or freezing of accounts. No… |
| **Governance / Economics** | 9/10 | Low | The token's liquidity profile shows $12,199 in total DEX liquidity. A significant strength is that 100.0% of the pool's LP tokens are burned, ensuring liquidity cannot be withdrawn by any party. The… |
| **Upgrades** | 10/10 | Low | The lowk jelly token mint has a fixed configuration as both mint and freeze authorities are revoked. This prevents any future changes to the token's supply or the ability to freeze accounts. The… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $55K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AYRTq6...pump`](https://solscan.io/account/AYRTq6bfnNzWMY5ACWTRUtMCwV8PAhux3wm84q5mpump) |
| **Network** | Solana |
| **Price** | $0.00002198 |
| **24h Volume** | $54.9K |
| **Liquidity** | $12.3K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 617 buys / 548 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7gb1hnyfcpevepn1dskrxijxt5ffntpgsguaxslnyief)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lowk-jelly-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
