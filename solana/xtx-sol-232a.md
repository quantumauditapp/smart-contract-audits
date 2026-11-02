---
token: XTX
ticker: XTX
network: solana
risk_score: 2
status: low
date: 2026-11-02
---

# XTX (XTX) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xtx-sol-232a)

---

## Audit Summary

The XTX token is a Token-2022 asset with both mint and freeze authorities successfully revoked. The primary risks identified are extremely low liquidity and a high volume-to-liquidity ratio, which indicates potential wash trading. Holder concentration data was unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity environment, which may prevent the execution of sell orders at expected prices. Monitor the market for sustained liquidity growth before considering a position.

Verify the current market depth on the DEX interface before interacting. Do not rely on 24-hour volume metrics as a signal of genuine demand, given the high volume-to-liquidity ratio.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic analysis reveals a critical lack of liquidity at $2,248, making large trades prone to extreme slippage. 7.6 External market data shows a volume-to-liquidity ratio of 1087.10, which is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is an immutable SPL mint. Metadata and balance-mutating authorities are disabled, ensuring the token configuration remains static. No further administrative… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,248. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 1087.10x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; volume may not represent organic market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.0M (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.0M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8cbyp3...pump`](https://solscan.io/account/8cbyp372MxSoWPto5PpiA3CMT84qs7uCG28AjFfepump) |
| **Network** | Solana |
| **Price** | $0.6095 |
| **24h Volume** | $1.09M |
| **Liquidity** | $1.98M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35136 buys / 693 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/94ytuqoo1wwzf8xr3cscwovlca2qsq4xpxvwg3avcnui)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xtx-sol-232a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
