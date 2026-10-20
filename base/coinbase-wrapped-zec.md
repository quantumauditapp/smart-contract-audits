---
token: Coinbase Wrapped ZEC
ticker: CBZEC
network: base
risk_score: 33
status: low
date: 2026-09-25
---

# Coinbase Wrapped ZEC (CBZEC) — Smart Contract Security Analysis | Base

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-zec-base)

---

## Audit Summary

This report is based on an audit of a contract deployed at 0xb2000000000000000000008501b13360000cb2ec on the Base network. No source code was provided for analysis, limiting the scope of this audit to publicly available on-chain information and general security considerations. Therefore, specific code-level vulnerabilities cannot be identified.

> **Final Recommendation:** It is strongly recommended to only interact with smart contracts that have publicly verified source code. Users should exercise extreme caution when interacting with this contract due to the inability to audit its functionality and security. For developers, always verify your contract source code on block explorers to provide transparency and enable community security reviews.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Without access to the contract's source code (7.2 Code Security), a comprehensive technical security assessment is impossible. The lack of verification means the deployed bytecode cannot be… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4 Economic) and governance structure (7.5 Governance) of the contract cannot be determined without source code. This introduces a high level of uncertainty regarding potential… |
| **Upgrades** | 5/10 | Medium | The contract is not identified as a proxy (is_proxy: false), suggesting it is not directly upgradeable (7.7 Upgrades). This reduces the risk associated with upgrade mechanisms, as there is no upgrade… |

## Security Findings

_⚪ 4 Informational_

### `I-01` — Source Code Not Provided for Audit  *(Severity: Informational · Status: Unresolved)*

The primary source code for the contract at `0xb2000000000000000000008501b13360000cb2ec` was not provided for this audit. This severely limits the scope of the security review, as detailed analysis of the contract's logic, potential vulnerabilities (7.2 Code Security), and adherence to best practices cannot be performed.

**Recommendation:** Always provide the full, verified source code for all contracts intended for audit. This enables a thorough security assessment and builds trust with users and the community.


### `I-02` — Contract Source Code Not Verified on Block Explorer  *(Severity: Informational · Status: Unresolved)*

The contract at `0xb2000000000000000000008501b13360000cb2ec` is not verified on the Base network block explorer (is_verified: false). This means the deployed bytecode cannot be publicly matched against its corresponding source code, making it impossible for users, auditors, or other protocols to independently verify its intended functionality or security properties. This impacts transparency and trust (7.8 Operations).

**Recommendation:** Verify the contract's source code on the Base network block explorer. This is a fundamental step for transparency and allows for public scrutiny and understanding of the contract's operations.


### `I-03` — Unknown Contract Functionality and Purpose  *(Severity: Informational · Status: Unresolved)*

Without the source code, the specific functionality, purpose, and intended behavior of the contract at `0xb2000000000000000000008501b13360000cb2ec` remain unknown. This prevents any assessment of its architecture (7.1 Architecture), economic model (7.4 Economic), or potential interactions with other protocols (7.6 External).

**Recommendation:** Clearly document the contract's intended functionality, design principles, and any external dependencies. Providing source code is the best way to convey this information.


### `I-04` — Inability to Assess Access Control Mechanisms  *(Severity: Informational · Status: Unresolved)*

The absence of source code makes it impossible to analyze the access control mechanisms implemented within the contract (7.3 Access Control). Critical functions might be callable by unauthorized entities, or privileged roles might be poorly secured, leading to potential misuse or loss of funds.

**Recommendation:** Implement robust access control using established patterns (e.g., OpenZeppelin's Ownable or AccessControl). Ensure all privileged functions are adequately protected and roles are clearly defined and managed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb200...b2ec`](https://basescan.org/address/0xb2000000000000000000008501b13360000cb2ec) |
| **Network** | Base |
| **Price** | $1,583.2400 |
| **24h Volume** | $1.40M |
| **Liquidity** | $878.4K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1669 buys / 1487 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0fc47c17af86078d809358db1b4db2debc988566)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-zec-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
