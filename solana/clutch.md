---
token: Clutch
ticker: CLUTCH
network: solana
risk_score: 21
status: low
date: 2026-10-29
---

# Clutch (CLUTCH) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clutch-sol)

---

## Audit Summary

The Clutch (CLUTCH) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading. Holder distribution data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may not reflect organic market demand. Monitor the token on-chain to ensure no unexpected changes occur, though the current revocation status makes this unlikely.

Verify the token mint address against official project channels before interacting. Given the lack of holder distribution data, avoid large position entries that could be subject to high slippage despite the burned liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control).… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured with 100% of LP tokens burned, preventing creator withdrawal (7.4 Economic). However, the volume-to-liquidity ratio of 61.38 significantly exceeds the 20x threshold… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns present (7.8 Operations). The mint state is finalized… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 61.38, which is significantly higher than the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of organic growth versus automated volume generation before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AHtLsp...Xhot`](https://solscan.io/account/AHtLsp84S3ThHeNgcqg1jXaE9M6FSXKW8oj7WjYkXhot) |
| **Network** | Solana |
| **Price** | $0.00003738 |
| **24h Volume** | $1.22M |
| **Liquidity** | $17.6K |
| **Volume / Liquidity** | 69.0× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9656 buys / 8221 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cgy9pe7j76wky98ej3g4us5rmzx6caztcmm5zu8ueu41)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/clutch-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
