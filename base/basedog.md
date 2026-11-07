---
token: BASEDOG
ticker: BASEDOG
network: base
risk_score: 53
status: medium
date: 2026-11-07
---

# BASEDOG (BASEDOG) — Smart Contract Security Analysis | Base

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/basedog-base)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security analysis. Users should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to distinguish between a legitimate project and a malicious one. Users should avoid providing liquidity or purchasing tokens until the contract is verified on a block explorer and audited by a reputable third party.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be evaluated due to lack of source code. 7.3 Access Control: Cannot be verified; potential for hidden minting or pausing functions exists. 7.6… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Tokenomics and tax structures are opaque. 7.5 Governance: Ownership privileges are unknown. Without source code, there is no assurance against rug-pull mechanisms or malicious economic… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract's upgradeability status cannot be determined. 7.8 Operations: Operational security is entirely dependent on the deployer's intent, which remains unverified. |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer. This prevents any security analysis of the contract's logic, including potential backdoors, minting functions, or malicious tax logic.

**Recommendation:** Verify the contract source code on the block explorer and perform a comprehensive security audit before any public interaction.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 30.1% of supply. What remains: 4.6% in wallets, 25.5% in other contracts. 559 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

559 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $71K (DexScreener, all pools). 24h trading volume $511K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $71K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa5dc...db14`](https://basescan.org/address/0xa5dc6bddbf8bb85b8f27bf083b9c1921e03fdb14) |
| **Network** | Base |
| **Price** | $0.0001506 |
| **24h Volume** | $511.0K |
| **Liquidity** | $71.0K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 6h |
| **Top-10 Holders** | 30.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 870 buys / 760 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x9d3810f364c7fd5dd6190fd4219af35a897a9b516c6e2067489b6efb8b6cbda0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/basedog-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
