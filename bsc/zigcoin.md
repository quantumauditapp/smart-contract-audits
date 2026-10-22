---
token: ZigCoin
ticker: ZIG
network: bsc
risk_score: 18
status: low
date: 2026-10-22
---

# ZigCoin (ZIG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zigcoin-bsc)

---

## Audit Summary

The ZigCoinBSC contract is a standard ERC-20 token implementation. The code follows the OpenZeppelin library structure, ensuring standard compliance and predictable behavior. No privileged roles or administrative functions were identified, meaning the contract operates in a fully decentralized, immutable manner.

> **Final Recommendation:** The contract is secure and follows industry standards for a basic ERC-20 token. No further action is required as the code is immutable and lacks complex logic that could introduce vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns (7.1 Architecture). Code security is robust due to the use of well-audited OpenZeppelin base contracts (7.2 Code Security). There are no access… |
| **Governance / Economics** | 6/10 | Medium | There are no governance or economic parameters defined in the contract (7.4 Economic, 7.5 Governance). The token supply is fixed upon deployment and cannot be modified. Operations are limited to… |
| **Upgrades** | 9/10 | Low | The contract is not upgradeable (7.7 Upgrades). This provides high security against proxy-related vulnerabilities but prevents any future logic updates. The implementation is immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x712c…45cb — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.2% of supply. Of that, 0.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.1% in wallets, 95.7% in other contracts. 10,182 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ZIG Finance (ZIG), market cap $67M, rank #363. 10,182 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $813K (DexScreener, all pools). 24h trading volume $4.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $813K of DEX liquidity across 9 pools. Launch: 1884 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8c90...1145`](https://bscscan.com/address/0x8c907e0a72c3d55627e853f4ec6a96b0c8771145) |
| **Network** | BNB Chain |
| **Price** | $0.04782 |
| **24h Volume** | $2.27M |
| **Liquidity** | $782.7K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 5y |
| **Top-10 Holders** | 98.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6073 buys / 5889 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9fac151b7f1dbbb9d14ccd1ca5b990bc4da5cd1f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zigcoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
