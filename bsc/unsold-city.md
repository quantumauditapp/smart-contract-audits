---
token: Unsold City
ticker: UNSOLD
network: bsc
risk_score: 45
status: medium
date: 2026-10-23
---

# Unsold City (UNSOLD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unsold-city-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is an ERC-20 token deployed via EIP-1167 minimal clone pattern. The contract implements a state-machine based migration mechanism controlled by the owner. No critical vulnerabilities were identified during the analysis of the transfer logic and privileged migration functions. The protocol relies on centralized ownership for state transitions, which is standard for this architecture.

> **Final Recommendation:** The protocol is structurally sound for its intended use case. Given the centralized control over migration states, it is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks.

Ensure that the owner's private keys are managed with institutional-grade security practices. Monitor the migration process closely, as the transition to 'TaxEnforcedAntiFarmer' state significantly impacts token utility and holder experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows the EIP-1167 standard, ensuring immutable implementation logic. 7.1 Architecture is robust for a token contract, while 7.2 Code Security is maintained through standard… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance risks are centralized under the contract owner. The owner has the authority to trigger migration states that fundamentally alter transfer behavior, such as enforcing… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not applicable as the contract is an EIP-1167 minimal clone. The implementation logic is fixed at deployment and cannot be altered. This eliminates risks associated with malicious… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 77.0% of supply. What remains: 16.9% in wallets, 60.1% in other contracts. The deployer/owner wallet itself holds 46.3%. A holder that also controls the contract can sell into its own liquidity. 62 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

62 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $49K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7125...7777`](https://bscscan.com/address/0x7125b07dee00b9cc68ef4c8ff8e5081ff71e7777) |
| **Network** | BNB Chain |
| **Price** | $0.00001603 |
| **24h Volume** | $49.0K |
| **Liquidity** | $18.0K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 7h |
| **Top-10 Holders** | 77.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 388 buys / 216 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x41081f5956045a3a68d14bd8dbdb1e381f7b18c9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unsold-city-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
