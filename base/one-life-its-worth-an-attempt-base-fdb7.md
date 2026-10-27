---
token: one life, its worth an attempt
ticker: WORTH
network: base
risk_score: 62
status: medium
date: 2026-10-27
---

# one life, its worth an attempt (WORTH) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-fdb7)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for inspection, preventing any technical analysis of its logic, security, or functionality. Investors should exercise extreme caution as unverified contracts may contain malicious backdoors, honeypot mechanisms, or lack basic security safeguards.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, there is no assurance that the contract functions as intended or that it is free from malicious intent. 

Prior to any engagement, verify the contract on the block explorer and ensure a third-party security audit has been conducted. If the developers refuse to verify the code, treat the asset as a high-risk or potentially fraudulent project.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be evaluated due to the lack of verified source code. 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, and 7.6 External interactions remain entirely opaque.… |
| **Governance / Economics** | 3/10 | High | Economic and governance parameters are hidden from public view. 7.4 Economic and 7.5 Governance metrics cannot be assessed, meaning potential risks like minting backdoors or centralized control… |
| **Upgrades** | 6/10 | Medium | The upgradeability status (7.7 Upgrades) is unknown as the contract is not verified. It is impossible to determine if the contract uses a proxy pattern or if the logic can be altered by an owner. 7.8… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, rendering it impossible to audit for security vulnerabilities or malicious backdoors.

**Recommendation:** Verify the contract source code on the block explorer immediately to provide transparency to users and allow for security assessments.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.9% of supply. What remains: 37.9% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 15.1%. 664 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

664 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $142K (DexScreener, all pools). 24h trading volume $997K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $142K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x25e1...631f`](https://basescan.org/address/0x25e1c201a5e92a59bc6a89d690e8267d6b06631f) |
| **Network** | Base |
| **Price** | $0.0005101 |
| **24h Volume** | $997.3K |
| **Liquidity** | $142.5K |
| **Volume / Liquidity** | 7.0× |
| **Token Age** | 23h |
| **Top-10 Holders** | 37.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 979 buys / 627 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x068007b60a9f23c436eac0bf784c8c6f9bf9d402b0e7313145384f908aaa4d28)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-fdb7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
