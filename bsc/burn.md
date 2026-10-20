---
token: BURN
ticker: BURN
network: bsc
risk_score: 35
status: medium
date: 2026-10-20
---

# BURN (BURN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/burn-bsc)

---

## Audit Summary

The CurveToken contract implements a standard ERC-20 token with additional tax, dividend, and trading control features. While ownership has been renounced, several administrative functions remain that allow the deployer or owner to influence transfer logic, fees, and dividend exclusions. The code is well-structured, but the presence of centralized control mechanisms and minor arithmetic precision issues warrants caution.

> **Final Recommendation:** Users should be aware that the deployer retains the ability to toggle trading and modify tax/dividend settings, which directly impacts the token's utility and economic behavior. We recommend that the community monitors the deployer's actions closely until all administrative functions are fully renounced or locked.

For future iterations, consider implementing a timelock for sensitive administrative changes to provide transparency and protection against sudden parameter shifts. Ensure that all arithmetic operations involving division are audited for potential precision loss to maintain economic integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns with clean implementation of auxiliary features. 7.1 Architecture is modular, separating dividend tracking from token logic. 7.2 Code Security is… |
| **Governance / Economics** | 8/10 | Low | 7.5 Governance is centralized through the deployer and owner roles. 7.4 Economic parameters, such as transfer fees and trading status, are adjustable by these privileged roles. This creates a… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable once deployed. 7.8 Operations are limited to the defined administrative functions. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 6 Informational_

### `CP-05` — Centralized Control over Trading Status  *(Severity: Medium · Status: Unresolved)*

The deployer has the authority to enable or disable trading via the activateTrading function. This allows the deployer to unilaterally halt or resume token transfers at their discretion.

**Recommendation:** Consider renouncing the deployer role or implementing a decentralized governance mechanism to control trading status.


### `CP-07` — Administrative Control over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The owner and deployer can influence transfer fees through functions like activateTrading and setStartTime. This allows for dynamic adjustment of the economic cost associated with moving tokens.

**Recommendation:** Document the fee structure clearly and consider setting hard caps on fee percentages to protect users from excessive taxation.


### `CD-01` — Potential Precision Loss from Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The _executePoolBurn function performs division before multiplication, which can lead to rounding errors and slight inaccuracies in the calculated burn amounts.

**Recommendation:** Reorder arithmetic operations to perform multiplication before division to maintain higher precision.


### `CP-08` — Administrative Control over Transaction Limits  *(Severity: Low · Status: Unresolved)*

Privileged roles can modify transaction or wallet limits using setStartTime and activateTrading. These changes can restrict how much a user can hold or transfer at once.

**Recommendation:** Ensure that any changes to limits are communicated to the community in advance to prevent unexpected transaction failures.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.3% of supply. Of that, 6.0% burned, 21.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.6% in wallets, 22.2% in other contracts. 21,729 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

21,729 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $114K (DexScreener, all pools). 24h trading volume $565K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $114K of DEX liquidity across 1 pools. Launch: 4 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xffaa...3333`](https://bscscan.com/address/0xffaaac7aa1b772cdc57501bb006ce62c303a3333) |
| **Network** | BNB Chain |
| **Price** | $0.01262 |
| **24h Volume** | $564.7K |
| **Liquidity** | $114.0K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 4d |
| **Top-10 Holders** | 51.3% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 4444 buys / 1887 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xead15eecb8d2230e66aeed0d00b95c39278c009a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/burn-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
