---
token: chrome
ticker: CHROME
network: solana
risk_score: 23
status: low
date: 2026-10-22
---

# chrome (CHROME) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chrome-sol)

---

## Audit Summary

The CHROME token is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise caution regarding the high trading volume, which may not reflect genuine market demand. Monitor the token on block explorers to ensure no unexpected changes occur in the token program state.

Verify the current holder distribution once on-chain registry data becomes available to assess the risk of concentrated sell-offs. Do not rely solely on DEX volume metrics when evaluating the asset's liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture is standard for SPL mints, while 7.3 Access Control is robust as both mint and freeze authorities… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows 100% of liquidity is burned, preventing rug pulls via withdrawal. However, 7.6 External signals indicate a volume/liquidity ratio of 108.98, which is significantly above… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL mint as it is a fixed-state asset. 7.8 Operations are secure because metadata is immutable and no upgradeable extensions are enabled. The token… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 108.98, which exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`E7DTr6...MUZ2`](https://solscan.io/account/E7DTr6RANsHApnidgGT1VqzAJKcqYXBEvf2QeyvJMUZ2) |
| **Network** | Solana |
| **Price** | $0.00002181 |
| **24h Volume** | $1.22M |
| **Liquidity** | $12.0K |
| **Volume / Liquidity** | 101.8× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12767 buys / 9779 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8uy2d5riwkf4ir8lzvx7pvnwd8smiivjc1u9zd1s7tqs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chrome-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
