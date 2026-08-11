---
token: Olympus
ticker: OHM
network: ethereum
risk_score: 49
status: high
date: 2026-08-11
---

# Olympus (OHM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/olympus-eth)

---

## Audit Summary

This audit covers foundational components of the Olympus protocol, including an access control mechanism, ECDSA signature recovery, EIP-712 typed data hashing, and ERC-20 interfaces with mint/burn capabilities. The provided code snippets demonstrate robust security patterns and adherence to best practices for libraries and access control. However, the centralized nature of the `IOlympusAuthority` introduces significant governance and operational risks, which are further amplified by the powerful functions implied by the `IOHM` interface. A comprehensive security posture depends heavily on the full implementation of the `OlympusERC20Token` and the secure management of privileged roles.

> **Final Recommendation:** Prioritize the secure management of all privileged roles defined within the `IOlympusAuthority`, especially the `governor`. Implement multi-signature wallets (e.g., Gnosis Safe) for these addresses and establish clear operational procedures for key management and transaction execution. For critical administrative actions, consider implementing time-locks to provide a window for community review and emergency intervention. Additionally, ensure that the specific roles assigned to powerful functions like `mint` and `burn` in the `OlympusERC20Token` are strictly defined and adhere to the principle of least privilege.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation demonstrates strong security practices. The `OlympusAccessControlled` contract provides a clear role-based access control system (7.3 Access Control). Libraries like… |
| **Governance / Economics** | 2/10 | High | The protocol's governance and economic model, as implied by the `IOlympusAuthority` pattern, presents a high risk due to its centralized control (7.5 Governance). The `governor` role holds… |
| **Upgrades** | 3/10 | High | Based on the provided code snippets and prefilled information, the contracts are not designed as upgradeable proxies (`is_proxy: false`). Therefore, direct upgradeability is not a concern, and no… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control via OlympusAuthority  *(Severity: Medium · Status: Unresolved)*

The `OlympusAccessControlled` pattern relies on a single `IOlympusAuthority` contract to manage all critical roles (governor, guardian, policy, vault). The `governor` role has the power to change the `authority` contract itself via `setAuthority`. If the `governor` address is compromised, it could lead to a complete takeover of the protocol's access control, potentially enabling unauthorized minting, burning, or other critical operations if the `OlympusERC20Token` implements `IOHM` and uses these roles. This introduces significant governance and operational risk (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Implement robust multi-signature (e.g., Gnosis Safe) for the `governor` address and other critical roles. Ensure clear operational procedures and key management for these privileged accounts. Consider time-locks for critical administrative actions like `setAuthority` to allow for community review and emergency response.


### `L-01` — Use of Solidity 0.7.x  *(Severity: Low · Status: Unresolved)*

The contracts are compiled with Solidity `0.7.5` and `^0.7.5`. While `SafeMath` is used to prevent integer overflows/underflows, newer Solidity versions (e.g., `0.8.x`) include default checked arithmetic, which provides an additional layer of safety and reduces the reliance on external libraries for basic arithmetic. Migrating to a newer compiler version could simplify the code and leverage these built-in safety features (7.2 Code Security).

**Recommendation:** Consider upgrading to Solidity `0.8.x` to benefit from default checked arithmetic and other compiler improvements. Thoroughly test all contracts after any compiler upgrade to ensure compatibility and prevent unexpected behavior.


### `I-01` — Powerful `IOHM` Interface Functions  *(Severity: Informational · Status: Unresolved)*

The `IOHM` interface defines `mint`, `burn`, and `burnFrom` functions, which are highly privileged operations for an ERC-20 token. While the `OlympusAccessControlled` abstract contract provides modifiers (`onlyPolicy`, `onlyVault`, etc.) to restrict access, the specific roles assigned to these functions in the actual `OlympusERC20Token` implementation are not visible in the provided snippets. Misconfiguration or overly broad permissions for these functions could lead to uncontrolled supply manipulation, impacting the token's economic stability (7.1 Architecture, 7.3 Access Control, 7.4 Economic).

**Recommendation:** Ensure that `mint`, `burn`, and `burnFrom` functions in the `OlympusERC20Token` are strictly controlled by appropriate, multi-sig-protected roles (e.g., `onlyPolicy` or `onlyVault` with strong governance). Document the exact permissions and their implications clearly to maintain transparency and accountability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x64aa...f1d5`](https://etherscan.io/address/0x64aa3364f17a4d01c6f1751fd97c2bd3d7e7f1d5) |
| **Network** | Ethereum |
| **Price** | $18.6800 |
| **24h Volume** | $59.9K |
| **Liquidity** | $4.10M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 99.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 54 buys / 52 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x88051b0eea095007d3bef21ab287be961f3d8598)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/olympus-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
