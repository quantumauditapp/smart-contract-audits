---
token: Tajir
ticker: TJR
network: ethereum
risk_score: 60
status: medium
date: 2026-10-07
---

# Tajir (TJR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tajir-eth)

---

## Audit Summary

The TajirToken contract is an upgradeable ERC-20 token utilizing the UUPS proxy pattern and OpenZeppelin's AccessControl for administrative functions. No critical or high-severity vulnerabilities were identified during this audit based on the provided code map and analysis.

> **Final Recommendation:** Ensure that all administrative roles, particularly those with upgrade and role management capabilities, are secured with multi-signature wallets to prevent single points of failure. Establish a robust process for managing and executing upgrades, including thorough testing in a staging environment before deployment to production. Regularly review access control roles and permissions to adhere to the principle of least privilege.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a standard ERC-20 token with burn functionality, inheriting from OpenZeppelin's `ERC20BurnableUpgradeable`. It uses `AccessControlUpgradeable` for managing administrative… |
| **Governance / Economics** | 2/10 | High | Access control is robustly implemented using OpenZeppelin's `AccessControlUpgradeable` pattern (7.3 Access Control). Administrative functions like `grantRole`, `revokeRole`, and `renounceRole` are… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS (Universal Upgradeable Proxy Standard) pattern, allowing for future upgrades of the implementation logic (7.1 Architecture). The `upgradeToAndCall` function, which… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 0.0% in wallets, 100.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tajir (TJR). 1 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $79K (CoinGecko, all markets, daily snapshot). 24h trading volume $67K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $98K of DEX liquidity across 1 pools. Launch: 7 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9d98...c110`](https://etherscan.io/address/0x9d98c61d1136cfa2ac263be355350c97ca41c110) |
| **Network** | Ethereum |
| **Price** | $0.3626 |
| **24h Volume** | $67.1K |
| **Liquidity** | $97.9K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 7d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 626 buys / 585 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4d12b3947d0cf7124012d3c4321d4d2dda8803f7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tajir-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
