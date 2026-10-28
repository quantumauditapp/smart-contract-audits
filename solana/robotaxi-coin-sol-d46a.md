---
token: Robotaxi Coin
ticker: ROBOTAXI
network: solana
risk_score: 15
status: low
date: 2026-10-28
---

# Robotaxi Coin (ROBOTAXI) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-sol-d46a)

---

## Audit Summary

The Robotaxi Coin token mint demonstrates strong security posture regarding authority control, as both mint and freeze authorities are revoked. The primary risk identified is a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the queried sources.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high ratio is driven by organic interest or artificial activity. Given the lack of holder distribution data, users should exercise caution regarding potential whale activity that may not be visible in the current registry.

Verify the mint and freeze authority status directly on-chain using a block explorer to confirm they remain set to null. No further administrative actions are required for this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with all administrative authorities revoked, satisfying 7.3 Access Control. 7.1 Architecture is standard for SPL tokens, and 7.2 Code Security is inherent to… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is impacted by a volume-to-liquidity ratio of 63.04, which exceeds the 20x threshold for wash-trading signals. 7.5 Governance is decentralized as the mint authority is null.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, and no extensions allow for balance or fee modifications. The token state is fixed and cannot be… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 63.04, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when evaluating market demand; verify trade history for repetitive, non-organic patterns.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 84% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $63K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $63K of DEX liquidity across 28 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4veRZz...pump`](https://solscan.io/account/4veRZzp7e6tT6FxKL81CZpHPVZrgjj2LUh8FFf6mpump) |
| **Network** | Solana |
| **Price** | $0.0003357 |
| **24h Volume** | $1.41M |
| **Liquidity** | $53.3K |
| **Volume / Liquidity** | 26.5× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14978 buys / 11963 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5urkrfaqb4g6dqj6bdnjknhrtzcydyrnlojrrqwvc3hn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-sol-d46a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
