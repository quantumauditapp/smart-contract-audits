---
token: requests
ticker: REQUESTS
network: solana
risk_score: 21
status: low
date: 2026-10-21
---

# requests (REQUESTS) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/requests-sol)

---

## Audit Summary

The 'requests' token is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits a high volume-to-liquidity ratio of 59.95, which is a strong indicator of wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, as it suggests artificial market activity. Monitor the token's price stability and volume trends before executing large trades.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected changes occur, although the current revocation status is immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default frozen states… |
| **Governance / Economics** | 7/10 | Low | Liquidity is $18,358 and is 100% burned, preventing rug pulls via liquidity withdrawal (7.4 Economic). The 24h volume of $1,100,624 relative to liquidity suggests potential wash trading (7.6… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable (7.7 Upgrades). There are no upgradeable components or proxy patterns in the SPL Token-2022 standard. Authority revocation is permanent (7.3 Access Control). |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 59.95, which exceeds the 20x threshold, indicating potential wash trading.

**Recommendation:** Exercise caution; high volume relative to liquidity can lead to significant slippage and may not reflect genuine market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6ceuPf...pump`](https://solscan.io/account/6ceuPfcE67PLs3Z6CbJpFpqNyAevVocP2zsDkbM1pump) |
| **Network** | Solana |
| **Price** | $0.00005506 |
| **24h Volume** | $1.10M |
| **Liquidity** | $19.9K |
| **Volume / Liquidity** | 55.2× |
| **Token Age** | 22h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8631 buys / 7518 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6bs7vnsbjpjkjyg7flfrd1kxekrb92s7maxnngc9m9bh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/requests-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
