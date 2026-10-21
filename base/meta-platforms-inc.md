---
token: Meta Platforms Inc.
ticker: METAC
network: base
risk_score: 28
status: low
date: 2026-08-30
---

# Meta Platforms Inc. (METAC) — Smart Contract Security Analysis | Base

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meta-platforms-inc-base)

---

## Audit Summary

This audit report is based on an unverified contract at address 0xb2000000000000000000008bc8786b856e61707c on the Base network. No source code was provided for analysis. Therefore, a comprehensive security assessment of the contract's logic, architecture, and potential vulnerabilities could not be performed. The risk levels and findings are primarily informational, highlighting the inherent risks of interacting with unverified contracts.

> **Final Recommendation:** It is strongly recommended that users exercise extreme caution when interacting with unverified smart contracts. Before any interaction, ensure the contract's source code is publicly verified on block explorers and has undergone independent security audits. For developers, always verify your contract source code to provide transparency and build trust within the community. Consider implementing robust access control and emergency mechanisms, even for non-upgradeable contracts, to mitigate unforeseen operational risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1 Architecture) and code security (7.2 Code Security) of this contract cannot be assessed due to the absence of verifiable source code. While a well-designed contract… |
| **Governance / Economics** | 3/10 | High | Without source code, the economic model (7.4 Economic) and governance structure (7.5 Governance) of the contract cannot be evaluated. A robust system would typically feature transparent tokenomics… |
| **Upgrades** | 6/10 | Medium | The provided information indicates the contract is not a proxy (`is_proxy: false`), suggesting it is not designed for upgradeability (7.7 Upgrades). This inherently limits the risk associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Lack of Source Code Verification  *(Severity: Informational · Status: Unresolved)*

The smart contract deployed at 0xb2000000000000000000008bc8786b856e61707c on the Base network is not verified on the block explorer. This means its Solidity source code is not publicly available or linked to the deployed bytecode. Users cannot independently review the contract's logic, functionality, or security properties. This significantly increases the risk of interacting with the contract, as its behavior is opaque and could potentially contain malicious code or critical vulnerabilities (7.2 Code Security).

**Recommendation:** The contract deployer should immediately verify the source code on the Base block explorer. This provides transparency, allows for community review, and is a fundamental step in establishing trust for any public smart contract.


### `I-02` — Undetermined Contract Functionality and Architecture  *(Severity: Informational · Status: Unresolved)*

Without access to the source code, the specific functionality, purpose, and architectural design of the contract cannot be determined (7.1 Architecture). It is impossible to ascertain if it's a token, a DeFi protocol component, a governance contract, or something else entirely. This lack of clarity prevents any assessment of its intended use, potential attack vectors, or adherence to best practices for its presumed type.

**Recommendation:** Provide the source code and a clear description of the contract's intended functionality and architectural overview. This context is crucial for any security assessment and for users to understand the contract's role within a larger ecosystem.


### `I-03` — Unassessable Access Control and Economic Risks  *(Severity: Informational · Status: Unresolved)*

The absence of source code makes it impossible to evaluate the contract's access control mechanisms (7.3 Access Control) or its economic model (7.4 Economic). Critical questions regarding who can perform privileged operations, potential centralization risks, or how value is managed and distributed remain unanswered. This creates a high risk of unknown administrative backdoors, owner-controlled functions, or economic exploits that could lead to loss of funds or manipulation (7.5 Governance, 7.8 Operations).

**Recommendation:** Full transparency of the source code is required to assess and mitigate access control and economic risks. Implement robust, multi-signature based access control for critical functions and ensure economic parameters are transparent and, where appropriate, decentralized or governed by a community.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb200...707c`](https://basescan.org/address/0xb2000000000000000000008bc8786b856e61707c) |
| **Network** | Base |
| **Price** | $614.8800 |
| **24h Volume** | $3.22M |
| **Liquidity** | $830.3K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 81.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2923 buys / 2318 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xeaf57753bc382e0324a1d43f72e7027705a2273e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meta-platforms-inc-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
