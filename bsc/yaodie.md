---
token: YAODIE
ticker: 妖蝶
network: bsc
risk_score: 0
status: low
date: 2026-10-12
---

# YAODIE (妖蝶) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yaodie-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone. Ownership has been renounced, rendering all owner-restricted functions, including those affecting transfer logic, dormant. The contract exhibits a robust and immutable design, with no critical or high-severity vulnerabilities identified.

> **Final Recommendation:** Given the renounced ownership and immutable nature of the FlapTaxTokenV3 contract, the primary recommendation is to ensure all users understand its fixed parameters. No further security-specific actions are required for the contract itself. Users should be aware that the token's behavior, including any transfer fees or special states, is permanently set and cannot be altered.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract is a standard-compliant ERC-20 token, supporting core functionalities like `transfer` and `balanceOf`. Its architecture as an EIP-1167 minimal clone ensures immutability… |
| **Governance / Economics** | 10/10 | Low | The governance and economic risk for FlapTaxTokenV3 is low due to the renounced ownership (7.5 Governance). This means no single entity can unilaterally alter the token's parameters or transfer… |
| **Upgrades** | 10/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means it is not upgradeable (7.7 Upgrades). Its bytecode is fixed, and there is no mechanism to change its logic or point… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.8% of supply. Of that, 70.1% burned, 0.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.0% in wallets, 0.7% in other contracts. 8,219 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

8,219 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $447K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $447K of DEX liquidity across 3 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8274...7777`](https://bscscan.com/address/0x82741f086b0d87b1430400ea259d703c5dc37777) |
| **Network** | BNB Chain |
| **Price** | $0.02302 |
| **24h Volume** | $1.80M |
| **Liquidity** | $433.5K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 79.8% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 7599 buys / 3154 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x42acaf8e330b5f686e1e8ec9884bc997e926199f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yaodie-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
