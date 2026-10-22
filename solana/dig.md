---
token: DIG
ticker: DIG
network: solana
risk_score: 14
status: low
date: 2026-10-22
---

# DIG (DIG) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dig-sol)

---

## Audit Summary

The DIG token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. While liquidity is fully burned, the token is flagged by a third-party registry for single-holder ownership, and liquidity levels are currently below the $10,000 threshold. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the liquidity pool for growth, as the current sub-$10,000 level may lead to high slippage during trades. Given the third-party registry flag regarding single-holder ownership, users should exercise caution regarding potential concentration risks even if the token contract itself is secure.

Verify the current holder distribution using block explorers to ensure that the 'single holder' flag does not represent a risk of immediate dumping. Since the mint and freeze authorities are revoked, no further changes to the token's core mechanics are possible, providing a stable technical foundation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer… |
| **Governance / Economics** | 9/10 | Low | Liquidity is fully burned, preventing withdrawal by the creator (7.4 Economic). However, current liquidity is $9,993, which falls below the $10,000 safety threshold (7.6 External). Trading volume is… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns in the SPL Token-2022 architecture. Authority… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,993. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Monitor liquidity growth before executing large trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $181K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7BZBP5...pump`](https://solscan.io/account/7BZBP5Tm5mHAtgMF3qKF5aBeE8eM8cqQdNWgFmSDpump) |
| **Network** | Solana |
| **Price** | $0.00002432 |
| **24h Volume** | $86.7K |
| **Liquidity** | $11.6K |
| **Volume / Liquidity** | 7.5× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1877 buys / 1175 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/haznm3sqqgxdsd48nkdufpm27zcd9egfr5wa8kb62lrr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dig-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
