---
token: Mimi
ticker: MIMI
network: solana
risk_score: 20
status: low
date: 2026-10-19
---

# Mimi (MIMI) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mimi-sol)

---

## Audit Summary

Mimi implements the Token-2022 standard with fully revoked mint and freeze authorities and permanently burned DEX pool liquidity. However, DEX market data reveals an abnormal volume-to-liquidity ratio exceeding 170x, signalling heavy artificial volume or wash trading. Note that holder distribution metrics were unavailable from chain-native RPC at the time of assessment.

> **Final Recommendation:** Examine order book and trade history data across decentralized exchanges to confirm whether volume is organic before executing swaps. Validate on-chain token account distributions independently once RPC indexer services update, checking that individual wallets do not hold overwhelming shares of circulating tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with initialized status and 6 decimals across a total supply of 956,334,037,940,371 raw units. Both mint and freeze authorities are permanently… |
| **Governance / Economics** | 7/10 | Low | Pool liquidity stands at $16,969 with 100.0% of LP tokens burned, eliminating the risk of creator withdrawal. Despite non-withdrawable liquidity, 24-hour trading volume reached $2,891,396 on a newly… |
| **Upgrades** | 10/10 | Low | The mint parameters are structurally immutable with zero active administrative roles. Neither the transfer hook nor transfer fee extensions are present or upgradable, and metadata is permanently… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 170.39x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Inspect trade execution counterparties and transaction frequency for automated self-dealing before engaging with the market.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $3.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8CYyiv...pump`](https://solscan.io/account/8CYyivwMZPg6Edaofxo3eHiveZkDrU6TtUDwtMjTpump) |
| **Network** | Solana |
| **Price** | $0.00004188 |
| **24h Volume** | $2.89M |
| **Liquidity** | $18.2K |
| **Volume / Liquidity** | 158.5× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 28850 buys / 24555 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/haewlk7ysun3tsyit87zzwq1jdpgvp2mvffpbde8seit)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mimi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
