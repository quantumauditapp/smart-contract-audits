---
token: 😬
ticker: 😬
network: bsc
risk_score: 46
status: medium
date: 2026-10-27
---

# 😬 (😬) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-1bdee7-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom migration and tax logic. The architecture is immutable, meaning the logic cannot be upgraded after deployment. The owner maintains significant control over the token's state, specifically regarding migration phases and tax enforcement. No critical vulnerabilities were identified during the static analysis of the provided code map.

> **Final Recommendation:** The protocol is well-structured for its intended purpose. We recommend that the owner consider transitioning to a multi-signature wallet or a decentralized governance contract to manage the privileged migration functions, reducing the risk associated with a single point of failure. 

Additionally, ensure that all migration parameters are clearly documented and communicated to the community before execution to maintain transparency regarding the tax and anti-farmer enforcement mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20 and access control, ensuring robust base functionality. 7.1 Architecture follows the EIP-1167 standard, providing gas-efficient… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are concentrated in the owner's ability to trigger migration phases. The startMigration and finalizeMigration functions allow the owner to unilaterally alter the… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not applicable as the contract is deployed as an EIP-1167 minimal clone, which is inherently immutable. The implementation address is fixed at deployment, preventing any future logic… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 76.5% of supply. What remains: 15.7% in wallets, 60.8% in other contracts. The deployer/owner wallet itself holds 59.1%. A holder that also controls the contract can sell into its own liquidity. 87 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

87 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $42K (DexScreener, all pools).

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
| **Contract** | [`0x6be8...7777`](https://bscscan.com/address/0x6be8f023b73447dd341d9910c3c4661b59927777) |
| **Network** | BNB Chain |
| **Price** | $0.00000877 |
| **24h Volume** | $42.1K |
| **Liquidity** | $12.6K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 3h |
| **Top-10 Holders** | 76.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 485 buys / 292 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x1406403227d474c048146c14fa8b887726bc36c1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-1bdee7-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
