---
token: Digital Slop Coin
ticker: SLOP
network: solana
risk_score: 22
status: low
date: 2026-11-05
---

# Digital Slop Coin (SLOP) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/digital-slop-coin-sol)

---

## Audit Summary

Digital Slop Coin (SLOP) is a Token-2022 asset with fully revoked mint and freeze authorities, mitigating central control risks. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial market activity rather than organic demand. Monitor the token's liquidity depth on DEX platforms before executing large trades to avoid excessive slippage.

Verify the token mint address directly on a block explorer to ensure it matches the official contract address provided. Since holder concentration data is currently unavailable, perform independent analysis of the top token accounts if such data becomes accessible via public indexers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as both mint and… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show $11,544 in liquidity, which is fully burned, preventing rug pulls via liquidity withdrawal. 7.5 Governance is decentralized due to the lack of mint authority. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not support proxy patterns. Metadata is immutable, and extension configurations such as transfer fees and hooks are not upgradable. The token state is… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 219.02, which exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for potential liquidity gaps when trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $2.6M (DexScreener, all pools).

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
| **Contract** | [`6z3cf9...gajt`](https://solscan.io/account/6z3cf9nDuxdA9xyccx8m8SonWdZGH5s9kbqAeaV5gajt) |
| **Network** | Solana |
| **Price** | $0.00002286 |
| **24h Volume** | $2.52M |
| **Liquidity** | $12.6K |
| **Volume / Liquidity** | 200.2× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26426 buys / 19424 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fsrk3tjj7y3vfvsqje1dzrxep9uu6rksq1hkrjeonlka)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/digital-slop-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
