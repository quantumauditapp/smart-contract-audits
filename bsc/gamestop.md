---
token: GameStop
ticker: GMEB
network: bsc
risk_score: 90
status: critical
date: 2026-08-14
---

# GameStop (GMEB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gamestop-bsc)

---

## Audit Summary

The audit of the SecuritiesToken contract, an upgradeable ERC-20 token, revealed a robust architecture leveraging OpenZeppelin standards for access control and upgradeability. Key strengths include comprehensive role-based access control for critical functions and integration with compliance and pause mechanisms. However, the contract exhibits a high degree of centralization in the DEFAULT_ADMIN_ROLE, critical dependencies on external contracts, and the economic implications of its UI multiplier mechanism. Upgradeability also introduces inherent risks.

> **Final Recommendation:** Implement multi-signature wallets or time-locked governance for the `DEFAULT_ADMIN_ROLE` and the BeaconProxy admin to decentralize control and enhance security. Thoroughly vet and monitor all external contract dependencies, especially `ComplianceClient` and `PauseManagerClient`. Establish clear policies and transparent communication for any changes to the UI multiplier to maintain user trust and economic stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates good technical practices, utilizing OpenZeppelin's upgradeable patterns and access control. The `_update` function correctly integrates compliance and pause checks (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The economic model includes a UI multiplier that can be adjusted by authorized roles, which could lead to user confusion or economic instability if not managed transparently (7.4 Economic). The… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern and OpenZeppelin's upgradeable contracts, including `__gap` storage for future compatibility (7.7 Upgrades). This allows for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 27.9% |
| **Top-3 Unlocked** | 49.9% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` holds extensive power, including setting token name/symbol/identifier, enabling/disabling mint/burn, and configuring critical external contracts (`ComplianceClient`, `PauseManagerClient`). This high degree of centralization means a compromise of the admin key could lead to full control over the token's functionality and potentially its economic parameters. While common for security tokens, this presents a significant operational risk (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for the `DEFAULT_ADMIN_ROLE` to mitigate the risk of a single point of failure.


### `H-02` — Critical External Dependencies  *(Severity: High · Status: Unresolved)*

The contract relies on external `ComplianceClient` and `PauseManagerClient` contracts, whose addresses can be set by the `DEFAULT_ADMIN_ROLE`. A malicious or compromised external contract, or an incorrectly set address, could lead to a complete halt of token operations (via `PauseManagerClient`) or arbitrary restrictions on transfers (via `ComplianceClient`). This introduces significant external dependency risks (7.6 External, 7.8 Operations).

**Recommendation:** Thoroughly vet and secure the external `ComplianceClient` and `PauseManagerClient` contracts. Implement robust monitoring for changes to these addresses and consider a timelock for `setCompliance` and `setPauseManager` functions.


### `M-01` — Economic Impact of UI Multiplier  *(Severity: Medium · Status: Unresolved)*

The `ERC8056BaseUpgradeable` introduces a UI multiplier that can significantly alter the perceived value of tokens. The `_setUIMultiplier` function, callable by `onlyAdminOrIssuer` (after `_authorizeMultiplierUpdate`), allows changing this multiplier within defined bounds. While bounds are present, an unexpected or frequent change in the multiplier could confuse users, impact integrations, or lead to economic instability if not communicated clearly and managed carefully (7.4 Economic).

**Recommendation:** Establish clear policies and procedures for managing the UI multiplier. Ensure transparent communication with users and integrated platforms regarding any planned multiplier changes. Consider adding a timelock for multiplier updates to allow users to react.


### `M-02` — Upgradeability Risks  *(Severity: Medium · Status: Unresolved)*

The contract is deployed as an implementation behind a BeaconProxy, allowing its logic to be upgraded by the BeaconProxy's admin. While OpenZeppelin's upgradeable patterns are used correctly (e.g., `__gap` storage, `initializer` functions), the ability to upgrade introduces a trust assumption. A malicious upgrade could introduce new vulnerabilities or change contract behavior unexpectedly (7.7 Upgrades).

**Recommendation:** Secure the admin key of the BeaconProxy with a multi-signature wallet or a robust governance mechanism. Implement a transparent upgrade process, including public announcements and audit reports for new implementations, to maintain user trust.


### `L-01` — Missing Zero Address Check for Admin in Initialization  *(Severity: Low · Status: Unresolved)*

In the `__securitiesToken_init` function, the `admin_` address passed to `_grantRole(DEFAULT_ADMIN_ROLE, admin_)` is not checked for being `address(0)`. While the `issuers_` array elements are checked, a `DEFAULT_ADMIN_ROLE` assigned to `address(0)` would effectively lock out administrative control, rendering the contract unmanageable (7.2 Code Security).

**Recommendation:** Add a check `if (admin_ == address(0)) revert ZeroAddress();` at the beginning of the `__securitiesToken_init` function to prevent accidental assignment of the admin role to the zero address.


### `I-01` — Role Definition via keccak256  *(Severity: Informational · Status: Unresolved)*

The `ISSUER_ROLE` is defined using `keccak256("ISSUER_ROLE")`. While this is a standard and secure practice for defining roles in OpenZeppelin's `AccessControl`, it's important to ensure that the string literal used is unique and consistent across all related contracts and off-chain systems to prevent role collision or misinterpretation (7.2 Code Security).

**Recommendation:** Document all role definitions and their corresponding string literals clearly. Ensure that any external systems interacting with these roles use the exact same string literals for `keccak256` hashing.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x46ce...b15c`](https://bscscan.com/address/0x46ceefda28dd7207059ed19b0acdc026955bb15c) |
| **Network** | BNB Chain |
| **Price** | $18.6600 |
| **24h Volume** | $9.13M |
| **Liquidity** | $1.14M |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 79.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 44328 buys / 40389 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x908d49048eb3a7bedfd238972403842805eaf2be)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gamestop-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
