---
token: evmbot
ticker: EVMBOT
network: ethereum
risk_score: 8
status: low
date: 2026-10-22
---

# evmbot (EVMBOT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/evmbot-eth)

---

## Audit Summary

The evmbot contract is a standard ERC-20 token implementation. The codebase follows OpenZeppelin standards and contains no privileged administrative functions, backdoors, or complex logic that could lead to unauthorized fund movement or manipulation. The contract is immutable and operates as a simple utility token.

> **Final Recommendation:** The contract is secure for its intended purpose as a standard ERC-20 token. No further action is required as there are no vulnerabilities or administrative risks identified.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns using OpenZeppelin libraries. Code security is high due to the lack of custom logic or complex state machines. Access control is non-existent, which… |
| **Governance / Economics** | 10/10 | Low | There are no governance or economic mechanisms within this contract. 7.4 Economic and 7.5 Governance coverage items are not applicable as the token has no minting, burning, or fee-on-transfer logic.… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable and does not utilize proxy patterns. 7.7 Upgrades coverage confirms the contract is immutable. 7.8 Operations are straightforward as no maintenance is required. |

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

The ten largest holders own 24.6% of supply. Of that, 2.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.2% in wallets, 2.3% in other contracts. 245 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

245 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $146K (DexScreener, all pools). 24h trading volume $495K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $146K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0e45...11de`](https://etherscan.io/address/0x0e45c6356637a3c71d450764c37ae69ae69011de) |
| **Network** | Ethereum |
| **Price** | $0.003382 |
| **24h Volume** | $494.6K |
| **Liquidity** | $146.0K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 2h |
| **Top-10 Holders** | 24.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 465 buys / 108 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x2b589da180f279a1e03cc819f29fc8f98cedec4c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/evmbot-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
