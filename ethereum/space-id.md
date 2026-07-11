---
token: SPACE ID
ticker: ID
network: ethereum
risk_score: 78
status: critical
date: 2026-06-11
---

# SPACE ID (ID) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 78/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/space-id-eth)

---

## Audit Summary

This audit focused solely on the OpenZeppelin `AccessControl.sol` library contract, which is a dependency for the `SpaceIDToken` contract. No custom logic for `SpaceIDToken` was provided for review, thus a comprehensive security assessment of the entire protocol cannot be performed. The `AccessControl` library itself is well-tested and widely used.

> **Final Recommendation:** Ensure that the `DEFAULT_ADMIN_ROLE` and other critical roles in the `SpaceIDToken` contract are secured with multi-signature wallets and, ideally, time-locks for sensitive operations. Implement the principle of least privilege when assigning roles to prevent over-permissioning. Conduct a full security audit of the `SpaceIDToken` contract's custom logic to identify specific vulnerabilities related to its business logic, tokenomics, and interactions with other protocols.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The provided code is the OpenZeppelin `AccessControl` library, which implements a robust role-based access control system (7.3 Access Control). It is a well-audited and widely adopted standard… |
| **Governance / Economics** | 1/10 | High | A comprehensive assessment of economic (7.4 Economic) and governance (7.5 Governance) risks is not possible as the core `SpaceIDToken` contract logic was not provided. The `AccessControl` contract… |
| **Upgrades** | 5/10 | Medium | The provided `AccessControl` contract is not designed as an upgradeable proxy (7.7 Upgrades). The prefill indicates `is_proxy: false` for the main contract. If the `SpaceIDToken` were to be… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 3 Informational_

### `L-01` — Lack of Time-Lock for Critical Operations  *(Severity: Low · Status: Unresolved)*

The `AccessControl` contract itself does not inherently include time-lock mechanisms for sensitive operations like `grantRole` or `revokeRole`. Without a time-lock, critical changes can be executed immediately, leaving no window for community or governance intervention in case of a compromised key or malicious action (7.5 Governance, 7.8 Operations).

**Recommendation:** For critical roles, especially the `DEFAULT_ADMIN_ROLE`, consider implementing a separate time-lock contract that acts as an intermediary for executing sensitive `AccessControl` functions. This introduces a delay, allowing for review and potential cancellation of malicious or erroneous operations.


### `I-01` — Default Admin Role Security  *(Severity: Informational · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` in `AccessControl` has the power to grant and revoke any other role, including itself. Compromise of an account holding this role would grant an attacker full control over the contract's access control mechanisms, potentially leading to critical system compromise (7.3 Access Control, 7.8 Operations).

**Recommendation:** The address assigned to `DEFAULT_ADMIN_ROLE` should be a highly secured multi-signature wallet. Consider implementing a time-lock for critical operations performed by this role to provide a window for intervention.


### `I-02` — Role Granularity and Least Privilege  *(Severity: Informational · Status: Unresolved)*

While `AccessControl` provides a robust framework, the security of the system heavily depends on how roles are defined and assigned in the inheriting `SpaceIDToken` contract. Over-permissioning accounts can lead to unintended access to sensitive functions (7.3 Access Control).

**Recommendation:** Adhere strictly to the principle of least privilege. Each role should have only the minimum permissions necessary to perform its designated tasks. Regularly review role assignments and revoke unnecessary permissions.


### `I-03` — Event Monitoring for Role Changes  *(Severity: Informational · Status: Unresolved)*

The `AccessControl` contract explicitly states that it does not allow enumerating role members except through off-chain means by accessing contract event logs. This means that active monitoring of `RoleGranted`, `RoleRevoked`, and `RoleAdminChanged` events is crucial for maintaining an accurate understanding of current permissions (7.8 Operations).

**Recommendation:** Implement robust off-chain monitoring systems to track all role-related events. This allows for timely detection of unauthorized role changes or misconfigurations, enhancing operational security.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2dff...6406`](https://etherscan.io/address/0x2dff88a56767223a5529ea5960da7a3f5f766406) |
| **Network** | Ethereum |
| **Price** | $0.03276 |
| **24h Volume** | $300.9K |
| **Liquidity** | $584.1K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 91.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 226 buys / 282 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x0143b80d682d2b6fb8945f47b7d199841ab8184c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/space-id-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-11*
