---
token: Wired fees to socials
ticker: WIRED
network: bsc
risk_score: 0
status: low
date: 2026-10-01
---

# Wired fees to socials (WIRED) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wired-fees-to-socials-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone. Its ownership has been renounced on-chain, rendering all `onlyOwner` functions, including those for adjusting transfer fees (`startMigration`, `finalizeMigration`), permanently inactive. This design choice significantly reduces administrative risk and ensures the immutability of the token's core parameters post-deployment. No specific vulnerabilities were identified during the audit.

> **Final Recommendation:** Given the contract's non-upgradeable nature and renounced ownership, the primary security recommendation is to ensure that all initial parameters and configurations were thoroughly verified and set correctly at the time of deployment. No further administrative actions are possible to modify the token's behavior or economic rules. Token holders should be aware that the contract's logic and economic mechanisms are immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements the ERC-20 standard with all expected functionalities (7.1 Architecture). It is deployed as an EIP-1167 minimal clone, ensuring its logic is fixed and cannot be altered… |
| **Governance / Economics** | 10/10 | Low | The token's economic parameters, specifically the `poolState` which influences transfer amounts and fees, were designed to be adjustable via `startMigration` and `finalizeMigration` (7.4 Economic).… |
| **Upgrades** | 10/10 | Low | The contract is deployed as an EIP-1167 minimal clone (7.1 Architecture), which inherently means its implementation is fixed and cannot be upgraded or modified after deployment (7.7 Upgrades). The… |

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

The ten largest holders own 21.9% of supply. Of that, 5.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 3.9% in wallets, 12.6% in other contracts. 1,878 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,878 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $114K (DexScreener, all pools). 24h trading volume $721K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $114K of DEX liquidity across 3 pools. Launch: 4 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x55db...7777`](https://bscscan.com/address/0x55db4b1f497b1d7aa93354701883efc758367777) |
| **Network** | BNB Chain |
| **Price** | $0.0009861 |
| **24h Volume** | $720.6K |
| **Liquidity** | $113.7K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 4d |
| **Top-10 Holders** | 21.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1954 buys / 1375 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x380462504f0eb4eb9955e7db3530559a7a3b0beb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wired-fees-to-socials-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
