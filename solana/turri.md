---
token: Turri
ticker: TURRI
network: solana
risk_score: 28
status: low
date: 2026-10-23
---

# Turri (TURRI) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/turri-sol)

---

## Audit Summary

The Turri token (TURRI) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the token architecture is secure regarding administrative control, the asset exhibits high-risk trading characteristics, specifically very low liquidity and a high volume-to-liquidity ratio indicative of potential wash trading. All sources were successfully retrieved for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity environment, which may prevent the execution of large sell orders without significant price impact. Monitor the asset for sustained organic volume rather than relying on current high-frequency trading metrics.

Verify the current liquidity pool status on-chain to ensure no new pools have been created with different locking parameters. Avoid placing market orders that exceed a small fraction of the total pool liquidity to minimize slippage losses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program, ensuring modern extension capabilities. 7.1 Architecture and 7.2 Code Security are standard for SPL mints, with no transfer hooks or custom logic… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics reveal significant volatility risks. Liquidity is limited to $7,344, triggering a high-risk classification for market depth. The volume-to-liquidity ratio of… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, and no authority exists to modify token parameters. The configuration is fixed at the protocol level. |

## Security Findings

_🟠 2 High · ⚪ 6 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,344. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth before entering or exiting positions.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 97.34x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume in low-liquidity pools is often non-organic.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 45.0% of supply. Of that, 24.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.7% in wallets, 0.0% in other contracts. 678 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

678 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $794K (DexScreener, all pools).

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
| **Contract** | [`DqYemN...pump`](https://solscan.io/account/DqYemNm4ez4Epxgjgws74NpyGAaddgTyQQercSgpump) |
| **Network** | Solana |
| **Price** | $0.0000244 |
| **24h Volume** | $708.5K |
| **Liquidity** | $12.2K |
| **Volume / Liquidity** | 58.2× |
| **Token Age** | 22h |
| **Top-10 Holders** | 45.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8164 buys / 8232 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c4vh5sgdamzscawrnsduwf7vbjydkeduzgg8tcm9fgo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/turri-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
