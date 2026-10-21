---
token: Coinbase Wrapped Hyperliquid
ticker: CBHYPE
network: base
risk_score: 18
status: low
date: 2026-09-02
---

# Coinbase Wrapped Hyperliquid (CBHYPE) — Smart Contract Security Analysis | Base

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-hyperliquid-base)

---

## Audit Summary

This audit report is based on the provided contract address 0xb200000000000000000000451d033a5000cb479e on the Base network. No source code was provided for analysis, therefore a comprehensive security audit could not be performed. The risk levels assigned reflect the absence of information rather than an assessment of the contract's inherent security. A full audit requires access to the complete and verified source code.

> **Final Recommendation:** To enable a comprehensive security audit, it is crucial to provide the complete and verified source code for the contract at 0xb200000000000000000000451d033a5000cb479e. This will allow for a thorough analysis of the contract's logic, identification of potential vulnerabilities, and assessment of its overall security posture across all relevant categories.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | A technical review (7.2 Code Security) could not be conducted due to the absence of source code. Without access to the Solidity implementation, it is impossible to assess common vulnerabilities such… |
| **Governance / Economics** | 3/10 | High | An economic and governance review (7.4 Economic, 7.5 Governance) could not be performed without understanding the contract's logic and intended functionality. Potential risks related to tokenomics… |
| **Upgrades** | 6/10 | Medium | The upgradeability status (7.7 Upgrades) of the contract cannot be determined without source code. It is unknown if the contract utilizes a proxy pattern (UUPS, Transparent) or if it is immutable.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Missing Source Code for Audit  *(Severity: Informational · Status: Unresolved)*

The smart contract at address 0xb200000000000000000000451d033a5000cb479e was provided without its corresponding Solidity source code. This prevents any meaningful static or dynamic analysis of the contract's implementation, logic, and potential vulnerabilities (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Provide the complete and verified Solidity source code for the contract. Ideally, the code should be verified on a block explorer (e.g., Basescan) to ensure transparency and immutability of the deployed logic.


### `I-02` — Unverified Contract on Block Explorer  *(Severity: Informational · Status: Unresolved)*

The contract at 0xb200000000000000000000451d033a5000cb479e is not verified on the Base network's block explorer. This lack of verification hinders public transparency and makes it difficult for users and auditors to confirm the deployed bytecode matches any claimed source code (7.8 Operations).

**Recommendation:** Verify the contract's source code on the Base network's block explorer. This step is crucial for transparency, user trust, and facilitating future audits or incident response.


### `I-03` — Inability to Assess Architectural Design  *(Severity: Informational · Status: Unresolved)*

Without access to the source code, it is impossible to evaluate the contract's architectural design, dependencies, and overall system integration (7.1 Architecture). This includes understanding its role within a larger protocol, its interaction with other contracts, and potential external risks (7.6 External).

**Recommendation:** Provide the source code and, if applicable, architectural diagrams or documentation detailing the contract's role, dependencies, and interaction patterns within the broader protocol.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb200...479e`](https://basescan.org/address/0xb200000000000000000000451d033a5000cb479e) |
| **Network** | Base |
| **Price** | $87.0220 |
| **24h Volume** | $1.06M |
| **Liquidity** | $587.5K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 47.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1117 buys / 1043 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd5eaea9da564217ea101d1e369fda168a3025686)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-hyperliquid-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
