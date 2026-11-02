---
token: Warcoin
ticker: WARCOIN
network: solana
risk_score: 21
status: low
date: 2026-11-02
---

# Warcoin (WARCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/warcoin-sol)

---

## Audit Summary

Warcoin is a Token-2022 asset with fully revoked mint and freeze authorities, providing a secure baseline for token supply and transferability. The primary risks identified are low liquidity and a high volume-to-liquidity ratio, which suggest potential wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may not reflect organic market demand. Before trading, verify the current liquidity depth on the target DEX to ensure slippage remains within acceptable bounds for your position size.

Monitor the token's market activity for sustained volume without corresponding liquidity growth, as this is a common indicator of artificial trading patterns. No further on-chain action is required regarding authority management, as the mint and freeze functions are correctly revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture is standard for SPL mints, and 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is challenged by low liquidity of $8,412 and a high volume/liquidity ratio of 69.37, indicating potential wash trading. 7.5 Governance is decentralized as the mint authority is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. 7.8 Operations are secure due to immutable metadata and the absence of balance-mutating authorities. The token… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,412. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 69.37x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Review the trading history and volume sources before interacting with the token.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $860K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H86pLy...pump`](https://solscan.io/account/H86pLyqzZMim3pxrC29YWsMKoxL6xGFM1nQyVtyRpump) |
| **Network** | Solana |
| **Price** | $0.00001862 |
| **24h Volume** | $579.0K |
| **Liquidity** | $10.0K |
| **Volume / Liquidity** | 58.0× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10192 buys / 6453 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/aqnhqikaduvvy5xvznphyaobkdc2lx776v3emcxatmqg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/warcoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
