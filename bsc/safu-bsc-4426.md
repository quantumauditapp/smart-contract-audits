---
token: SAFU
ticker: SAFU
network: bsc
risk_score: 33
status: low
date: 2026-11-04
---

# SAFU (SAFU) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/safu-bsc-4426)

---

## Audit Summary

The contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. Ownership has been renounced, meaning no administrative functions can be executed. The codebase follows industry standards for token transfers and allowance management.

> **Final Recommendation:** The contract is secure for standard token operations. No further action is required as the ownership is renounced and the code relies on battle-tested libraries.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 pattern with EIP-712 permit support. 7.1 Architecture is robust and standard. 7.2 Code Security is high due to the use of audited OpenZeppelin contracts.… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance items are not applicable as the contract is a simple token without staking or voting mechanisms. 7.6 External dependencies are limited to standard OpenZeppelin… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as this is a non-proxy contract. 7.8 Operations are straightforward and rely on standard ERC-20 functionality. No upgrade paths exist, ensuring immutability. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.4% of supply. Of that, 23.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.3% in wallets, 0.0% in other contracts. 312 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

312 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 19 Nov 2026 (14 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $86K (DexScreener, all pools). 24h trading volume $800K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $86K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0813...7777`](https://bscscan.com/address/0x0813ef36a6fa3a7c85f08ee59e91811d6a8b7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001738 |
| **24h Volume** | $800.3K |
| **Liquidity** | $86.0K |
| **Volume / Liquidity** | 9.3× |
| **Token Age** | 1h |
| **Top-10 Holders** | 37.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 549 buys / 227 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4bbd2227d7149c57319b10ee27c8c3bfbc55fea8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/safu-bsc-4426)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
