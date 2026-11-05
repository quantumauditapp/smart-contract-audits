---
token: BUSTED
ticker: BUSTED
network: solana
risk_score: 27
status: low
date: 2026-11-05
---

# BUSTED (BUSTED) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/busted-sol)

---

## Audit Summary

The BUSTED token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were identified by third-party registries. The primary risk factor is high holder concentration, which is common for early-stage tokens.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs, as the concentration is high. No further technical action is required as the mint and freeze authorities are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control (7.3) is robust, as both mint and freeze authorities are revoked. No transfer hooks or balance-mutating extensions are… |
| **Governance / Economics** | 8/10 | Low | Economic security (7.4) is supported by 100% burned liquidity, preventing rug-pulls via withdrawal. However, holder concentration (7.5) is high, with the top 10 holders controlling 100% of the… |
| **Upgrades** | 10/10 | Low | The token has no upgradeable components (7.7 Upgrades). Metadata and extension configurations are locked, ensuring long-term consistency of the token's properties. |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 100% of the supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for signs of distribution or coordinated selling.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 4.3% in wallets, 95.7% in other contracts. 9 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

9 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $89K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Gg3XUJ...pump`](https://solscan.io/account/Gg3XUJHFoFSha6cWFDT2im8mtNuSHhCzp2D4naowpump) |
| **Network** | Solana |
| **Price** | $0.0000432 |
| **24h Volume** | $88.8K |
| **Liquidity** | $17.0K |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 890 buys / 601 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6hwhwypnhvi3qh3xkexetwg6b2mx7ctcxpntwznprwd9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/busted-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
