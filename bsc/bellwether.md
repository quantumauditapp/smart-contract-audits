---
token: Bellwether
ticker: 领头羊
network: bsc
risk_score: 1
status: low
date: 2026-10-10
---

# Bellwether (领头羊) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bellwether-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an EIP-1167 minimal clone, meaning its logic is fixed and cannot be upgraded. Ownership of the contract has been renounced on-chain, rendering all owner-restricted functions, including those that modify transfer fees and states, permanently inactive. No specific vulnerabilities were identified during the audit.

> **Final Recommendation:** Users should be aware that the FlapTaxTokenV3 token's logic is immutable and its administrative functions are permanently disabled due to renounced ownership. This provides a high degree of certainty regarding its future behavior. Token holders should verify the current `poolState` and associated transfer fees, as these are now fixed. No further security actions are required for the contract itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract is implemented as an EIP-1167 minimal clone, ensuring its bytecode and logic are immutable post-deployment (7.1 Architecture). It provides standard ERC-20 functionality… |
| **Governance / Economics** | 10/10 | Low | The economic parameters of the token, specifically the `poolState` which influences transfer amounts and fees, were designed to be modifiable via `startMigration` and `finalizeMigration` (7.4… |
| **Upgrades** | 10/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed at deployment and cannot be upgraded or altered (7.7 Upgrades). This design choice provides strong… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 23.7% of supply. Of that, 13.8% burned, 0.6% locked, 3.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.2% in wallets, 1.6% in other contracts. 21,108 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Bellwether (领头羊), market cap $2M, rank #2368. 21,108 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 61% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $240K (DexScreener, all pools). 24h trading volume $524K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $240K of DEX liquidity across 14 pools. Launch: 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x589f...7777`](https://bscscan.com/address/0x589f84b19933c1a8edac82a37ed329b327f97777) |
| **Network** | BNB Chain |
| **Price** | $0.00199 |
| **24h Volume** | $923.2K |
| **Liquidity** | $146.4K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 6d |
| **Top-10 Holders** | 23.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 8544 buys / 4367 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x434d3b73640a81022adf8529b612cc221010f6bf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bellwether-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
