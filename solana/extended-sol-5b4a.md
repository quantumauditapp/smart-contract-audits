---
token: Extended
ticker: XTEN
network: solana
risk_score: 27
status: low
date: 2026-11-07
---

# Extended (XTEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/extended-sol-5b4a)

---

## Audit Summary

The token exhibits significant economic risks due to extreme wash-trading signals and the lack of locked liquidity. While the mint and freeze authorities are correctly revoked, the high volume-to-liquidity ratio and the absence of locked LP tokens suggest a high risk of market manipulation. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the liquidity pool for sudden withdrawals and verify the current liquidity depth before executing any trades.

Verify the current state of the mint address on a block explorer to confirm that authorities remain revoked. Avoid large market orders given the high slippage potential and the absence of locked LP tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). The… |
| **Governance / Economics** | 5/10 | Medium | The token shows a volume/liquidity ratio of 207.20, which is highly indicative of wash trading (7.4 Economic). 100% of liquidity remains unlocked, posing a risk of sudden withdrawal (7.8 Operations).… |
| **Upgrades** | 8/10 | Low | The token does not support upgrades or metadata changes (7.7 Upgrades). Metadata is immutable, and no transfer hooks or fee extensions are present (7.5 Governance). |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 207.20, significantly exceeding the 20x threshold, which is a strong indicator of artificially inflated trade volume.

**Recommendation:** Monitor trading activity for organic volume and be aware that price action may not reflect genuine market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the liquidity can be withdrawn by the pool creator at any time.

**Recommendation:** Treat the liquidity pool as temporary and subject to removal by the creator.


### `M-01` — High-Risk LP Status  *(Severity: Medium · Status: Unresolved)*

Third-party registry signals indicate a large amount of LP is unlocked and there is a low number of LP providers, increasing the risk of liquidity instability.

**Recommendation:** Exercise caution when providing liquidity or trading in low-depth pools.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $172K (DexScreener, all pools). 24h trading volume $35.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $172K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GXKH2n...bbpK`](https://solscan.io/account/GXKH2nRJqu7BznzSdUELcMwk7C3ebNDcqB5YEgM4bbpK) |
| **Network** | Solana |
| **Price** | $0.00001015 |
| **24h Volume** | $35.35M |
| **Liquidity** | $172.4K |
| **Volume / Liquidity** | 205.0× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 32140 buys / 29365 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4jnvpakstntyakv5plzdhkr8bqr6ldovdkygahiupgn8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/extended-sol-5b4a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
