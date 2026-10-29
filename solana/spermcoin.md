---
token: spermcoin
ticker: SPERM
network: solana
risk_score: 40
status: medium
date: 2026-10-29
---

# spermcoin (SPERM) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spermcoin-sol)

---

## Audit Summary

The SPERM token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits a high volume-to-liquidity ratio of 107.69, indicating potential wash trading, and liquidity is very low at $8,667. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise extreme caution due to the very low liquidity and high volume-to-liquidity ratio, which may lead to significant slippage and difficulty in exiting positions. Monitor the token's trading activity on-chain to verify if volume remains consistent with genuine market interest.

Verify the current supply and authority status using a block explorer to ensure no unexpected changes have occurred. Given the lack of holder concentration data, maintain small position sizes to mitigate the impact of potential whale activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is deployed via the spl-token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the SPL… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics show significant volatility risks. Liquidity is limited to $8,667, which is below the $10,000 threshold for stable trading. 7.6 External market data reveals a… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once authorities are revoked. Metadata is immutable, and no upgradeable extensions are present. The token configuration is finalized… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,667, which is below the $10,000 threshold. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure position sizes are significantly smaller than the available liquidity pool to avoid excessive price impact.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 107.69, which is well above the 20x threshold, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume relative to liquidity often indicates non-organic trading activity.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 20 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9JrZq5...RJW6`](https://solscan.io/account/9JrZq5wzwsqzeA1jmXZ8bg7PVGzT8asuKe1TkrsWRJW6) |
| **Network** | Solana |
| **Price** | $0.00001376 |
| **24h Volume** | $932.1K |
| **Liquidity** | $9.3K |
| **Volume / Liquidity** | 100.2× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13214 buys / 10174 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dsvuktcbvxfqphb9fgxtcpg9rykuvbh3mod9cuxhmze)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spermcoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
