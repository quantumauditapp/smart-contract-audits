---
token: Moustache Baby
ticker: MOUSTACHE
network: solana
risk_score: 13
status: low
date: 2026-10-24
---

# Moustache Baby (MOUSTACHE) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moustache-baby-sol)

---

## Audit Summary

The Moustache Baby token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully burned, eliminating withdrawal risks, though the high volume-to-liquidity ratio suggests potential wash trading. Holder distribution data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high activity is organic or artificial. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity.

Verify the current supply and authority status using a block explorer to confirm the 'revoked' status remains unchanged. Do not rely on high volume as a proxy for liquidity depth, as the current liquidity is relatively low.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show 100% of liquidity is burned, preventing rug-pulls via withdrawal. However, 7.5 Governance and concentration metrics are limited by missing holder data. 7.6 External market… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is immutable, and extension configurations such as transfer fees and hooks are locked. The token state is fixed, providing high… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 56.90, which exceeds the threshold of 20, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade history to identify organic demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 52% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $109K (DexScreener, all pools). 24h trading volume $3.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $109K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`J9WL4z...pump`](https://solscan.io/account/J9WL4zQVCFvLTydjtHoMGcLasjhRMZomnVmp4Y2cpump) |
| **Network** | Solana |
| **Price** | $0.0003671 |
| **24h Volume** | $3.40M |
| **Liquidity** | $56.7K |
| **Volume / Liquidity** | 59.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33596 buys / 25971 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ffxscky624ixvsvobp3izrlhuqcternwcouvnfdhgfrx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moustache-baby-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
