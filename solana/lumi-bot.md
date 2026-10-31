---
token: Lumi Bot
ticker: LUMIBOT
network: solana
risk_score: 19
status: low
date: 2026-10-31
---

# Lumi Bot (LUMIBOT) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lumi-bot-sol)

---

## Audit Summary

The Lumi Bot token is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against administrative abuse. However, the token exhibits high-risk trading patterns, including extremely low liquidity and a volume-to-liquidity ratio indicative of wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity, which prevents large exits without significant price impact. Monitor the asset for sustained organic volume before considering participation.

Verify the current liquidity depth on-chain before executing any swaps. Avoid relying on 24-hour volume metrics as a proxy for market interest, as the current ratio suggests potential wash trading.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default frozen states… |
| **Governance / Economics** | 9/10 | Low | Liquidity is critically low at $1,977, creating significant slippage risks (7.4 Economic). The volume-to-liquidity ratio of 226.70 suggests artificial trading activity (7.6 External). While 100% of… |
| **Upgrades** | 10/10 | Low | The token is immutable with no upgradeable components (7.7 Upgrades). Metadata is not mutable, ensuring branding consistency. No further administrative changes are possible due to revoked authorities. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $1,977. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 226.70x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Verify volume sources and market depth before trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $428K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 4 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Dqwrb1...pump`](https://solscan.io/account/Dqwrb1YVyL9Ewf5C8eWFhjnqMzZocMC8bbwt2tetpump) |
| **Network** | Solana |
| **Price** | $0.0001443 |
| **24h Volume** | $424.4K |
| **Liquidity** | $30.4K |
| **Volume / Liquidity** | 14.0× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11175 buys / 7868 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dycszami4myucoddz15xpohbqmwtjxgcxmgcgnhzniry)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lumi-bot-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
