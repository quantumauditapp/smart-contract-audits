---
token: Gains Network
ticker: GNS
network: arbitrum
risk_score: 43
status: medium
date: 2026-09-01
---

# Gains Network (GNS) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gains-network-arb)

---

## Audit Summary

The GainsNetworkToken contract is an ERC20Capped token utilizing OpenZeppelin's AccessControlEnumerable for role-based permissions. The contract implements minting and burning functionalities controlled by specific roles. The primary risks identified relate to the centralized control over token supply via the DEFAULT_ADMIN_ROLE and the multiple MINTER_ROLE addresses, which could lead to significant economic impact if compromised. The contract is not upgradeable, simplifying its security profile in that regard.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to secure the `DEFAULT_ADMIN_ROLE` with a robust multi-signature wallet or a decentralized autonomous organization (DAO) governance mechanism. Implement strict operational security procedures for all addresses holding `MINTER_ROLE` and `BURNER_ROLE`, ensuring they are not single points of failure. Regularly review and audit the security posture of all privileged addresses and associated infrastructure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits strong technical security (7.2 Code Security). It leverages well-audited OpenZeppelin libraries for ERC20Capped and AccessControlEnumerable, minimizing common vulnerabilities… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4 Economic) and governance structure (7.5 Governance) present the highest risks. The `DEFAULT_ADMIN_ROLE` holds significant power, able to grant and revoke all other roles… |
| **Upgrades** | 3/10 | High | The GainsNetworkToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract, meaning its logic cannot be changed post-deployment. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Single Point of Failure for Default Admin Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` is initially assigned to a single `admin` address in the constructor. This creates a single point of failure (7.8 Operations). If this `admin` address's private key is compromised, an attacker would gain full control over all roles within the contract, including the ability to assign themselves `MINTER_ROLE` or `BURNER_ROLE`, leading to potential token manipulation (7.3 Access Control).

**Recommendation:** Transition the `DEFAULT_ADMIN_ROLE` to a multi-signature wallet or a robust governance contract as soon as possible after deployment. This distributes control and significantly reduces the risk associated with a single compromised key.


### `M-02` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke `MINTER_ROLE` and `BURNER_ROLE`. Additionally, multiple external addresses are assigned `MINTER_ROLE` in the `setupRoles` function. A compromise of the `DEFAULT_ADMIN_ROLE` or any address holding `MINTER_ROLE` could lead to unauthorized token minting up to the cap (100,000,000 GNS), significantly devaluing existing tokens and impacting the protocol's economic stability. This represents a critical risk to the token's integrity and value (7.3 Access Control, 7.4 Economic).

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to require multiple approvals for critical actions like granting/revoking roles. Carefully evaluate the necessity of each address holding `MINTER_ROLE` and consider reducing the number of such privileged entities. Implement robust security measures for all addresses with minting or burning capabilities.


### `L-01` — Critical Initialization Function `setupRoles`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setupRoles` function is a critical, one-time initialization function that assigns `MINTER_ROLE` and `BURNER_ROLE` to several external addresses. While protected by an `initialized` flag and `onlyRole(DEFAULT_ADMIN_ROLE)`, any error in the initial setup (e.g., incorrect addresses) or a compromise of the `DEFAULT_ADMIN_ROLE` before this call could lead to incorrect or malicious role assignments that are difficult to rectify (7.3 Access Control, 7.8 Operations).

**Recommendation:** Ensure thorough testing and verification of all addresses passed to `setupRoles` before deployment. Consider a timelock for the `DEFAULT_ADMIN_ROLE` to introduce a delay for critical operations, allowing time to react to potential errors or malicious actions during initialization.


### `I-01` — Use of AccessControlEnumerable  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract inherits `AccessControlEnumerable`, which provides functionality to enumerate role members (e.g., `getRoleMember`, `getRoleMemberCount`). If the protocol does not actively utilize these enumeration features, inheriting directly from `AccessControl` would be sufficient. `AccessControlEnumerable` adds a slight increase in contract size and gas costs due to the additional storage and logic for `EnumerableSet` (7.2 Code Security).

**Recommendation:** Review if the enumeration features of `AccessControlEnumerable` are strictly necessary for the protocol's operations. If not, consider using `AccessControl` to slightly optimize contract size and gas usage. This is a minor optimization and does not pose a security risk.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x18c1...a122`](https://arbiscan.io/address/0x18c11fd286c5ec11c3b683caa813b77f5163a122) |
| **Network** | Arbitrum |
| **Price** | $0.5257 |
| **24h Volume** | $6.5K |
| **Liquidity** | $252.3K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 60.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 218 buys / 402 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x9b6ff025aee245d314c09f57b72f0de6e231c3a6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gains-network-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
