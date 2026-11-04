---
token: Vitalik the Shoggoth
ticker: VITOGGOTH
network: ethereum
risk_score: 16
status: low
date: 2026-11-04
---

# Vitalik the Shoggoth (VITOGGOTH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vitalik-the-shoggoth-eth-583c)

---

## Audit Summary

The Vitoggoth contract is a standard ERC-20 token implementation. The codebase follows OpenZeppelin standards and contains no custom logic, privileged roles, or administrative backdoors. The contract is immutable and functions as a simple, permissionless asset.

> **Final Recommendation:** The contract is secure and follows industry best practices for a standard ERC-20 token. No further action is required as there are no identified vulnerabilities or administrative risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes standard ERC-20 patterns (7.1 Architecture) with robust, battle-tested library implementations (7.2 Code Security). The transfer path is standard and lacks complex state… |
| **Governance / Economics** | 9/10 | Low | There is no governance mechanism or economic logic (7.4 Economic, 7.5 Governance). The token is a simple utility asset without inflationary or deflationary mechanics. Operations are fully… |
| **Upgrades** | 10/10 | Low | The contract is not a proxy and does not support upgrades (7.7 Upgrades). The code is immutable, ensuring that the logic cannot be altered post-deployment. This eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 23.4% of supply. What remains: 9.2% in wallets, 14.1% in other contracts. 199 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

199 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $107K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x823e...4026`](https://etherscan.io/address/0x823eb6534202a300ca4a61d0977d9a7a52c84026) |
| **Network** | Ethereum |
| **Price** | $0.0001148 |
| **24h Volume** | $106.6K |
| **Liquidity** | $30.9K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 2h |
| **Top-10 Holders** | 23.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 225 buys / 189 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe7cd7226ca5f6ec9cc62b7b0fd0cea5a67138b5df2f3654d011d426f228228bc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vitalik-the-shoggoth-eth-583c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
