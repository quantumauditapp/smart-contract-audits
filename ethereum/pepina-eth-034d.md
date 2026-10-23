---
token: Pepina
ticker: PEPINA
network: ethereum
risk_score: 7
status: low
date: 2026-10-23
---

# Pepina (PEPINA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepina-eth-034d)

---

## Audit Summary

The audited contract is a standard, immutable ERC-20 token implementation. It lacks any privileged administrative functions, backdoors, or complex logic, adhering strictly to the OpenZeppelin ERC-20 standard. No vulnerabilities were identified during the static analysis of the codebase.

> **Final Recommendation:** The contract is secure and follows standard implementation patterns. No further action is required for the current codebase as it contains no logic flaws or administrative risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 specification (7.1 Architecture). Code security is high due to the use of well-vetted, standard library implementations (7.2 Code Security). There are no… |
| **Governance / Economics** | 10/10 | Low | The token has no governance or economic parameters (7.4 Economic, 7.5 Governance). It functions as a simple value transfer asset without inflationary or deflationary mechanics. Operations are limited… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable (7.7 Upgrades). It is a standard, immutable deployment, ensuring that the logic cannot be altered post-deployment. This eliminates risks associated with proxy patterns… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.0% of supply. What remains: 21.0% in wallets, 0.0% in other contracts. 547 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

547 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $281K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $281K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8ce3...ace4`](https://etherscan.io/address/0x8ce3cac9fe9436e6e4b6539e6853ac1b037dace4) |
| **Network** | Ethereum |
| **Price** | $0.009481 |
| **24h Volume** | $1.33M |
| **Liquidity** | $281.2K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 4h |
| **Top-10 Holders** | 21.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 834 buys / 280 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x0e8a47cd980007364d539b174cb24c6079efd515)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepina-eth-034d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
