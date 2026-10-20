---
token: Chatul
ticker: CHATUL
network: solana
risk_score: 43
status: medium
date: 2026-10-20
---

# Chatul (CHATUL) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chatul-sol)

---

## Audit Summary

The Chatul token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. The primary risks identified are related to low liquidity and suspicious trading volume patterns. Third-party risk registry data indicates no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the low liquidity, which may lead to significant slippage during trades. Monitor the token's volume-to-liquidity ratio over time to determine if the current trading activity is sustainable or indicative of artificial inflation.

Verify the current supply and holder distribution via a block explorer to ensure no single entity accumulates a dominant position. Do not rely on the token for large-scale transactions until liquidity depth improves significantly.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals a high volume-to-liquidity ratio of 37.42, indicating potential wash trading. 7.6 External market data shows liquidity is $7,818, which is below the $10,000 threshold.… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not support proxy-based logic updates. Metadata is immutable, and extension configurations such as transfer fees are not upgradable. The token… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,818. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 37.42x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading patterns for organic growth before committing capital.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $352K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.7% of supply. Of that, 51.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.9% in wallets, 0.0% in other contracts. 453 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

453 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 29 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8kh7mP...pump`](https://solscan.io/account/8kh7mPfHqF4TBbszY3x76GZzt6a3GNLbZNdXjPs3pump) |
| **Network** | Solana |
| **Price** | $0.00001121 |
| **24h Volume** | $351.2K |
| **Liquidity** | $8.1K |
| **Volume / Liquidity** | 43.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 73.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3090 buys / 2788 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/avpxmiacxfrtznxlor3irexahhr7sg7cw9gmhjx73xsz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chatul-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
