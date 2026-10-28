---
token: 4GANG
ticker: GANG
network: bsc
risk_score: 43
status: medium
date: 2026-10-28
---

# 4GANG (GANG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/4gang-bsc)

---

## Audit Summary

The contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. Ownership has been renounced, meaning no administrative functions can be executed, effectively locking the contract configuration. The codebase adheres to established standards and presents no identified vulnerabilities.

> **Final Recommendation:** The contract is secure and requires no further action. As ownership is renounced, the contract is immutable and functions as intended by its current state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows standard ERC-20 and ERC-2612 (Permit) patterns, ensuring high interoperability. Code security is robust due to the use of audited OpenZeppelin libraries for core token logic.… |
| **Governance / Economics** | 8/10 | Low | Governance and economic parameters are fixed as ownership is renounced. 7.4 Economic: Standard tokenomics. 7.5 Governance: None. 7.8 Operations: Passive. |
| **Upgrades** | 8/10 | Low | The contract is not a proxy and is immutable. 7.7 Upgrades: Not applicable. |

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

The ten largest holders own 28.4% of supply. Of that, 15.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.8% in wallets, 0.0% in other contracts. 913 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

913 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 11 Nov 2026 (14 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. That date is close: treat it as short-term protection. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $186K (DexScreener, all pools). 24h trading volume $6.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $186K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x03c9...7777`](https://bscscan.com/address/0x03c9ea4fd8f09c72d1d918ea370da1f554487777) |
| **Network** | BNB Chain |
| **Price** | $0.0006563 |
| **24h Volume** | $6.81M |
| **Liquidity** | $186.5K |
| **Volume / Liquidity** | 36.5× |
| **Token Age** | 16h |
| **Top-10 Holders** | 28.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3087 buys / 2217 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcb64321b326b9efc09ba941cb37ed0c8e633803e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/4gang-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
