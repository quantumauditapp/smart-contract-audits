---
token: Sandisk Corporation
ticker: SNDKB
network: bsc
risk_score: 100
status: critical
date: 2026-09-02
---

# Sandisk Corporation (SNDKB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sandisk-corporation-bsc)

---

## Audit Summary

The SecuritiesToken contract, an upgradeable ERC-20 token, implements a scaled UI amount standard (ERC8056) and integrates with compliance and pause management systems. The contract exhibits good adherence to upgradeability patterns and OpenZeppelin best practices. However, the audit identified a high degree of centralization in administrative control, critical dependencies on external contracts, and a wide range for economic parameters, which collectively contribute to a High overall risk level. Careful attention to governance, deployment procedures, and external contract security is crucial.

> **Final Recommendation:** Prioritize strengthening the administrative control mechanisms. Implement a multi-signature wallet or a time-locked governance system for the `DEFAULT_ADMIN_ROLE` to mitigate the single point of failure risk. Conduct thorough pre-deployment checks for all initialization parameters, especially the `admin_` and `issuers_` addresses, to prevent critical misconfigurations. Ensure that all external dependencies, particularly the `ComplianceClient` and `PauseManagerClient`, are rigorously audited and securely managed, as their integrity directly impacts the token's functionality. Review the acceptable range for the UI multiplier and consider narrowing it if the current wide range is not strictly necessary for the protocol's intended operation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates good technical practices, utilizing OpenZeppelin's upgradeable patterns and implementing robust checks for compliance and pausing within the `_update` function (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The contract design features a highly centralized access control model, with the `DEFAULT_ADMIN_ROLE` possessing extensive power over critical functions such as minting, burning, and setting external… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern and OpenZeppelin's upgradeable contracts, including proper `initializer` functions and a `__gap` storage variable (7.1… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.9% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 1 Low_

### `H-01` — High Centralization of Administrative Control  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` holds extensive power, including managing `ISSUER_ROLE`, enabling/disabling mint/burn, and setting critical external contracts like `ComplianceClient` and `PauseManagerClient`. This creates a single point of failure where a compromised or malicious admin key could lead to severe consequences, such as freezing transfers, arbitrary token issuance/destruction, or manipulating the token's economic parameters via the multiplier. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for the `DEFAULT_ADMIN_ROLE` to mitigate the risk of a single point of failure and enhance security.


### `M-01` — Critical Initialization Parameter Dependency  *(Severity: Medium · Status: Unresolved)*

The `initialize` function, specifically the `__securitiesToken_init` internal function, takes crucial parameters such as `admin_` and `issuers_`. If `admin_` is set to `address(0)` or an incorrect address during deployment, the contract could become unmanageable or controlled by an unintended entity. Similarly, if `issuers_` contains `address(0)` or incorrect addresses, it could lead to operational issues. (7.7 Upgrades, 7.8 Operations)

**Recommendation:** Implement robust pre-deployment checks and a secure deployment process to ensure all initialization parameters, especially `admin_`, are correct and valid. Consider adding a mechanism to recover admin control if `admin_` is accidentally set to `address(0)` (e.g., a time-locked recovery function, though this adds complexity).


### `M-02` — Reliance on External Compliance and Pause Managers  *(Severity: Medium · Status: Unresolved)*

The `SecuritiesToken` contract relies on external `ComplianceClient` and `PauseManagerClient` contracts to enforce transfer restrictions and pausing functionality. The security and integrity of the token's core transfer mechanism (`_update`) are directly dependent on these external contracts. A compromise or misconfiguration of these external contracts could lead to the token being frozen, transfers being arbitrarily restricted, or other unintended behaviors. (7.6 External)

**Recommendation:** Ensure that the `ComplianceClient` and `PauseManagerClient` contracts are thoroughly audited, securely managed, and follow best practices. Consider implementing circuit breakers or emergency mechanisms within the `SecuritiesToken` to temporarily bypass or disable these external dependencies in case of a critical issue, if feasible and aligned with the project's risk model.


### `M-03` — Wide Range for UI Multiplier Manipulation  *(Severity: Medium · Status: Unresolved)*

The `_validateMultiplier` function allows the `_uiMultiplier` to be set within a very broad range (from `1e9` to `1e27`, representing `1e-9x` to `1e9x` relative to the base `1e18`). While `_authorizeMultiplierUpdate` is restricted to `onlyAdminOrIssuer`, such a wide range provides significant power to these roles to drastically alter the perceived value or display of the token. Misuse or malicious manipulation of this multiplier could lead to economic instability or user confusion. (7.4 Economic, 7.5 Governance)

**Recommendation:** Review the intended use case and acceptable bounds for the UI multiplier. If the current range is wider than necessary, consider narrowing it to reduce the potential impact of malicious or erroneous settings. Ensure strong governance and operational controls are in place for the `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE` that can modify this parameter.


### `L-01` — Redundant Return Value for Mint/Burn Functions  *(Severity: Low · Status: Unresolved)*

The `mint` and `burn` functions return a boolean `true` after calling `_mint` and `_burn` respectively. However, the `_mint` and `_burn` functions from `ERC20Upgradeable` do not return a boolean. This means the `return true;` statement is redundant and could be misleading if a future change to `_mint` or `_burn` were to return a boolean indicating success/failure. While not a direct vulnerability, it's a minor inconsistency. (7.2 Code Security)

**Recommendation:** Remove the `returns (bool)` and `return true;` statements from the `mint` and `burn` functions, as the underlying `_mint` and `_burn` functions do not return a boolean. This aligns the function signature with the inherited behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3ee4...50fb`](https://bscscan.com/address/0x3ee4df61bd4f867e349beae8bfe07bc31b4850fb) |
| **Network** | BNB Chain |
| **Price** | $1,565.0580 |
| **24h Volume** | $227.8K |
| **Liquidity** | $335.0K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 98.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 434 buys / 456 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe4b5403f5103b02d1e8193b0d7d76d49f3f8ad77)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sandisk-corporation-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
