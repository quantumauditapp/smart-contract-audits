---
token: Invesqo QQQ
ticker: QQQB
network: bsc
risk_score: 100
status: critical
date: 2026-07-26
---

# Invesqo QQQ (QQQB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/invesqo-qqq-bsc)

---

## Audit Summary

The audit of the SecuritiesToken contract, serving as the implementation for a Beacon Proxy, identified a critical vulnerability related to the initialization of the admin role, which could lead to permanent loss of administrative control. Additional medium and low-severity issues were found concerning zero-address checks for external dependencies and inherent centralization risks. The contract utilizes standard OpenZeppelin upgradeable patterns and role-based access control.

> **Final Recommendation:** Address the critical vulnerability by implementing a zero-address check for the `admin_` parameter in the `initialize` function to prevent irreversible loss of administrative control. Additionally, add zero-address checks for `compliance_` and `pauseManager_` to ensure robust system integrity. Consider implementing multi-signature control for the `DEFAULT_ADMIN_ROLE` to mitigate centralization risks and enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages OpenZeppelin's upgradeable patterns and AccessControlEnumerable for robust role management (7.1 Architecture, 7.3 Access Control). Custom error types enhance readability and… |
| **Governance / Economics** | 1/10 | High | The token's economic model relies on a centralized `DEFAULT_ADMIN_ROLE` for critical operations such as enabling/disabling minting/burning, and managing all other roles (7.4 Economic, 7.5… |
| **Upgrades** | 1/10 | High | The contract correctly implements OpenZeppelin's upgradeable proxy pattern, utilizing `_disableInitializers()` in the constructor and the `initializer` modifier for the `initialize` function (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing Zero Address Check for Admin Role in `initialize`  *(Severity: Critical · Status: Unresolved)*

The `initialize` function, which sets up the initial `DEFAULT_ADMIN_ROLE`, does not validate that the `admin_` parameter is not the zero address (`address(0)`). If `address(0)` is provided during initialization, the `DEFAULT_ADMIN_ROLE` will be granted to the zero address, making it impossible to manage roles, enable/disable minting/burning, or perform any other administrative functions. This would lead to a permanent lockout of administrative control over the contract.

**Recommendation:** Add a check in the `initialize` function to ensure `admin_` is not `address(0)` before granting the `DEFAULT_ADMIN_ROLE`. For example: `if (admin_ == address(0)) revert ZeroAddress();`


### `M-01` — Missing Zero Address Checks for External Client Contracts  *(Severity: Medium · Status: Unresolved)*

The `initialize` function accepts `compliance_` and `pauseManager_` addresses for external client contracts without validating that these addresses are not the zero address (`address(0)`). While not directly leading to a loss of funds, setting these critical external dependencies to `address(0)` could result in unexpected runtime errors, non-functional compliance checks, or an inability to pause the token, severely impacting the contract's intended behavior and operational stability.

**Recommendation:** Implement zero-address checks for `compliance_` and `pauseManager_` parameters in the `initialize` function. For example: `if (compliance_ == address(0)) revert ZeroAddress();` and `if (pauseManager_ == address(0)) revert ZeroAddress();`


### `L-01` — High Centralization Risk with DEFAULT_ADMIN_ROLE  *(Severity: Low · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` holds extensive power over the `SecuritiesToken` contract. This role can set the token's name, symbol, and identifier, enable/disable minting and burning, and grant/revoke any other role, including the `ISSUER_ROLE`. While common for security tokens requiring centralized control, this concentration of power means that a compromise of the single entity holding the `DEFAULT_ADMIN_ROLE` could lead to significant operational and economic risks, including unauthorized token issuance or manipulation of token metadata.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for the `DEFAULT_ADMIN_ROLE` to distribute control and introduce a delay for critical operations. This would enhance security by requiring multiple approvals for sensitive actions and providing a window for intervention.


### `I-01` — Reliance on External Compliance and Pause Managers  *(Severity: Informational · Status: Unresolved)*

The `SecuritiesToken` contract integrates `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable`, making its core functionalities (transfers, minting, burning) dependent on the logic and availability of these external contracts. The security, reliability, and upgradeability of these external dependencies are paramount, as any vulnerability or malfunction in them could directly impact the `SecuritiesToken`'s operations and user experience.

**Recommendation:** Ensure that the external `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts are thoroughly audited, well-maintained, and controlled by robust governance mechanisms. Implement monitoring for these external contracts to detect any unusual behavior or potential compromises promptly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2058...efc7`](https://bscscan.com/address/0x205812cdbed920aff76c6580abd681a46d11efc7) |
| **Network** | BNB Chain |
| **Price** | $679.2300 |
| **24h Volume** | $45.04M |
| **Liquidity** | $1.74M |
| **Volume / Liquidity** | 25.8× |
| **Token Age** | 16d |
| **Top-10 Holders** | 94.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7406 buys / 6727 sells |

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

## Frequently Asked Questions

### Is Invesqo QQQ a scam?

Based on automated analysis, Invesqo QQQ scores 63/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Invesqo QQQ safe to buy?

Our scanner flagged a risk score of 63/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Invesqo QQQ been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xe531fcb1f5a195de7608b9f4f9518544c2cdb693)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/invesqo-qqq-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
