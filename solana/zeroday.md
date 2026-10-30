---
token: ZEROday
ticker: ZERODAY
network: solana
risk_score: 21
status: low
date: 2026-10-30
---

# ZEROday (ZERODAY) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zeroday-sol)

---

## Audit Summary

The ZEROday token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which is a strong indicator of artificial trading activity. Monitor the token's market behavior over a longer period to ensure price stability before committing capital.

Verify the current supply and authority status directly on-chain using a block explorer to confirm that the mint and freeze authorities remain null. Do not rely solely on third-party market data for liquidity assessments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured with 100% of LP tokens burned (7.4 Economic). However, the 24h volume-to-liquidity ratio of 177.11 indicates significant wash trading activity (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding metadata and extension configurations (7.7 Upgrades). No upgrade paths exist for the token program logic itself. Metadata is fixed, preventing post-launch branding… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 177.11, significantly exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for potential slippage in low-liquidity environments.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $2.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 17 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6rg9Gd...ecnj`](https://solscan.io/account/6rg9GdCro19d2sz79mhix5pLJjSwn8RTCjZvG4Wecnj) |
| **Network** | Solana |
| **Price** | $0.00004441 |
| **24h Volume** | $2.83M |
| **Liquidity** | $18.5K |
| **Volume / Liquidity** | 152.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26050 buys / 20467 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4v3mw7djgsrwn8uw3lxca4wgjzo4rkkszgtcwvtnsesc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zeroday-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
