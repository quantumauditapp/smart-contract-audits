---
token: Pog
ticker: POG
network: solana
risk_score: 36
status: medium
date: 2026-11-03
---

# Pog (POG) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pog-sol)

---

## Audit Summary

The Pog token is a Token-2022 asset with both mint and freeze authorities successfully revoked. The primary risks identified are very low liquidity and a high volume-to-liquidity ratio suggesting potential wash trading. Holder concentration data was unavailable from the source.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity, which will cause significant slippage on even modest sell orders. Monitor the token on block explorers to ensure no unexpected changes occur, though the current immutable settings make this unlikely.

Verify market activity independently, as the high volume-to-liquidity ratio suggests that reported trading volume may not reflect genuine organic demand. Avoid large positions that cannot be exited without incurring substantial price impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program, which supports advanced extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as both… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high risk due to low liquidity ($7,613) and a volume/liquidity ratio of 65.79. 7.6 External signals confirm the liquidity is fully burned, preventing… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades and 7.8 Operations are secure as metadata and extension parameters are immutable. The token cannot be modified post-launch, ensuring consistent behavior for all holders. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,613. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 65.79x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Verify trading activity through independent market analysis.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $580K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 13 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`JcPLcB...pump`](https://solscan.io/account/JcPLcB4WN61b2i6cZctiXW2R9AYCAKCQo6tqFVNpump) |
| **Network** | Solana |
| **Price** | $0.00001451 |
| **24h Volume** | $491.9K |
| **Liquidity** | $8.5K |
| **Volume / Liquidity** | 57.7× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9758 buys / 8358 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/78fdpskq7lxalypn953ekgyruhjq1xsalxf7eg8t8g9q)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
