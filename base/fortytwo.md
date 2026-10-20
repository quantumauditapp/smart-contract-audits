---
token: Fortytwo
ticker: FTW
network: base
risk_score: 80
status: high
date: 2026-10-15
---

# Fortytwo (FTW) — Smart Contract Security Analysis | Base

> **Risk Score: 80/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fortytwo-base)

---

## Audit Summary

This report is based on a security audit of the contract at 0x23c26bc380475e4b52aa304607662fbf5e9aa8a3 on the Base network. No Solidity source code was provided for analysis, therefore, a comprehensive security assessment could not be performed. The findings below are general informational points regarding best practices and missing information.

> **Final Recommendation:** To ensure the security and transparency of the protocol, it is crucial to provide the full Solidity source code for all deployed contracts. This enables a thorough audit for vulnerabilities, adherence to best practices, and proper verification on block explorers. Without source code, users and auditors cannot independently verify the contract's intended functionality or security posture, posing a significant trust and security risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Due to the absence of Solidity source code (7.2 Code Security), a detailed technical analysis of the contract's architecture (7.1 Architecture) and implementation was not possible. Without the code… |
| **Governance / Economics** | 1/10 | High | Without the contract's source code, it is impossible to assess its economic model (7.4 Economic) or governance mechanisms (7.5 Governance). This includes evaluating tokenomics, fee structures, or… |
| **Upgrades** | 5/10 | Medium | The contract's upgradeability status (7.7 Upgrades) cannot be determined without its source code. It is unknown if it implements a proxy pattern (e.g., UUPS, Transparent) or if it is immutable. This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 8 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0x03c8…e5a2 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — Missing Source Code for Verification  *(Severity: Informational · Status: Unresolved)*

The Solidity source code for the contract at 0x23c26bc380475e4b52aa304607662fbf5e9aa8a3 was not provided for analysis. This prevents a comprehensive security audit and independent verification of the contract's logic and functionality by users and auditors.

**Recommendation:** Publish the full Solidity source code for the contract on a block explorer (e.g., Basescan) and provide it for security audits. Ensure that the deployed bytecode matches the compiled source code.


### `I-02` — Inability to Assess Technical Vulnerabilities  *(Severity: Informational · Status: Unresolved)*

Without the source code, it is impossible to identify common technical vulnerabilities such as reentrancy, integer overflows/underflows, access control flaws, denial-of-service vectors, or other logic errors (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Provide the source code to allow for a detailed technical security review. This includes analysis of all functions, state variables, and external interactions.


### `I-03` — Uncertainty Regarding Upgradeability and Operational Risks  *(Severity: Informational · Status: Unresolved)*

The absence of source code makes it impossible to determine if the contract is upgradeable (e.g., via a proxy pattern) or immutable (7.7 Upgrades). Consequently, potential risks associated with upgrade mechanisms, administrative privileges, or operational procedures (7.8 Operations) cannot be assessed.

**Recommendation:** Clearly document the contract's upgradeability status and any associated administrative roles. If upgradeable, provide the source code for all proxy and implementation contracts.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.3% of supply. Of that, 1.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 67.7% in wallets, 18.1% in other contracts. 1,742 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,742 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $72K (DexScreener, all pools). 24h trading volume $100K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $72K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x23c2...a8a3`](https://basescan.org/address/0x23c26bc380475e4b52aa304607662fbf5e9aa8a3) |
| **Network** | Base |
| **Price** | $0.01148 |
| **24h Volume** | $100.4K |
| **Liquidity** | $72.0K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 22h |
| **Top-10 Holders** | 87.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1467 buys / 263 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x0d1959a640930f63433a5e3e5a2343e2233303f6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fortytwo-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
