---
token: Universal High Income
ticker: UHI
network: solana
risk_score: 17
status: low
date: 2026-10-19
---

# Universal High Income (UHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/universal-high-income-sol)

---

## Audit Summary

The mint demonstrates secure fundamental parameters with permanently revoked mint and freeze authorities and 100.0% burned pool liquidity. DEX trading signals raise significant concern due to a 24-hour volume of $6,626,465 against $79,203 in liquidity (an 83.66x ratio), reflecting probable wash trading. On-chain holder distribution data was unavailable during this evaluation.

> **Final Recommendation:** Examine on-chain DEX transaction logs to determine whether the high transaction volume is generated organically or driven by cyclical algorithmic wash trading across linked wallets. Independently inspect token account distribution using a block explorer once holder queries succeed to ensure tokens are broadly distributed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the spl-token-2022 program with a total initialized supply of 960,569,525,328,845 raw units and 6 decimals. Both mint authority and freeze authority are fully revoked… |
| **Governance / Economics** | 8/10 | Low | DEX liquidity is recorded at $79,203, with 100.0% of LP tokens burned, ensuring the liquidity cannot be removed. However, 24-hour DEX trading volume reached $6,626,465 with a pair age of 0 days… |
| **Upgrades** | 10/10 | Low | Mint parameters are immutable, as neither a mint authority nor a freeze authority exists on-chain. Token-2022 configuration indicates balance_mutable, metadata_mutable, and fee upgrade authorities… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 83.66x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Analyze transaction histories for repetitive automated routing between identical wallets before relying on liquidity depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 66% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $126K (DexScreener, all pools). 24h trading volume $7.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $126K of DEX liquidity across 28 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FGkCj2...pump`](https://solscan.io/account/FGkCj28xhabWTYg9QyzACvs4NsN6LUyesP6EwiHepump) |
| **Network** | Solana |
| **Price** | $0.00064 |
| **24h Volume** | $6.58M |
| **Liquidity** | $83.6K |
| **Volume / Liquidity** | 78.7× |
| **Token Age** | 21h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 47771 buys / 39057 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3ensvqnhuhtqzmbxpdg4pkxwbbnzjvfcz2yycfxc9qnh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/universal-high-income-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
