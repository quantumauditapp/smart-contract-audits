---
token: Gang
ticker: GANG
network: bsc
risk_score: 42
status: medium
date: 2026-10-23
---

# Gang (GANG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gang-bsc-9ac5)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. Ownership has been renounced, meaning no administrative functions can be executed, effectively locking the contract configuration. The codebase follows industry-standard patterns for token transfers and allowance management.

> **Final Recommendation:** The contract is secure and follows standard implementation patterns. No further action is required as the ownership is renounced and the code is standard.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture relies on established OpenZeppelin ERC-20 and EIP-712 standards, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is effectively disabled due to the… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance risks are minimal as the token lacks complex logic or administrative control. The supply is fixed and immutable due to the renounced ownership. No external economic… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are straightforward, with no administrative overhead or maintenance requirements. The contract is immutable by design. |

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

The ten largest holders own 23.0% of supply. Of that, 15.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.3% in wallets, 0.0% in other contracts. 936 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

936 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 06 Nov 2026 (14 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $195K (DexScreener, all pools). 24h trading volume $9.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $195K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe0b5...7777`](https://bscscan.com/address/0xe0b5e9b42f35e03eb0b11fcce6c8a37e4d4e7777) |
| **Network** | BNB Chain |
| **Price** | $0.0006726 |
| **24h Volume** | $9.25M |
| **Liquidity** | $195.1K |
| **Volume / Liquidity** | 47.4× |
| **Token Age** | 17h |
| **Top-10 Holders** | 23.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3825 buys / 2946 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1b6741702c8dfc9a8bb72872605f3bc834de56b4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gang-bsc-9ac5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
