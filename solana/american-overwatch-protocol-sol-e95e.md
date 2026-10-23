---
token: American Overwatch Protocol
ticker: AOP
network: solana
risk_score: 0
status: low
date: 2026-10-23
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-sol-e95e)

---

## Audit Summary

The American Overwatch Protocol (AOP) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and metadata is immutable. While a third-party registry flags high holder correlation, the token exhibits no critical technical vulnerabilities.

> **Final Recommendation:** The token is technically sound regarding authority management and liquidity security. Holders should monitor the 'High holder correlation' flag reported by third-party registries to ensure that the low concentration does not shift significantly over time.

Verify the current supply and authority status directly via a block explorer to confirm that no unexpected changes have occurred since this audit. No further technical intervention is required for standard holding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics show low concentration, with the top 10 holders controlling only 1.81% of the supply. 7.6 External data confirms 100% of pool liquidity is burned, preventing… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the immutable nature of the mint. Metadata is fixed and cannot be altered, preventing branding deception. The token configuration is final and cannot… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the circulating supply may be controlled by related entities.

**Recommendation:** Monitor on-chain wallet movements to identify potential coordinated sell-offs by related holders.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $90K (DexScreener, all pools). 24h trading volume $160K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $90K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`25X5iC...pump`](https://solscan.io/account/25X5iC9VQY1yJhVTtfrXY1RVwocLrCQPaTBPnstApump) |
| **Network** | Solana |
| **Price** | $0.001128 |
| **24h Volume** | $160.4K |
| **Liquidity** | $89.6K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21346 buys / 9488 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6eagmvh6scwgfwdpbgduwzvryvjpehkxek4ob742w337)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-sol-e95e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
