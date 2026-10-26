---
token: The Stonks Exchange
ticker: STONKEX
network: base
risk_score: 57
status: medium
date: 2026-10-26
---

# The Stonks Exchange (STONKEX) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-stonks-exchange-base-1b01)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is inaccessible, preventing a technical security audit. Investors should exercise extreme caution as the lack of transparency precludes verification of ownership, tax mechanisms, or minting capabilities.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, it is impossible to determine if the contract contains malicious functions such as honeypot mechanisms, unauthorized minting, or blacklisting capabilities. Prioritize assets with verified, audited, and transparent codebases.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified due to lack of source code. 7.3 Access Control: Cannot be verified. 7.6 External: Cannot be verified. |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Tokenomics and tax logic are hidden. 7.5 Governance: Administrative controls are unknown. The inability to inspect the contract poses a severe risk of rug-pulls or hidden backdoors. |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Proxy status cannot be confirmed. 7.8 Operations: Operational security is impossible to assess without code visibility. |

## Security Findings

_🔴 1 Critical · ⚪ 4 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to audit for security vulnerabilities or malicious logic.

**Recommendation:** Publish the source code on the block explorer and undergo a professional security audit before requesting user interaction.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $117K (DexScreener, all pools). 24h trading volume $934K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $117K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6365...e44d`](https://basescan.org/address/0x6365c82ab575b52f297c3a8a235aa19b1571e44d) |
| **Network** | Base |
| **Price** | $0.0003579 |
| **24h Volume** | $933.6K |
| **Liquidity** | $117.1K |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1115 buys / 839 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe189ca7f3382ac8645db65e03910b47fc45cd1ce5b72f09ba13398fce421ca2b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-stonks-exchange-base-1b01)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
