---
token: Sperax
ticker: SPA
network: arbitrum
risk_score: 42
status: medium
date: 2026-09-24
---

# Sperax (SPA) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sperax-arb)

---

## Audit Summary

This audit covers a partial Solidity source code for an ERC20 token, including Pausable and MintPausable functionalities. The provided code is truncated, preventing a comprehensive security assessment. Key concerns include unverified access control for critical administrative functions and inherent centralization risks associated with pausing and minting capabilities. The contract utilizes SafeMath for arithmetic safety and adheres to standard ERC20 patterns. However, the incomplete nature of the code means a full security posture cannot be definitively determined.

> **Final Recommendation:** It is critical to provide the complete and untruncated source code for a comprehensive security audit. Without the full code, especially the implementation of access control for administrative functions, the contract's security posture cannot be fully verified. Ensure that all critical administrative functions (pausing, unpausing, minting, burning) are protected by robust access control mechanisms, such as a multi-signature wallet or a well-defined governance process. Clearly document the roles and responsibilities of addresses with administrative privileges.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a standard ERC20 token with `SafeMath` for arithmetic safety (7.2 Code Security). It includes `Pausable` and `MintPausable` features, which are common patterns for… |
| **Governance / Economics** | 4/10 | Medium | The contract includes `Pausable` and `MintPausable` functionalities, along with `_mint` and `_burn` capabilities, which introduce centralization points (7.4 Economic). A privileged entity or set of… |
| **Upgrades** | 6/10 | Medium | Based on the provided information and the prefill `is_proxy: false`, the contract does not appear to be upgradeable (7.7 Upgrades). This eliminates risks associated with proxy patterns, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 49.9% |
| **Top-3 Unlocked** | ⚠️ 93.6% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 1 Informational_

### `H-01` — Unverified Access Control for Critical Functions  *(Severity: High · Status: Unresolved)*

The provided code snippets for `Pausable` and `MintPausable` define `internal virtual` functions (`_pause`, `_unpause`, `_mintPause`, `_mintUnpause`, `_mint`, `_burn`). The actual public/external functions that call these, and their associated access control mechanisms (e.g., `onlyOwner`, role-based), are not present in the provided code. Without the full contract, it's impossible to verify if these critical administrative functions are adequately protected. The prefill `ownership_renounced: true` further raises concerns, as it implies that if an `Ownable` pattern was used, these functions might now be uncallable, leading to a denial of service for administrative actions, or, if not properl…

**Recommendation:** Provide the complete source code for the contract, including all derived contracts and their access control implementations. Ensure that all administrative functions are protected by appropriate access control (e.g., `onlyOwner`, a multi-signature wallet, or a robust governance mechanism). If ownership has been renounced, confirm that a secure and functional alternative access control or governance system is in place for these critical operations.


### `H-02` — Incomplete Code Prevents Comprehensive Audit  *(Severity: High · Status: Unresolved)*

The provided source code is truncated, specifically for the `MintPausable` contract. This prevents a complete and thorough security assessment of the entire contract's logic, interactions, and potential vulnerabilities. Any findings are based solely on the partial code available, and a full security posture cannot be definitively determined.

**Recommendation:** Provide the complete and untruncated source code for all contracts involved in the system to enable a comprehensive security audit. This includes all inherited contracts and any external dependencies.


### `M-01` — Centralization Risk from Administrative Controls  *(Severity: Medium · Status: Unresolved)*

The contract incorporates `Pausable` and `MintPausable` functionalities, along with `_mint` and `_burn` capabilities. These features inherently introduce centralization points, as a privileged entity (or set of entities) can halt token transfers, prevent minting, or adjust the total supply. The security and integrity of the token ecosystem depend heavily on the trustworthiness and security of the controlling address(es).

**Recommendation:** Clearly document the administrative roles and their associated privileges. Consider implementing a multi-signature wallet or a decentralized governance mechanism to control these critical functions, thereby distributing control and reducing single points of failure. Ensure that the controlling address(es) are highly secured.


### `I-01` — Use of Older Solidity Version  *(Severity: Informational · Status: Unresolved)*

The contract uses Solidity versions `0.6.x`. While `SafeMath` is correctly implemented to prevent integer overflows/underflows, Solidity versions 0.8.0 and higher include built-in overflow and underflow checks by default. This means that explicit `SafeMath` library usage is no longer strictly necessary for basic arithmetic operations in newer versions.

**Recommendation:** Consider migrating to Solidity 0.8.0 or a newer version. This would allow for the removal of the `SafeMath` library, simplifying the codebase and leveraging the compiler's native overflow/underflow protection. Thorough testing would be required after such a migration.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5575...ad4b`](https://arbiscan.io/address/0x5575552988a3a80504bbaeb1311674fcfd40ad4b) |
| **Network** | Arbitrum |
| **Price** | $0.002882 |
| **24h Volume** | $48.2K |
| **Liquidity** | $56.0K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 4y |
| **Top-10 Holders** | 82.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 413 buys / 377 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x08e0b47588e1ac22bc0f8b4afaa017aaf273f85e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sperax-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-24*
