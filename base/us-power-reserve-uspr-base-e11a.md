---
token: U.S POWER RESERVE (USPR)
ticker: USPR
network: base
risk_score: 72
status: high
date: 2026-11-07
---

# U.S POWER RESERVE (USPR) (USPR) — Smart Contract Security Analysis | Base

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-power-reserve-uspr-base-e11a)

---

## Audit Summary

The contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. It includes EIP-2612 permit functionality for gasless approvals. No privileged roles or administrative backdoors were identified in the codebase.

> **Final Recommendation:** The contract is secure and follows industry standards for a basic ERC-20 token. No further action is required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows standard ERC-20 patterns (7.1 Architecture) with robust implementation via OpenZeppelin (7.2 Code Security). The code is clean and adheres to current Solidity standards… |
| **Governance / Economics** | 1/10 | High | The token has no governance mechanisms or economic parameters (7.4 Economic, 7.5 Governance). It functions as a simple utility token without minting or burning capabilities. Access control is… |
| **Upgrades** | 6/10 | Medium | The contract is not a proxy and does not support upgrades (7.7 Upgrades). The logic is immutable upon deployment. Operational risks are minimal due to the lack of administrative functions (7.8… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x20a3…4708) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.5% of supply. What remains: 22.4% in wallets, 19.1% in other contracts. 902 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

902 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $206K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $206K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x91af...8749`](https://basescan.org/address/0x91afdadeff57b718d3153f5640a29487c3db8749) |
| **Network** | Base |
| **Price** | $0.00000585 |
| **24h Volume** | $1.01M |
| **Liquidity** | $206.5K |
| **Volume / Liquidity** | 4.9× |
| **Token Age** | 3h |
| **Top-10 Holders** | 41.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1341 buys / 848 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd1e21c72e3ddcb09c388100bc602c950368f4efbab8ad9146458fa7962ca2706)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-power-reserve-uspr-base-e11a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
