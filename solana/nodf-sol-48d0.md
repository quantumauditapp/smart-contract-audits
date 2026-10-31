---
token: NODF
ticker: NODF
network: solana
risk_score: 38
status: medium
date: 2026-10-31
---

# NODF (NODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nodf-sol-48d0)

---

## Audit Summary

The NODF token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits signs of wash trading with a high volume-to-liquidity ratio and low total liquidity. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise caution due to the low liquidity and high volume-to-liquidity ratio, which may indicate artificial trading activity. Before interacting, verify the current liquidity depth on the DEX to ensure the position size does not exceed the slippage tolerance.

Monitor the token's market activity for sustained organic volume. As the mint and freeze authorities are revoked, the token's supply and transfer mechanics are fixed, reducing the risk of administrative intervention.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals low liquidity of $9,183, creating significant slippage risks. 7.6 External market data indicates a volume/liquidity ratio of 186.39, suggesting potential wash trading.… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, and no upgradeable extensions are active. The configuration is locked, providing high assurance… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,183. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation and avoid large market orders.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 186.39x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity often indicates non-organic market activity.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $1.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`QgKzyh...pump`](https://solscan.io/account/QgKzyhRDqf4D8xLF6jiQygZ8n8rRp6RwaYUb1Zmpump) |
| **Network** | Solana |
| **Price** | $0.00001721 |
| **24h Volume** | $1.71M |
| **Liquidity** | $9.2K |
| **Volume / Liquidity** | 186.4× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19266 buys / 1056 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9beleysntwm2fn365ljqqod8mgbvkzoxwmcl5k5nf3op)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nodf-sol-48d0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
