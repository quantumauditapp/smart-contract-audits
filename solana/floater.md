---
token: FLOATER
ticker: FLOATER
network: solana
risk_score: 23
status: low
date: 2026-10-29
---

# FLOATER (FLOATER) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/floater-sol)

---

## Audit Summary

The FLOATER token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high ratio is indicative of sustained interest or artificial inflation. Since liquidity is burned, the pool is safe from creator withdrawal, but users should remain cautious of price volatility given the low total liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or custom… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured with 100% of LP tokens burned (7.4 Economic). However, the volume-to-liquidity ratio of 21.25 indicates suspicious trading patterns (7.6 External). Holder concentration… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing future changes to branding (7.7 Upgrades). All authority-related extensions are locked, ensuring no operational changes can be made to the mint (7.8… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 21.25, which exceeds the 20x threshold and is strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating market demand; verify trade history on-chain to distinguish between organic volume and automated wash trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $49K (DexScreener, all pools). 24h trading volume $968K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $49K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`J7cqsa...pump`](https://solscan.io/account/J7cqsaTuXUavwA3sp238tSpartUfYwDrJAaHuDvypump) |
| **Network** | Solana |
| **Price** | $0.0003409 |
| **24h Volume** | $967.8K |
| **Liquidity** | $49.5K |
| **Volume / Liquidity** | 19.6× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 30288 buys / 13141 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3jowswwkei8ntmrkm3knlhm7xsbm7telrzf9qenels8o)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/floater-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
