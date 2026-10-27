---
token: one life, its worth an attempt
ticker: WORTH
network: base
risk_score: 78
status: high
date: 2026-10-27
---

# one life, its worth an attempt (WORTH) — Smart Contract Security Analysis | Base

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-3b3a)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is unavailable for inspection, and no automated or manual security analysis could be performed. Investors should exercise extreme caution as unverified contracts often lack transparency regarding ownership, minting capabilities, or transfer restrictions.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, there is no way to ensure the safety of funds or the integrity of the token's logic. Avoid providing liquidity or purchasing tokens associated with this address until the developer verifies the source code on the block explorer and provides a transparent audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture and 7.2 Code Security cannot be assessed due to the lack of source code. 7.3 Access Control and 7.6 External interactions are opaque. Without verification, the contract may contain… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance parameters are unknown. There is no documentation regarding tokenomics, supply caps, or administrative control. The lack of transparency poses a significant risk of… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades and 7.8 Operations are entirely opaque. It is impossible to determine if the contract is immutable or if it utilizes a proxy pattern that allows for arbitrary logic changes. Users should… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · ⚪ 4 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, preventing any security assessment.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security review.


### `H-01` — Lack of Transparency  *(Severity: High · Status: Unresolved)*

The absence of verified code hides potential malicious functions such as blacklisting, minting, or tax manipulation.

**Recommendation:** Publish the source code and provide documentation for all administrative functions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 52.6% of supply. What remains: 52.6% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 37.8%. A holder that also controls the contract can sell into its own liquidity. 766 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

766 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $272K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x91a1...fc22`](https://basescan.org/address/0x91a1d69dcbd3e620f50b985f247149eb4daafc22) |
| **Network** | Base |
| **Price** | $0.00008069 |
| **24h Volume** | $272.2K |
| **Liquidity** | $49.5K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | 52.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1143 buys / 794 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x222a366d14f59b24be888d3de3381fcefaed701f888043acfc06499a876fc80e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/one-life-its-worth-an-attempt-base-3b3a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
