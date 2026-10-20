---
token: Temo
ticker: TEMO
network: ethereum
risk_score: 7
status: low
date: 2026-10-14
---

# Temo (TEMO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/temo-eth)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation. Static analysis and review of key functions reveal no custom privileged logic or complex interactions, resulting in a very low-risk profile. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** The Token contract is a straightforward ERC-20 implementation with no identified vulnerabilities or complex features. Users should exercise standard caution when interacting with any token, verifying the contract address and understanding the token's purpose within its ecosystem. Ensure that any dApps or platforms interacting with this token are also audited and secure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements a standard ERC-20 token (7.1 Architecture). It includes all expected ERC-20 functions such as `transfer`, `transferFrom`, and `approve`. No custom logic, privileged functions… |
| **Governance / Economics** | 10/10 | Low | The contract does not feature any privileged functions or special roles that could introduce governance or economic risks (7.5 Governance). Token transfers are solely governed by standard ERC-20… |
| **Upgrades** | 10/10 | Low | The contract is not designed as an upgradeable proxy, meaning its logic cannot be changed after deployment (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy… |

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

The ten largest holders own 22.3% of supply. What remains: 22.3% in wallets, 0.0% in other contracts. 662 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Temo (TEMO). 662 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $231K (DexScreener, all pools). 24h trading volume $6.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $231K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4602...a430`](https://etherscan.io/address/0x4602e48a5b2e53f83b9bacf36249ccd443b3a430) |
| **Network** | Ethereum |
| **Price** | $0.005448 |
| **24h Volume** | $1.79M |
| **Liquidity** | $231.4K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 11h |
| **Top-10 Holders** | 22.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1569 buys / 523 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa176c263a997c264e62fad513966a9cca343eb44)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/temo-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
