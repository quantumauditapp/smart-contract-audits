---
token: YIYI
ticker: 一一
network: bsc
risk_score: 45
status: medium
date: 2026-10-12
---

# YIYI (一一) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yiyi-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an ERC-20 token deployed as an EIP-1167 minimal clone, ensuring its logic is immutable. The contract includes standard ERC-20 functionality and an OwnableUpgradeable pattern, retaining administrative control by a single owner. No specific technical vulnerabilities were identified by static analysis, but the owner's ability to modify transfer parameters introduces a centralized governance risk.

> **Final Recommendation:** To enhance decentralization and reduce reliance on a single entity, consider implementing a multi-signature wallet or a time-locked governance mechanism for critical functions that modify token economics, such as `startMigration` and `finalizeMigration`. This would distribute control and introduce a delay for sensitive operations, providing greater transparency and security for token holders. Additionally, ensure robust operational security practices are in place for the owner's private key.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control: The contract is an EIP-1167 minimal clone, meaning its implementation is fixed and cannot be upgraded, which enhances security by preventing… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic, 7.5 Governance: The contract owner retains significant control over the token's economic parameters through the poolState variable. Functions like startMigration() and… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The FlapTaxTokenV3 is deployed as an EIP-1167 minimal clone, which means its bytecode fixes the implementation permanently. This design choice explicitly prevents any future upgrades or… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.2% of supply. What remains: 7.5% in wallets, 91.7% in other contracts. 37 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

37 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $36K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x770f...7777`](https://bscscan.com/address/0x770f732c39fdab1dbb098ed8672f4b16c0e87777) |
| **Network** | BNB Chain |
| **Price** | $0.00000503 |
| **24h Volume** | $35.5K |
| **Liquidity** | $10.1K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 3h |
| **Top-10 Holders** | 99.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 386 buys / 312 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3108aefe6aa90376cb549970622587690c7e672d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yiyi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
