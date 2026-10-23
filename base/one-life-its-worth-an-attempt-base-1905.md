---
token: one life, its worth an attempt
ticker: WORTH
network: base
risk_score: 66
status: high
date: 2026-10-23
---

# one life, its worth an attempt (WORTH) — Smart Contract Security Analysis | Base

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-1905)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract until the source code is verified on the block explorer. Perform thorough due diligence on the project team and verify the contract address through official, trusted channels before considering any capital allocation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be verified. 7.6 External: Unknown dependencies. |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: Tokenomics and tax logic are hidden. 7.5 Governance: Administrative privileges are unknown. 7.8 Operations: Operational security is impossible to evaluate without code access. |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: It is unknown if the contract is upgradeable or contains proxy patterns. Without source code, hidden upgrade paths or logic changes cannot be ruled out. |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 4 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for vulnerabilities, backdoors, or malicious logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 48.4% of supply. What remains: 48.4% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 22.3%. A holder that also controls the contract can sell into its own liquidity. 754 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

754 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $95K (DexScreener, all pools). 24h trading volume $817K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $95K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1db2...bff6`](https://basescan.org/address/0x1db216807d8820b98d0237c075b8bf60f432bff6) |
| **Network** | Base |
| **Price** | $0.0002392 |
| **24h Volume** | $817.3K |
| **Liquidity** | $94.9K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 10h |
| **Top-10 Holders** | 48.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1323 buys / 964 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xed4a3a1a511c3f8c68bf3fa41f8cba2d213c156c5a72313d53d0577bd2192b51)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-1905)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
