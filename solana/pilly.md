---
token: Pilly
ticker: PILLY
network: solana
risk_score: 22
status: low
date: 2026-10-22
---

# Pilly (PILLY) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pilly-sol)

---

## Audit Summary

The Pilly token (2CvGN3ynUisRVdgeycFS6GrZZtyjxwtTPr9U1XPhpump) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio may indicate artificial market manipulation. Verify that no new liquidity pools are created with unburned tokens.

Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity. Use on-chain explorers to periodically verify the mint and freeze authority status remains null.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control (7.3) is robust, as both mint and freeze authorities are revoked. No transfer hooks or custom extensions are… |
| **Governance / Economics** | 7/10 | Low | Economic (7.4) stability is impacted by a high volume-to-liquidity ratio of 32.25, which exceeds the 20x threshold for wash-trading signals. Liquidity is fully secured, with 100% of LP tokens burned… |
| **Upgrades** | 10/10 | Low | Upgrades (7.7) are not applicable as the mint is a standard SPL token. Metadata and balance-mutating authorities are immutable, ensuring long-term consistency. No further administrative changes are… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 32.25, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading patterns for signs of bot-driven volume and exercise caution when assessing market depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $428K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 9 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2CvGN3...pump`](https://solscan.io/account/2CvGN3ynUisRVdgeycFS6GrZZtyjxwtTPr9U1XPhpump) |
| **Network** | Solana |
| **Price** | $0.00003397 |
| **24h Volume** | $381.8K |
| **Liquidity** | $14.6K |
| **Volume / Liquidity** | 26.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4851 buys / 3595 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9zp33ckbjenni1jgwsuk8ekh2jx1ou3kwort1pvd3smm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pilly-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
