---
token: MEME HORSE
ticker: MHORSE
network: bsc
risk_score: 53
status: medium
date: 2026-11-03
---

# MEME HORSE (MHORSE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meme-horse-bsc)

---

## Audit Summary

The MHORSE contract is a standard ERC-20 token implementation. The codebase follows OpenZeppelin standards and lacks any privileged administrative functions, backdoors, or complex logic. No vulnerabilities were identified during the static analysis of the transfer path and state management.

> **Final Recommendation:** The contract is secure and follows industry best practices for a standard ERC-20 token. No further action is required as the code is immutable and lacks privileged functions that could be exploited.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows the standard ERC-20 implementation (7.1 Architecture). Code security is high due to the use of well-vetted libraries (7.2 Code Security). There are no access control… |
| **Governance / Economics** | 2/10 | High | There are no economic parameters or governance mechanisms (7.4 Economic, 7.5 Governance). The token supply is fixed or managed via standard mint/burn logic if applicable, but no administrative… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy and does not support upgradeability (7.7 Upgrades). This ensures immutability of the token logic. No upgrade risk exists. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 93.3% is held, unlocked, by the token's owner/deployer (0x33db…b518) — they can pull that liquidity at any moment. This is the rug-pull path. 6.7% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.3% of supply. Of that, 24.4% locked, 4.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.1% in wallets, 0.0% in other contracts. 18,161 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as MEME HORSE (MHORSE), market cap $34M, rank #601. 18,161 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $813K (CoinGecko, all markets, daily snapshot). 24h trading volume $781K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Chinese Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 1 pools. Launch: 267 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9daf...b88d`](https://bscscan.com/address/0x9daf1a070f882d870a8d58d7a27041c752f3b88d) |
| **Network** | BNB Chain |
| **Price** | $0.03374 |
| **24h Volume** | $781.0K |
| **Liquidity** | $1.62M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 32.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 515 buys / 516 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcdcc8dc1f3f5132d9d7e46a5436ce2f693826004)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meme-horse-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
