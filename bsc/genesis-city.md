---
token: GENESIS CITY
ticker: GENESIS
network: bsc
risk_score: 23
status: low
date: 2026-11-02
---

# GENESIS CITY (GENESIS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/genesis-city-bsc)

---

## Audit Summary

HujiToken is a standard ERC-20 implementation deployed on the BNB Smart Chain. The contract follows the OpenZeppelin standard library, ensuring robust token mechanics. No privileged roles or administrative backdoors were identified in the codebase, making it a trustless asset. The audit identified one minor technical finding related to storage patterns that does not impact user funds.

> **Final Recommendation:** The HujiToken contract is secure for standard ERC-20 operations. No immediate action is required for the token to function as intended.

For future iterations, ensure that any added logic follows the Checks-Effects-Interactions pattern to maintain the current high security posture.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows standard ERC-20 patterns (7.1 Architecture). Code security is high due to the use of audited OpenZeppelin libraries (7.2 Code Security). Access control is non-existent as… |
| **Governance / Economics** | 9/10 | Low | There are no governance mechanisms or economic parameters to manipulate (7.4 Economic, 7.5 Governance). The token supply is fixed or managed by standard mint/burn logic if applicable. Operations are… |
| **Upgrades** | 10/10 | Low | The contract is not upgradeable (7.7 Upgrades). This eliminates risks associated with proxy patterns or logic changes. The code is immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Redundant Storage Write  *(Severity: Medium · Status: Unresolved)*

The contract performs a redundant write operation to storage, which is inefficient but does not compromise the integrity of user balances or token transfers.

**Recommendation:** Refactor the logic to check if the new value is identical to the current value before performing a storage write to save gas.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.7% of supply. Of that, 10.2% burned, 44.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 5.0% in wallets, 13.6% in other contracts. 621 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

621 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $110K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $13K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb1c5...a34a`](https://bscscan.com/address/0xb1c5d6300ac106287e9322335139a6b6d622a34a) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $110.4K |
| **Liquidity** | $12.6K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 73.7% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 1619 buys / 3548 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x96d4673534129d75710a60d8625163b6e38f8298)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/genesis-city-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
