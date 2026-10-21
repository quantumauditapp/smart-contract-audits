---
token: Ornn Exchange
ticker: ORNN
network: arbitrum
risk_score: 78
status: high
date: 2026-08-31
---

# Ornn Exchange (ORNN) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ornn-exchange-arb)

---

## Audit Summary

This audit report is based on the analysis of a contract deployed at 0x727c6fbfd4c6a1aaf256b863312d61a2f6c4da37 on the Arbitrum network. No source code was provided or verified for this contract, which severely limits the scope and depth of the security assessment. Therefore, no specific vulnerabilities could be identified, and the risk assessment is largely theoretical based on general best practices. Users should exercise extreme caution.

> **Final Recommendation:** It is strongly recommended that the contract's source code be verified on a block explorer to enable proper security analysis and community trust. Users should exercise extreme caution when interacting with unverified contracts, as their functionality and security properties cannot be independently confirmed. Always prioritize transparency and auditability in smart contract deployments to mitigate unknown risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Due to the absence of verified source code, a comprehensive technical security analysis (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) could not be performed. The bytecode alone does not… |
| **Governance / Economics** | 1/10 | High | The economic and governance aspects (7.4 Economic, 7.5 Governance) of the contract cannot be assessed without access to its source code and associated documentation. It is impossible to determine if… |
| **Upgrades** | 6/10 | Medium | Without source code, it is impossible to determine if the contract implements any upgradeability patterns (7.7 Upgrades) or if it is part of a larger proxy architecture. This lack of information… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Lack of Verified Source Code  *(Severity: Informational · Status: Unresolved)*

The source code for the contract at 0x727c6fbfd4c6a1aaf256b863312d61a2f6c4da37 is not publicly verified on the Arbitrum block explorer. This prevents a thorough security audit and makes it impossible to ascertain the contract's intended functionality, security mechanisms, and potential vulnerabilities.

**Recommendation:** The contract deployer should verify the source code on the block explorer. This enhances transparency, allows for community review, and enables security professionals to conduct proper assessments.


### `I-02` — Undetermined Contract Functionality and Purpose  *(Severity: Informational · Status: Unresolved)*

Without verified source code, the specific functionality, purpose, and business logic of the contract cannot be determined. This lack of clarity makes it impossible to assess its intended behavior, potential interactions with other protocols, or adherence to any specific ERC standards (e.g., ERC-20, ERC-721).

**Recommendation:** Provide comprehensive documentation detailing the contract's purpose, functionality, and any associated protocol architecture. This information, coupled with verified source code, is crucial for user understanding and security analysis.


### `I-03` — Absence of Public Documentation and Audit History  *(Severity: Informational · Status: Unresolved)*

There is no readily available public documentation or record of prior security audits for this contract. This absence limits the ability to understand the project's security posture, design considerations, and any known issues or resolutions.

**Recommendation:** Publish detailed documentation, including architectural overviews, functional specifications, and any past audit reports. This transparency builds trust and provides essential context for users and security researchers.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x727c...da37`](https://arbiscan.io/address/0x727c6fbfd4c6a1aaf256b863312d61a2f6c4da37) |
| **Network** | Arbitrum |
| **Price** | $0.1293 |
| **24h Volume** | $142.4K |
| **Liquidity** | $95.0K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 94.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1143 buys / 279 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x08b072f918ebaa6801d7f7d912ee95e86677e3c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ornn-exchange-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
