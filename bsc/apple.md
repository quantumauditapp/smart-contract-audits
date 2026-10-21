---
token: Apple
ticker: AAPLB
network: bsc
risk_score: 100
status: critical
date: 2026-08-30
---

# Apple (AAPLB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apple-bsc)

---

## Audit Summary

The audit focused on the `SecuritiesToken` contract, which serves as the implementation for a BeaconProxy. The contract implements an upgradeable ERC-20 token with custom scaling (`ERC8056BaseUpgradeable`), access control, compliance, and pause functionalities. While the contract leverages well-audited OpenZeppelin libraries for upgradeability and access control, several areas of concern were identified, primarily related to centralized administrative power, the broad authority granted to the 'Issuer' role, and dependencies on external contracts. A critical missing zero-address check for the admin during initialization was also noted. The `ERC8056BaseUpgradeable` code was truncated, limiting a full review of its complex scaling logic.

> **Final Recommendation:** Strengthen access control by implementing a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control. Re-evaluate the scope of the `ISSUER_ROLE`'s permissions, specifically regarding the ability to authorize multiplier updates, and consider restricting this sensitive function to the `DEFAULT_ADMIN_ROLE` only. Implement a zero-address check for the `admin_` parameter in the `initialize` function to prevent accidental deployment into an unmanageable state. Ensure that all external dependencies, such as the `ComplianceClient` and `PauseManagerClient`, are thoroughly audited and managed by trusted entities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture is sound, utilizing OpenZeppelin's upgradeable contracts and access control patterns (7.1 Architecture, 7.2 Code Security). The contract correctly implements `__gap`… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the `DEFAULT_ADMIN_ROLE` possessing extensive control over critical parameters, role management, and external dependencies (7.3 Access… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a BeaconProxy, correctly utilizing OpenZeppelin's upgradeable patterns (7.7 Upgrades). The `__gap` storage variable is present, ensuring… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 53.5% |
| **Top-3 Unlocked** | ⚠️ 91.9% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by DEFAULT_ADMIN_ROLE  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` holds extensive power, including the ability to set token name/symbol/identifier, enable/disable minting/burning, manage all roles (including `ISSUER_ROLE`), and set the addresses for the `ComplianceClient` and `PauseManagerClient`. A compromise of this single role would grant an attacker full control over the token's functionality and potentially its economic parameters.

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control and require multiple approvals for critical operations. This significantly reduces the risk of a single point of failure.


### `H-02` — Issuer Role Can Authorize Multiplier Updates  *(Severity: High · Status: Unresolved)*

The `_authorizeMultiplierUpdate()` function, which is a prerequisite for changing the `_uiMultiplier`, is accessible to both `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE` via the `onlyAdminOrIssuer` modifier. Changes to the `_uiMultiplier` directly impact the token's value and user balances. Granting this powerful ability to potentially multiple `ISSUER_ROLE` holders increases the attack surface for economic manipulation or accidental misconfiguration, as the `ISSUER_ROLE`'s primary function is typically related to minting/burning, not economic parameter adjustments.

**Recommendation:** Restrict the `_authorizeMultiplierUpdate()` function to only the `DEFAULT_ADMIN_ROLE`. This ensures that only the most trusted and secure role can initiate changes to the token's core economic scaling factor.


### `M-01` — Missing Zero Address Check for Admin in Initializer  *(Severity: Medium · Status: Unresolved)*

The `initialize` function grants the `DEFAULT_ADMIN_ROLE` to the `admin_` address provided. However, there is no check to ensure that `admin_` is not `address(0)`. If the contract is initialized with `admin_` as `address(0)`, no entity would possess the `DEFAULT_ADMIN_ROLE`, rendering the contract unmanageable and unable to perform critical administrative functions (e.g., setting compliance, pause manager, or granting other roles).

**Recommendation:** Add a `require(admin_ != address(0), "ZeroAddress");` check at the beginning of the `__securitiesToken_init` function to prevent initialization with a zero address admin.


### `M-02` — Dependency on External Compliance and Pause Manager Contracts  *(Severity: Medium · Status: Unresolved)*

The `SecuritiesToken` contract relies heavily on external `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts, whose addresses are set by the `DEFAULT_ADMIN_ROLE`. The security and trustworthiness of these external contracts are paramount, as a malicious or compromised `ComplianceClient` could block legitimate transfers or allow non-compliant ones, and a malicious `PauseManagerClient` could permanently pause the token or pause it at will, effectively freezing all token operations.

**Recommendation:** Ensure that the `ComplianceClient` and `PauseManagerClient` contracts are thoroughly audited, well-secured, and controlled by trusted entities, ideally through a multi-signature setup. Implement robust monitoring for these external contracts. Consider adding a time-lock or governance mechanism for changing these critical external contract addresses.


### `L-01` — Inconsistent Pragma Version  *(Severity: Low · Status: Unresolved)*

The main `SecuritiesToken.sol` contract uses `pragma solidity ^0.8.20;` while the imported `ERC8056BaseUpgradeable.sol` uses `pragma solidity ^0.8.24;`. Although both versions are compatible with a compiler version of 0.8.24 (as indicated in the prefill), maintaining a consistent pragma across all contract files is a best practice for clarity and to avoid potential future compiler-related issues or warnings.

**Recommendation:** Standardize the pragma version across all contract files to `pragma solidity ^0.8.24;` or the specific version used for compilation.


### `I-01` — Truncated `ERC8056BaseUpgradeable` Code  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `ERC8056BaseUpgradeable` contract was truncated. This contract is fundamental to the `SecuritiesToken`'s core token mechanics, particularly its scaled amount (`_uiMultiplier`) logic. A complete security assessment of the `SecuritiesToken`'s economic model and potential for integer overflows/underflows or rounding errors within the scaling mechanism requires a full review of the `ERC8056BaseUpgradeable` implementation.

**Recommendation:** Provide the complete source code for all inherited and imported contracts to enable a comprehensive security audit of the entire system.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x431a...9b7a`](https://bscscan.com/address/0x431a3bee82e2ca41e49895cbece5bb0f76a89b7a) |
| **Network** | BNB Chain |
| **Price** | $320.6500 |
| **24h Volume** | $402.4K |
| **Liquidity** | $373.6K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 93.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3818 buys / 3335 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xe9b9998b2ec5430d2246c7f1f8d9f298c97d7365)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apple-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
