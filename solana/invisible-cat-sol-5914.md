---
token: Invisible Cat
ticker: INVISIBLE
network: solana
risk_score: 26
status: low
date: 2026-10-28
---

# Invisible Cat (INVISIBLE) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/invisible-cat-sol-5914)

---

## Audit Summary

The token exhibits significant economic risks due to extreme wash-trading signals and a lack of locked liquidity. While the mint and freeze authorities are correctly revoked, the high volume-to-liquidity ratio and the fact that 100% of pool liquidity remains withdrawable by anonymous holders present a high risk of rug-pull. Holder distribution data was unavailable from the registry.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Before interacting, verify the current liquidity provider status on-chain to determine if the pool creator has moved to lock or burn their LP tokens.

Monitor the pool for sudden liquidity withdrawals. Given the high wash-trading signal, do not rely on DEX volume metrics as an indicator of organic demand or market depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are robust as both the Mint Authority and Freeze Authority are revoked. 7.2 Code Security is standard… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic stability is compromised by a volume/liquidity ratio of 145.09, indicating heavy wash-trading. 7.6 External data shows 100% of pool liquidity is unlocked and withdrawable by anonymous… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, and no extension-based upgrade paths were detected. The token state is fixed and cannot be modified by any authority. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 145.09, which significantly exceeds the 20x threshold, indicating artificial trade volume.

**Recommendation:** Do not use volume as a proxy for liquidity or interest; monitor for sudden price manipulation.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the liquidity provider can withdraw all funds at any time.

**Recommendation:** Verify if the liquidity provider intends to lock the LP tokens; avoid providing liquidity to this pool.


### `M-01` — Third-Party Risk Flag  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry flagged the token for having a large amount of unlocked LP and a low number of LP providers.

**Recommendation:** Treat the token as high-risk due to the potential for liquidity removal and low decentralization of the pool.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $118K (DexScreener, all pools). 24h trading volume $16.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $118K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4R6qGE...q1xW`](https://solscan.io/account/4R6qGExrfDGErUbAcMKsZoYN7wjz1s3Jsj2JWKCmq1xW) |
| **Network** | Solana |
| **Price** | $0.0001173 |
| **24h Volume** | $16.17M |
| **Liquidity** | $118.3K |
| **Volume / Liquidity** | 136.8× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15504 buys / 10477 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/3bxpggrhuyz1sknjmjr8j6u7yg6ysvnmx6metq4nnzmc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/invisible-cat-sol-5914)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
