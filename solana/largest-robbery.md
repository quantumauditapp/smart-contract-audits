---
token: Largest Robbery
ticker: ROBBERY
network: solana
risk_score: 21
status: low
date: 2026-10-30
---

# Largest Robbery (ROBBERY) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/largest-robbery-sol)

---

## Audit Summary

The Largest Robbery (ROBBERY) token is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against administrative abuse. However, the token exhibits extreme wash-trading behavior and very low liquidity, which poses significant risks to market participants. Holder concentration data was unavailable from the chain-native RPC.

> **Final Recommendation:** Investors should exercise extreme caution due to the high volume/liquidity ratio, which suggests artificial trading activity. Before interacting with this token, verify the current liquidity depth on a DEX to ensure that slippage remains within acceptable bounds for your trade size.

Monitor the token's market activity for sustained liquidity growth. Since the mint and freeze authorities are revoked, the primary risk is market manipulation rather than protocol-level administrative rug-pulls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default frozen… |
| **Governance / Economics** | 7/10 | Low | Liquidity is extremely low at $2,393, though 100% of the pool liquidity is burned, preventing creator withdrawal (7.4 Economic). The 24-hour volume of $870,835 relative to liquidity indicates a… |
| **Upgrades** | 10/10 | Low | The token is immutable with no upgradeable extensions (7.7 Upgrades). Metadata is non-mutable, ensuring branding consistency. No further administrative changes can be performed on the mint account. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,393. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 363.83x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as the reported volume may not reflect genuine market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $592K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $28K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AdkZmH...pump`](https://solscan.io/account/AdkZmHCBtJyDv1GmYA93JZTG7rts3B7heMrVvayVpump) |
| **Network** | Solana |
| **Price** | $0.0001194 |
| **24h Volume** | $587.2K |
| **Liquidity** | $28.3K |
| **Volume / Liquidity** | 20.7× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3266 buys / 3311 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dnetcdf1eky8xx78ar7trbseai67yx5fvqigcfktblzd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/largest-robbery-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
