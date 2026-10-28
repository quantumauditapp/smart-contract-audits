---
token: Top Floor
ticker: WORKR
network: solana
risk_score: 24
status: low
date: 2026-10-28
---

# Top Floor (WORKR) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/top-floor-sol)

---

## Audit Summary

The Top Floor (WORKR) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits signs of wash trading and very low liquidity, which poses significant execution risks. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise extreme caution due to the very low liquidity, which will cause significant slippage on even small trade sizes. Monitor the asset for sustained organic volume before considering participation.

Verify that the mint and freeze authorities remain null by inspecting the mint account on a block explorer. Do not rely on the reported 24-hour volume as a proxy for market interest, given the high volume-to-liquidity ratio.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors are concerning due to a liquidity of $2,479, which is below the $10,000 threshold. 7.6 External signals indicate a volume/liquidity ratio of 242.41, suggesting artificial trading… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is static and cannot be modified… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,479. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure trade sizes are significantly smaller than the available liquidity pool to avoid price impact.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 242.41x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity often indicates non-organic market activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $456K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ESvM3L...pump`](https://solscan.io/account/ESvM3LJuJD7d94nR2KRRfCSsKsgtUhbPe9u38z7vpump) |
| **Network** | Solana |
| **Price** | $0.00007904 |
| **24h Volume** | $419.2K |
| **Liquidity** | $22.9K |
| **Volume / Liquidity** | 18.3× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19805 buys / 7079 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/54mmgppaflumynmsbwei1yj3hwtogh71kncfsv5hwbwg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/top-floor-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
