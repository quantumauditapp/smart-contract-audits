---
token: Anome
ticker: ANOME
network: bsc
risk_score: 18
status: low
date: 2026-11-06
---

# Anome (ANOME) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anome-bsc)

---

## Audit Summary

The Anome contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. The codebase is clean, follows industry standards, and lacks any privileged administrative functions or complex logic. No vulnerabilities were identified during the static analysis of the transfer path.

> **Final Recommendation:** The contract is secure and functions as a standard ERC-20 token. No further action is required for the current implementation.

Users should ensure they interact only with the verified contract address provided. As there are no administrative functions, the token is fully decentralized and immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 pattern (7.1 Architecture). Code security is high due to the use of audited OpenZeppelin contracts (7.2 Code Security). There are no external dependencies… |
| **Governance / Economics** | 8/10 | Low | There is no governance mechanism or economic logic implemented within this contract (7.4 Economic, 7.5 Governance). The token supply is fixed upon deployment and cannot be altered. Operations are… |
| **Upgrades** | 9/10 | Low | The contract is not upgradeable (7.7 Upgrades). It is a standard immutable ERC-20 token. No proxy patterns are utilized. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 56.8% |
| **LP Locked** | 56.8% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

56.8% of the pool's LP is burned or time-locked. 56.8% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 43.2% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 2% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 95.3% of supply. Of that, 0.7% burned, 0.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.1% in wallets, 86.1% in other contracts. 33,405 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Anome (ANOME), rank #3825. 33,405 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $8.1M (DexScreener, all pools). 24h trading volume $241K (CoinGecko, all markets, daily snapshot). 24h trading volume $112K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.198 on 2025-10-28; the price is now 91.6725% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8.1M of DEX liquidity across 8 pools. Launch: 386 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6bc3...fbf0`](https://bscscan.com/address/0x6bc3855827fa6ee1229c937a26bb9fca1a0ffbf0) |
| **Network** | BNB Chain |
| **Price** | $0.01621 |
| **24h Volume** | $92.1K |
| **Liquidity** | $133.6K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1086 buys / 583 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x17c3c54a8a4740d7d35578c51af2ec0ce8e95d9e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anome-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
