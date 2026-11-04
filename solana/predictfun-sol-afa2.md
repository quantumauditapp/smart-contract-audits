---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 27
status: low
date: 2026-11-04
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol-afa2)

---

## Audit Summary

The PREDICT token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits significant economic risks, specifically a high volume-to-liquidity ratio suggesting potential wash trading and 100% of pool liquidity remaining unlocked and withdrawable. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows for the potential removal of all pool funds by the creator. Monitor the liquidity pool for sudden withdrawals before engaging in trades.

Verify the current liquidity status on-chain periodically. Given the high volume-to-liquidity ratio, avoid relying on reported trading volume as an indicator of genuine market interest or exit liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard SPL Token program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize… |
| **Governance / Economics** | 5/10 | Medium | Economic stability is compromised by the lack of locked liquidity (7.4 Economic). With 100% of liquidity unlocked, the pool creator retains the ability to withdraw all funds (7.5 Governance). The… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing unauthorized changes to branding or token identity (7.7 Upgrades). There are no upgradeable components or proxy patterns inherent to this SPL token mint.… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked; the remaining liquidity can be withdrawn by the pool creator.

**Recommendation:** Lock or burn the liquidity tokens to ensure the pool remains functional for all participants.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 199.23, which is significantly above the threshold of 20, indicating artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume-to-liquidity ratios often precede liquidity removal or price manipulation.


### `M-01` — Low Liquidity Providers  *(Severity: Medium · Status: Unresolved)*

Third-party registry signals indicate a low number of liquidity providers, increasing the risk of price volatility.

**Recommendation:** Monitor liquidity depth before executing large trades to minimize slippage impact.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $170K (DexScreener, all pools). 24h trading volume $33.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $170K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CnCWEA...adrB`](https://solscan.io/account/CnCWEAFg45Rh4ru52uATkog6Trohzg4TKGpi4wt1adrB) |
| **Network** | Solana |
| **Price** | $0.00001002 |
| **24h Volume** | $33.76M |
| **Liquidity** | $170.3K |
| **Volume / Liquidity** | 198.2× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 30077 buys / 27414 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4aafkd5gyzhjjxjxeqq31kpd4r1dm9grpad2kq46xfuu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol-afa2)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
