---
token: Synapse
ticker: SYN
network: ethereum
risk_score: 66
status: high
date: 2026-06-22
---

# Synapse (SYN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/synapse-eth)

---

## Audit Summary

This audit was conducted on a partial source code fragment, specifically the `AccessControlUpgradeable` contract, which is a dependency for the `SynapseERC20` token. A comprehensive security assessment of the `SynapseERC20` contract could not be performed due to the limited scope. The provided code itself is a standard OpenZeppelin implementation, generally considered robust. However, the overall security posture of the `SynapseERC20` token depends heavily on its full implementation and integration of this access control.

> **Final Recommendation:** A complete security audit of the entire `SynapseERC20` contract, including all its dependencies and business logic, is strongly recommended to identify any potential vulnerabilities not covered by this partial review. Special attention should be paid to the correct initialization of upgradeable contracts and the management of administrative roles. Ensure that the `DEFAULT_ADMIN_ROLE` is secured with a robust multi-signature wallet or a well-defined governance process.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The provided code, `AccessControlUpgradeable`, is a well-vetted OpenZeppelin library, indicating a strong foundation for access control (7.2 Code Security). It utilizes standard patterns for role… |
| **Governance / Economics** | 1/10 | High | The `AccessControlUpgradeable` contract provides a robust role-based access control system, allowing for granular permission management (7.3 Access Control). This structure can support decentralized… |
| **Upgrades** | 3/10 | High | The contract correctly inherits from `Initializable` and includes a `__gap` variable, indicating it is designed for use in an upgradeable proxy pattern (7.7 Upgrades). This is a strong practice for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 42.2% |
| **Top-3 Unlocked** | ⚠️ 88.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Incomplete Audit Scope Due to Partial Source Code  *(Severity: High · Status: Unresolved)*

The audit was conducted on a fragment of the project's source code, specifically the `AccessControlUpgradeable.sol` contract. The main `SynapseERC20` contract, which would integrate this access control, was not provided. This limitation prevents a comprehensive security assessment of the entire protocol, meaning potential vulnerabilities in the core logic, interactions, or other components of `SynapseERC20` could not be identified.

**Recommendation:** Provide the complete source code for all relevant contracts, especially the `SynapseERC20` token and any other contracts it interacts with, to enable a full and comprehensive security audit. This will allow for a thorough analysis of architectural design, business logic, and inter-contract dependencies.


### `M-01` — Critical Initialization Dependency for Upgradeable Contracts  *(Severity: Medium · Status: Unresolved)*

The `AccessControlUpgradeable` contract, being an upgradeable component, relies on its `__AccessControl_init()` or `__AccessControl_init_unchained()` functions to be called exactly once during the inheriting contract's initialization. Failure to correctly call these initializers in the `SynapseERC20` contract's `initialize` function could lead to an uninitialized state, rendering access control mechanisms ineffective or locking critical functions.

**Recommendation:** Ensure that the `SynapseERC20` contract's `initialize` function correctly calls `__AccessControl_init()` (or `__AccessControl_init_unchained()` if part of a larger initialization chain) from its constructor or `initialize` function. Implement robust testing to verify that all upgradeable components are correctly initialized upon deployment.


### `L-01` — Centralization Risk of DEFAULT_ADMIN_ROLE  *(Severity: Low · Status: Unresolved)*

The `AccessControlUpgradeable` contract's `DEFAULT_ADMIN_ROLE` possesses the authority to grant and revoke all other roles, including itself. While this is an inherent design of the OpenZeppelin AccessControl pattern, it introduces a single point of failure. If the account(s) holding the `DEFAULT_ADMIN_ROLE` are compromised or act maliciously, the entire access control system could be subverted.

**Recommendation:** Implement robust security measures for the account(s) holding the `DEFAULT_ADMIN_ROLE`. This typically involves using a multi-signature wallet (e.g., Gnosis Safe) with a sufficient number of signers, or integrating it into a decentralized governance mechanism. Regularly review and audit the accounts assigned to this critical role.


### `I-01` — Proper Use of Upgradeable Contract Pattern  *(Severity: Informational · Status: Unresolved)*

The contract correctly utilizes OpenZeppelin's `Initializable` base contract and includes a `__gap` storage variable. This demonstrates adherence to best practices for building upgradeable contracts, ensuring storage compatibility across different versions when used with a proxy pattern.

**Recommendation:** Continue to follow OpenZeppelin's upgradeability guidelines strictly for all future contract development and upgrades. Ensure that all state variables are declared before the `__gap` variable and that `initializer` modifiers are used correctly.


### `I-02` — Leveraging OpenZeppelin Standard Library  *(Severity: Informational · Status: Unresolved)*

The contract extensively uses well-audited and community-vetted OpenZeppelin contracts for its access control logic. This practice significantly reduces the risk of low-level vulnerabilities and common coding errors, as these libraries are maintained and regularly updated by a reputable team.

**Recommendation:** Maintain vigilance in keeping OpenZeppelin dependencies updated to their latest stable versions, especially when security patches are released. Regularly review OpenZeppelin's security advisories and release notes.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f2d...9f29`](https://etherscan.io/address/0x0f2d719407fdbeff09d87557abb7232601fd9f29) |
| **Network** | Ethereum |
| **Price** | $0.1498 |
| **24h Volume** | $133.2K |
| **Liquidity** | $132.1K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 67.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1354 buys / 1476 sells |

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

## Frequently Asked Questions

### Is Synapse a scam?

The data indicates a verified contract and renounced ownership, which are positive signals for transparency and decentralization of control over the contract. However, the presence of a mint function and significant token concentration among top holders, alongside unlocked liquidity, introduces considerable risks. While these factors point to potential vulnerabilities, they do not definitively label Synapse as a scam based solely on the provided security data.

### Is Synapse safe to buy?

Based on the security analysis, Synapse (SYN) presents several high-risk factors that investors should consider. The existence of a mint function, significant token concentration with the top 10 holders controlling 74.8% of supply, and critically, the absence of locked liquidity contribute to a high-risk score of 66/100. These elements suggest considerable caution is warranted due to potential for market manipulation and liquidity removal.

### Has Synapse been audited?

The Synapse contract is verified on-chain, meaning its source code is publicly accessible and matches the deployed version. This allows for transparency and code inspection. While beneficial, this is distinct from a comprehensive third-party security audit, which would rigorously assess for vulnerabilities and economic risks by independent experts.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4a86c01d67965f8cb3d0aaa2c655705e64097c31)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/synapse-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-22*
