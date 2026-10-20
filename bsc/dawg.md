---
token: DAWG
ticker: DAWG
network: bsc
risk_score: 0
status: low
date: 2026-10-17
---

# DAWG (DAWG) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dawg-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, ensuring its logic is immutable. Ownership has been renounced on-chain, rendering all previously owner-restricted functions, including those that modify transfer parameters like `startMigration` and `finalizeMigration`, permanently dormant. No specific vulnerabilities were identified during the audit.

> **Final Recommendation:** Token holders should be aware that the contract's logic is immutable and cannot be changed. The renounced ownership means no single entity can alter the token's parameters or transfer mechanisms. Users should verify the contract address and its immutable nature to ensure they are interacting with the intended, fixed logic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `FlapTaxTokenV3` contract is an ERC-20 compliant token, implementing standard functionalities such as `transfer` and `balanceOf`. It is deployed as an EIP-1167 minimal clone, which means its… |
| **Governance / Economics** | 10/10 | Low | The contract's ownership has been renounced on-chain, which significantly reduces governance risk by preventing any single entity from controlling critical functions (7.5 Governance). This action… |
| **Upgrades** | 10/10 | Low | The `FlapTaxTokenV3` is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded (7.7 Upgrades). Although it inherits `Initializable` and `Upgradeable`… |

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

The ten largest holders own 14.1% of supply. Of that, 2.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.9% in wallets, 0.0% in other contracts. 1,305 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,305 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $245K (DexScreener, all pools). 24h trading volume $910K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $245K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7d04...7777`](https://bscscan.com/address/0x7d0443cddfc8e11af105f4fe44dd28c630237777) |
| **Network** | BNB Chain |
| **Price** | $0.005613 |
| **24h Volume** | $910.3K |
| **Liquidity** | $245.4K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 14.1% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 15285 buys / 7448 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9e83be1267e9a6d43bb7f3a8c0dc3c092ccae63e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dawg-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
