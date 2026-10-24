---
token: one life, its worth an attempt
ticker: WORTH
network: base
risk_score: 56
status: medium
date: 2026-10-24
---

# one life, its worth an attempt (WORTH) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-c378)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, minting capabilities, tax mechanisms, or liquidity lock status.

> **Final Recommendation:** Do not interact with this contract. The absence of verified source code is a primary indicator of high-risk assets, often associated with malicious intent or lack of developer accountability. Verify the contract on the block explorer and perform a thorough audit before considering any capital allocation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be verified. 7.6 External: Unknown integration risks. |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Potential for hidden minting, blacklisting, or honeypot mechanisms. 7.5 Governance: No insight into ownership or administrative privileges. 7.8 Operations: High operational risk due to… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Cannot determine if the contract is immutable or utilizes a proxy pattern. Without source code, the risk of hidden upgradeability or rug-pull vectors remains at maximum. |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for backdoors, minting functions, or malicious tax logic.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $321K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $85K of DEX liquidity across 18 pools. Launch: 69 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb200...8f01`](https://basescan.org/address/0xb200000000000000000000585fd80c20af698f01) |
| **Network** | Base |
| **Price** | $0.000349 |
| **24h Volume** | $317.4K |
| **Liquidity** | $80.6K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 2mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1380 buys / 1229 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6cf637a82362d304dfa56a6387fc8f909ec0008ec520ee5fb999506d9b1f3514)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-c378)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
