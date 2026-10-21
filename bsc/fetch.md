---
token: Fetch
ticker: FET
network: bsc
risk_score: 39
status: medium
date: 2026-09-22
---

# Fetch (FET) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fetch-bsc)

---

## Audit Summary

This audit covers a partial Solidity code snippet, primarily consisting of OpenZeppelin standard libraries (EnumerableSet, Address, SafeMath, Context, AccessControl) and the beginning of an ERC20 token implementation. The visible code demonstrates high adherence to established security patterns and best practices. Due to the incomplete nature of the provided source, a comprehensive security assessment of the full ERC20 token logic and its interactions cannot be performed.

> **Final Recommendation:** It is crucial to conduct a full audit of the complete contract source code, including all ERC20 functions and any custom logic, to ensure comprehensive security coverage. Consider upgrading the Solidity compiler to a more recent version (e.8.x) to benefit from newer language features and security enhancements. Ensure that all administrative roles are assigned to trusted, multi-signature wallets to minimize single points of failure and enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture leverages well-vetted OpenZeppelin libraries (7.1 Architecture), including EnumerableSet, Address, SafeMath, and AccessControl. Code security (7.2 Code Security) is… |
| **Governance / Economics** | 4/10 | Medium | The contract implements a robust role-based access control system using OpenZeppelin's AccessControl (7.3 Access Control). This allows for granular permission management, with a `DEFAULT_ADMIN_ROLE`… |
| **Upgrades** | 3/10 | High | Based on the provided information and code snippet, the contract is not designed as an upgradeable proxy (7.7 Upgrades). This means the contract's logic is immutable once deployed, eliminating… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 23.3% |
| **Top-3 Unlocked** | 51.8% |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Centralized Control via AccessControl Roles  *(Severity: Low · Status: Unresolved)*

The `AccessControl` contract centralizes significant power in the hands of accounts holding administrative roles, particularly the `DEFAULT_ADMIN_ROLE`. Members of this role can grant and revoke other roles, effectively controlling who can perform privileged operations within the system. While this is the intended design of role-based access control, it introduces a single point of failure if the administrative keys are compromised or misused (7.3 Access Control).

**Recommendation:** Implement robust security measures for accounts holding administrative roles. This typically includes using multi-signature wallets (e.g., Gnosis Safe) for all administrative roles, strong key management practices, and clear operational procedures for role management. Regularly review and audit role assignments.


### `I-01` — Incomplete Code Snippet Provided  *(Severity: Informational · Status: Unresolved)*

The provided Solidity code is a partial snippet, primarily consisting of OpenZeppelin libraries (EnumerableSet, Address, SafeMath, Context, AccessControl) and the beginning of an ERC20 token contract. Critical functions of the ERC20 standard (e.g., `_transfer`, `_mint`, `_burn`, `approve` logic) are truncated or missing. This prevents a comprehensive security analysis of the full contract's functionality and potential interactions.

**Recommendation:** Provide the complete and final source code for all contracts intended for deployment to enable a thorough and accurate security audit. A full audit would cover all functions, state transitions, and external interactions.


### `I-02` — Older Solidity Compiler Version Used  *(Severity: Informational · Status: Unresolved)*

The contract uses Solidity compiler version 0.6.2. While this version is functional, newer versions (e.g., 0.8.x) offer significant improvements in terms of security features, gas optimizations, and developer experience, such as default overflow/underflow checks, custom errors, and more efficient Yul optimizations. Using an older compiler might miss out on these benefits.

**Recommendation:** Consider upgrading the Solidity compiler to a more recent stable version (e.g., 0.8.x). This would allow the contract to benefit from the latest security features, bug fixes, and optimizations. Thorough testing should be performed after any compiler upgrade.


### `I-03` — Limitations of `Address.isContract`  *(Severity: Informational · Status: Unresolved)*

The `Address.isContract` function relies on `extcodehash` to determine if an address is a contract. While standard, `extcodehash` has known limitations: it returns 0 for contracts during their constructor execution, and it can be 0 for addresses that have self-destructed. This means it might not always accurately reflect the contract status in all edge cases, potentially leading to unexpected behavior if critical logic depends on it (7.2 Code Security).

**Recommendation:** Be aware of the limitations of `Address.isContract`. If the contract logic requires absolute certainty about an address being a contract, especially during deployment or after potential self-destruction, consider alternative or supplementary checks, or ensure that the context of its usage does not expose the system to these edge cases. For most standard uses, the current implementation is acceptable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x031b...fa7f`](https://bscscan.com/address/0x031b41e504677879370e9dbcf937283a8691fa7f) |
| **Network** | BNB Chain |
| **Price** | $0.2082 |
| **24h Volume** | $217.1K |
| **Liquidity** | $95.2K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 3y |
| **Top-10 Holders** | 94.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1095 buys / 1064 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x8149b92ea743cc382aada523b68b8834733b9015)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fetch-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
