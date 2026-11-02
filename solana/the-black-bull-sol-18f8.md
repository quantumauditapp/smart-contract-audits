---
token: The Black Bull
ticker: SLINGOOR
network: solana
risk_score: 17
status: low
date: 2026-11-02
---

# The Black Bull (SLINGOOR) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-black-bull-sol-18f8)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading, and third-party registry data indicates high holder concentration. Holder distribution data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate artificial market activity rather than organic demand. Given the high holder concentration reported by third-party registries, users should be aware of the risk of significant price volatility if large holders decide to divest.

Verify the current holder distribution using block explorers to assess the impact of top-wallet holdings on market liquidity. Ensure that any trading strategy accounts for the potential slippage inherent in the current liquidity pool size.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks… |
| **Governance / Economics** | 8/10 | Low | Liquidity is fully secured as 100% of LP tokens are burned (7.4 Economic). However, the 24h volume-to-liquidity ratio of 36.63 exceeds the 20x threshold, indicating potential wash trading (7.6… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding metadata and authority settings (7.7 Upgrades). There are no upgradeable components or proxy patterns (7.8 Operations). The configuration is finalized and cannot be… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 36.63, which is significantly above the 20x threshold, suggesting artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive, non-organic patterns.


### `M-01` — High Holder Concentration  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate high ownership concentration among the top 10 holders, increasing the risk of price manipulation.

**Recommendation:** Monitor top holder wallet activity for signs of coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $2.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $100K of DEX liquidity across 29 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9rZR9n...pump`](https://solscan.io/account/9rZR9nCQbaiBvotWVpifN8z1vckVFshnsATuAJrXpump) |
| **Network** | Solana |
| **Price** | $0.0009409 |
| **24h Volume** | $2.59M |
| **Liquidity** | $81.6K |
| **Volume / Liquidity** | 31.7× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26897 buys / 18927 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hc4r8zmxkkpvdrsacuh1yxasvhmykud85ckavctb2gjo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-black-bull-sol-18f8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
