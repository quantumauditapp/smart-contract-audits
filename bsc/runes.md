---
token: RUNES
ticker: RUNES
network: bsc
risk_score: 50
status: medium
date: 2026-10-06
---

# RUNES (RUNES) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/runes-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, meaning its logic is immutable. It includes owner-controlled functions to manage migration states which affect transfer amounts and fees. No critical or high-severity vulnerabilities were identified during this audit.

> **Final Recommendation:** Ensure the private keys controlling the owner address are secured with robust multi-signature or hardware wallet solutions to prevent unauthorized access and manipulation of the token's migration states. Regularly review the contract's operational parameters and any off-chain processes that interact with the owner-controlled functions to maintain system integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The FlapTaxTokenV3 contract implements the ERC-20 standard, providing essential token functionalities like `transfer` and `balanceOf`. It is deployed as an EIP-1167 minimal clone, ensuring its… |
| **Governance / Economics** | 3/10 | High | The contract retains ownership, allowing the deployer or a designated address to control key functions (7.3 Access Control). The owner can call `startMigration()` and `finalizeMigration()` to… |
| **Upgrades** | 6/10 | Medium | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed at deployment and cannot be upgraded (7.7 Upgrades). This design choice eliminates… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 84.0% of supply. Of that, 4.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 7.1% in wallets, 72.9% in other contracts. The deployer/owner wallet itself holds 68.0%. A holder that also controls the contract can sell into its own liquidity. 86 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

86 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $68K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5153...7777`](https://bscscan.com/address/0x5153110809c5d8335605a9b0c143a1c93be17777) |
| **Network** | BNB Chain |
| **Price** | $0.00000842 |
| **24h Volume** | $67.7K |
| **Liquidity** | $13.4K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | 84.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 686 buys / 536 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xde95a0fad9777b29f61275bd02abd5f1cf2f6fb2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/runes-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
