---
token: Tesla, Inc. 
ticker: TSLAB
network: bsc
risk_score: 96
status: critical
date: 2026-08-14
---

# Tesla, Inc.  (TSLAB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 96/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tesla-inc-bsc)

---

## Audit Summary

The SecuritiesToken contract, an upgradeable ERC-20 token, implements robust access control, compliance, and pause functionalities, leveraging OpenZeppelin standards. It features a scalable UI multiplier and controlled mint/burn mechanisms suitable for a securities token. Key strengths include secure upgradeability patterns and input validation. However, the contract exhibits a high degree of centralization, particularly with the DEFAULT_ADMIN_ROLE possessing extensive immediate control over critical token parameters, supply, and external dependencies. The Beacon Proxy pattern also centralizes upgrade authority. Several medium-severity findings highlight these centralization and dependency risks.

> **Final Recommendation:** To enhance the security and decentralization posture of the SecuritiesToken, consider implementing a timelock mechanism for all critical administrative functions currently controlled by the `DEFAULT_ADMIN_ROLE`. This would introduce a delay for sensitive operations, allowing for community oversight and mitigating the impact of a compromised administrative key. Additionally, thoroughly audit the external `ComplianceClient` and `PauseManagerClient` contracts to ensure their security and prevent potential cascading vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates good adherence to secure coding practices, utilizing OpenZeppelin's upgradeable standards and Solidity 0.8+ for overflow protection. It includes robust input validation for… |
| **Governance / Economics** | 1/10 | High | The `SecuritiesToken` contract features a strong access control model with `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE` for managing token operations (7.3 Access Control). Minting and burning are… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the Beacon Proxy pattern, correctly implementing OpenZeppelin's `initializer` pattern and a `__gap` storage variable to ensure future compatibility… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 22.9% |
| **Top-3 Unlocked** | 51.1% |

## Security Findings

_🟠 1 High · 🟡 4 Medium · ⚪ 1 Informational_

### `H-01` — Centralized Control over Token Supply and Critical Parameters  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` possesses extensive and immediate control over critical token functionalities. This includes the ability to enable/disable minting and burning, set compliance and pause managers, change the token's name, symbol, and identifier, and manage all roles. The `ISSUER_ROLE` can also mint and burn tokens. This high degree of centralization (7.3 Access Control, 7.4 Economic, 7.5 Governance) means that a single compromised administrative key or malicious administrator could significantly impact the token's supply, functionality, and perceived value without any delay or external oversight.

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control among multiple trusted parties. For highly sensitive operations, consider integrating a timelock mechanism to introduce a delay before changes take effect, allowing for community review or emergency intervention. Explore options for progressive decentralization of certain administrative powers if feasible for the project's long-term vision.


### `M-01` — Issuers Can Update UI Multiplier  *(Severity: Medium · Status: Unresolved)*

The `_authorizeMultiplierUpdate()` function, which gates the ability to change the `_uiMultiplier`, allows both the `DEFAULT_ADMIN_ROLE` and the `ISSUER_ROLE` to perform this action. While the `_validateMultiplier` function enforces bounds (1e9 to 1e27) and `_setUIMultiplier` limits the effective timestamp to 365 days in the future, granting issuers the power to change this critical parameter (7.3 Access Control, 7.4 Economic) could lead to confusion, misrepresentation of token value, or potential market manipulation if not properly governed or if issuers act maliciously.

**Recommendation:** Re-evaluate whether the `ISSUER_ROLE` should have the authority to update the UI multiplier. If this is an intended feature, ensure that the implications are clearly communicated to token holders and that robust governance procedures are in place for issuers. Consider restricting this power solely to the `DEFAULT_ADMIN_ROLE` or requiring a multi-signature approval for such changes.


### `M-02` — Reliance on External Client Contracts for Core Logic  *(Severity: Medium · Status: Unresolved)*

The `_update` function, which is central to all token transfers, calls `_checkTokenIsPaused()` and `_checkIsCompliant()`. These functions interact with external `PauseManagerClient` and `ComplianceClient` contracts (7.6 External, 7.2 Code Security). The security and integrity of these external contracts are paramount. A vulnerability, compromise, or malicious implementation within these client contracts could directly impact the token's transfer functionality, potentially leading to freezing of funds, unauthorized transfers, or reentrancy issues if the external contracts are not carefully designed and audited.

**Recommendation:** Conduct thorough security audits of the `PauseManagerClient` and `ComplianceClient` contracts. Ensure that these external contracts are immutable or have robust, timelocked upgrade mechanisms. Implement strict access controls on who can set these client contract addresses. Consider adding circuit breakers or emergency pause mechanisms within the `SecuritiesToken` itself that can override or disable interactions with potentially compromised external clients.


### `M-03` — Beacon Proxy Centralization Risk  *(Severity: Medium · Status: Unresolved)*

The contract is deployed behind a Beacon Proxy (7.7 Upgrades). While this pattern offers flexible upgradeability and efficient management of multiple proxies, it centralizes control over the contract's logic. The owner of the Beacon contract has the unilateral power to upgrade the implementation for all associated proxies. A compromise of the Beacon owner's key or a malicious action by the owner could lead to a complete and immediate change of the token's functionality, potentially resulting in loss of funds or unauthorized operations (7.5 Governance, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet for the Beacon owner address to distribute control. Integrate a timelock mechanism for all Beacon upgrade operations to introduce a delay, allowing for community review and mitigating the impact of a compromised key. Clearly document the upgrade process and the role of the Beacon owner.


### `M-04` — Lack of Timelock for Critical Administrative Operations  *(Severity: Medium · Status: Unresolved)*

Several critical administrative functions, such as `setMintEnabled`, `setBurnEnabled`, `setCompliance`, `setPauseManager`, `setName`, `setSymbol`, `setIdentifier`, and role management functions, can be executed immediately by the `DEFAULT_ADMIN_ROLE` (7.3 Access Control, 7.8 Operations). The absence of a timelock for these operations means that a single compromised administrative key could instantly make significant, irreversible changes to the token's behavior, parameters, or external dependencies without any warning or opportunity for intervention.

**Recommendation:** Integrate a timelock mechanism for all critical administrative functions. This would introduce a mandatory delay between the initiation and execution of sensitive changes, providing a window for detection of malicious activity, community oversight, or emergency response. This significantly reduces the risk associated with a single point of failure.


### `I-01` — `_checkAdminOrIssuer` is Private  *(Severity: Informational · Status: Unresolved)*

The `_checkAdminOrIssuer` function is declared as `private`. While it is correctly used by the `onlyAdminOrIssuer` modifier, making it `internal view` instead of `private view` would offer more flexibility (7.1 Architecture, 7.2 Code Security). This would allow inheriting contracts to directly call this function for internal checks without needing to duplicate the logic or rely solely on the modifier, potentially improving code reusability and extensibility for future upgrades or derived contracts.

**Recommendation:** Consider changing the visibility of `_checkAdminOrIssuer` from `private` to `internal view` to allow for greater flexibility and reusability by inheriting contracts, if such extensibility is a design goal.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5b19...292f`](https://bscscan.com/address/0x5b1910eaad6450e50f816082aa078c41f10c292f) |
| **Network** | BNB Chain |
| **Price** | $341.6700 |
| **24h Volume** | $427.6K |
| **Liquidity** | $253.0K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 14d |
| **Top-10 Holders** | 94.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1944 buys / 1903 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb0f5e5400e8f0f7c242f2b7740c004f020579c41)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tesla-inc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
