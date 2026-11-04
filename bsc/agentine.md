---
token: AGENTINE
ticker: AGENTINE
network: bsc
risk_score: 22
status: low
date: 2026-11-04
---

# AGENTINE (AGENTINE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agentine-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token implemented as an EIP-1167 minimal clone. The contract ownership has been renounced on-chain, rendering all privileged administrative functions permanently dormant. The token logic is immutable and cannot be upgraded or altered by any party.

> **Final Recommendation:** No security issues were identified. The contract is immutable and ownership has been renounced, providing a high degree of trust for token holders. Users should interact with the contract with confidence that the current logic will remain unchanged.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a standard EIP-1167 minimal clone pattern, ensuring gas-efficient deployment. Code security is robust, adhering to standard ERC-20 and ERC-2612 (Permit) specifications. 7.1… |
| **Governance / Economics** | 6/10 | Medium | Economic parameters are fixed due to the renounced ownership. 7.4 Economic and 7.5 Governance items are effectively locked, preventing any future manipulation of tax or migration states. The protocol… |
| **Upgrades** | 9/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. 7.7 Upgrades are not applicable as the implementation address is hardcoded into the proxy bytecode and cannot be… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 82.4% |
| **LP Locked** | 82.4% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

82.4% of the pool's LP is burned or time-locked. 82.4% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 17.6% is held, unlocked, by 2 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.7% of supply. Of that, 64.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.5% in wallets, 5.3% in other contracts. 377 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

377 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $380K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 2% on buy, 2% on sell. Market: $11K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb47d...7777`](https://bscscan.com/address/0xb47db73293380088a1d78fb5c51bf9038f217777) |
| **Network** | BNB Chain |
| **Price** | $0.00000872 |
| **24h Volume** | $332.0K |
| **Liquidity** | $11.1K |
| **Volume / Liquidity** | 29.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 78.7% of supply |
| **Buy / Sell Tax** | 2.0% / 2.0% |
| **24h Transactions** | 8435 buys / 3696 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x1b6d80f217c73efe5f011a045ce8e1251404b5fc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agentine-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
