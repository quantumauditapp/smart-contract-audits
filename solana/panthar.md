---
token: Panthar
ticker: PANTHAR
network: solana
risk_score: 40
status: medium
date: 2026-11-03
---

# Panthar (PANTHAR) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/panthar-sol)

---

## Audit Summary

The Panthar token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits high-risk trading patterns, specifically a volume-to-liquidity ratio exceeding 77, which is indicative of potential wash trading. Holder concentration data was unavailable, and liquidity remains below the $10,000 threshold.

> **Final Recommendation:** Investors should exercise caution due to the low liquidity and high volume-to-liquidity ratio, which may lead to significant slippage and difficulty in exiting positions. Monitor the token's trading activity on-chain to verify if volume remains consistent or appears artificially inflated.

Verify the current supply and authority status using a block explorer to ensure no unexpected changes have occurred. Given the lack of holder distribution data, avoid large market orders that could be impacted by low liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account-level censorship (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is $9,211, which is below the $10,000 safety threshold (7.4 Economic). 100% of the pool liquidity is burned, preventing rug pulls via withdrawal (7.5 Governance). The 24h… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, and no upgradeable extensions are present (7.7 Upgrades). There are no administrative functions that allow for post-deployment logic changes (7.8 Operations). The… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,211. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth before executing large trades.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 77.94x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as the trading volume may not reflect genuine market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $829K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 22 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3MSE8H...mWkB`](https://solscan.io/account/3MSE8Ho8FwPrrof6Z2kadbD9sjtZYWWSrAAJrBnhmWkB) |
| **Network** | Solana |
| **Price** | $0.00001607 |
| **24h Volume** | $717.2K |
| **Liquidity** | $9.1K |
| **Volume / Liquidity** | 78.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10560 buys / 7738 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/atrhgp2nb5vas8cpqp9waslakjmtzqy4d6vczz8vfhr1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/panthar-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
