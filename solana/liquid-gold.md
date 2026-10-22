---
token: Liquid Gold
ticker: MERCURY
network: solana
risk_score: 23
status: low
date: 2026-10-22
---

# Liquid Gold (MERCURY) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/liquid-gold-sol)

---

## Audit Summary

Liquid Gold (MERCURY) exhibits an extreme 24-hour volume-to-liquidity ratio of 103.73 ($1,430,542 volume on $13,791 liquidity), indicating an active wash-trading pattern. Both mint and freeze authorities are revoked and 100.0% of pool liquidity is permanently burned. Holder distribution data was unavailable from chain-native RPC at the time of assessment.

> **Final Recommendation:** Query Solana RPC `getTokenLargestAccounts` directly to confirm individual holder concentration before executing trades. Monitor DEX transaction flows for automated circular swap loops between linked wallets that artificially inflate trading volume.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint utilizes the spl-token-2022 program with an initialized supply of 985,166,209,242,600 base units across 6 decimals. Both the mint authority and freeze authority are confirmed null… |
| **Governance / Economics** | 7/10 | Low | Total DEX liquidity stands at $13,791, with 100.0% of the LP tokens burned, preventing any creator liquidity rug pull. However, the 24-hour trading volume reached $1,430,542 on pair age day 0… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are permanently revoked, eliminating administrative upgrade or modification paths. Token metadata is flagged as immutable, preventing post-launch rebranding or… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 103.73x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for high artificial turnover and potential market manipulation when evaluating liquidity depth and execution slippage.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $14K of DEX liquidity across 20 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BaBDzV...pump`](https://solscan.io/account/BaBDzVBE3pTxuCjU7gcqNENUCfJpo24hDxDEsufhpump) |
| **Network** | Solana |
| **Price** | $0.00002762 |
| **24h Volume** | $1.43M |
| **Liquidity** | $13.9K |
| **Volume / Liquidity** | 102.8× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12688 buys / 10211 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dxteupe94ucesefqkberxv3h4skcbw3tp23ejfwnr92f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/liquid-gold-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
