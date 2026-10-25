---
token: BULLA
ticker: BULLA
network: bsc
risk_score: 21
status: low
date: 2026-10-25
---

# BULLA (BULLA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bulla-bsc)

---

## Audit Summary

The Bulla contract is a standard ERC-20 token implementation. It follows the OpenZeppelin standard library and contains no custom logic, privileged roles, or administrative backdoors. The contract is immutable and functions as a simple value transfer asset.

> **Final Recommendation:** The contract is secure for standard ERC-20 operations. No further action is required as the code is a standard implementation without complex logic or administrative risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 implementation (7.1 Architecture). Code security is high due to the use of audited library primitives (7.2 Code Security). There are no access control… |
| **Governance / Economics** | 7/10 | Low | There are no economic parameters or governance mechanisms present in the contract (7.4 Economic, 7.5 Governance). The token supply is fixed upon deployment. Operations are limited to standard token… |
| **Upgrades** | 9/10 | Low | The contract is not a proxy and does not support upgradeability (7.7 Upgrades). The logic is immutable and cannot be altered post-deployment. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 45.8% |
| **Top-3 Unlocked** | ⚠️ 84.1% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 93.7% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 57.2% of supply. What remains: 38.2% in wallets, 19.0% in other contracts. 60,552 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as BULLA (BULLA), market cap $34M, rank #596. 60,552 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $82K (DexScreener, all pools). 24h trading volume $1.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $601K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $82K of DEX liquidity across 11 pools. Launch: 506 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x595e...3511`](https://bscscan.com/address/0x595e21b20e78674f8a64c1566a20b2b316bc3511) |
| **Network** | BNB Chain |
| **Price** | $0.09007 |
| **24h Volume** | $559.6K |
| **Liquidity** | $66.8K |
| **Volume / Liquidity** | 8.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 57.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2201 buys / 2133 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x9950c1f3754fb8a3ebbaf24b8573cafc7474c00f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bulla-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
