---
token: Aethir Token
ticker: ATH
network: arbitrum
risk_score: 69
status: high
date: 2026-09-03
---

# Aethir Token (ATH) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aethir-token-arb)

---

## Audit Summary

The InterchainToken contract, serving as an upgradeable ERC20 token implementation, demonstrates adherence to modern Solidity practices and includes custom access control via a `RolesBase` contract. Key strengths include a robust initialization mechanism for proxy safety and careful handling of token metadata. However, the audit identified significant centralization risks associated with the `MINTER` role and a critical gap due to the truncation of the `RolesBase` contract, preventing a full assessment of access control. A minor issue with redundant initialization in the constructor was also noted.

> **Final Recommendation:** Address the high-severity issues by providing the complete source code for the `RolesBase` contract to allow for a comprehensive audit of the access control system. Implement robust multi-signature or governance controls for the `MINTER` role to mitigate centralization risks and enhance the security of token supply management. Remove the redundant `_initialize()` call from the constructor of the implementation contract to improve clarity and adhere to best practices for upgradeable contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract demonstrates good adherence to ERC20 standards and utilizes modern Solidity features. Custom `_spendAllowance` logic, while deviating from standard libraries, appears safe due to… |
| **Governance / Economics** | 2/10 | High | The economic model relies heavily on the `MINTER` role, which has the power to arbitrarily mint and burn tokens (7.4 Economic). The `init` function assigns this role to the `interchainTokenService_`… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation, correctly using an `_isInitialized()` check within its `init` function to prevent re-initialization of the proxy's storage (7.7 Upgrades).… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 32.9% |
| **Top-3 Unlocked** | 78.7% |

## Security Findings

_🟠 2 High · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control via Minter Role  *(Severity: High · Status: Unresolved)*

The `mint` and `burn` functions are protected by the `onlyRole(uint8(Roles.MINTER))` modifier. The `init` function adds `interchainTokenService_` and a user-provided `minter` address to the `MINTER` role. This grants significant power to these addresses, allowing them to arbitrarily mint and burn tokens, directly impacting the token's supply and value. If the `minter` address is an EOA or a single-sig contract, it represents a single point of failure and a high centralization risk (7.3 Access Control, 7.4 Economic).

**Recommendation:** Implement robust governance or multi-signature control over the `MINTER` role. Consider time-locks or multi-stage processes for critical actions like adding/removing minters or large mint operations to distribute control and reduce single points of failure.


### `H-02` — Incomplete `RolesBase` Contract  *(Severity: High · Status: Unresolved)*

The provided `RolesBase` contract, which is fundamental to the access control system, is truncated. Specifically, the `_addAccountRoles` function is incomplete: `function _addAccountRoles(address account, uint256 accountRoles) i... (truncated)`. Without the full implementation of this core access control logic, a complete security assessment of the role management system (including how roles are added, removed, and proposed) is impossible. This leaves a significant blind spot in the audit (7.2 Code Security).

**Recommendation:** Provide the complete source code for all inherited and used contracts, especially critical security components like `RolesBase`, to enable a comprehensive security review and ensure the integrity of the access control mechanisms.


### `L-01` — Redundant `_initialize()` Call in Constructor  *(Severity: Low · Status: Unresolved)*

The `InterchainToken` contract, intended as a proxy implementation, calls `_initialize()` in its constructor. In a proxy pattern (like UUPS or Transparent), the constructor of the implementation contract is executed only once when the implementation itself is deployed, not when the proxy is initialized. The actual initialization for the proxy's storage occurs via an `init` function called on the proxy. While not a direct vulnerability (as `init` correctly uses `_isInitialized()` to prevent re-initialization on the proxy's storage), this constructor call is redundant and can be misleading (7.7 Upgrades).

**Recommendation:** Remove the `_initialize()` call from the constructor of proxy implementation contracts. Ensure all proxy-related initialization logic resides solely within the designated initializer function (e.g., `init`) to maintain clarity and best practices for upgradeable contracts.


### `I-01` — Custom `_spendAllowance` Override  *(Severity: Informational · Status: Unresolved)*

The contract overrides the `_spendAllowance` function with a custom implementation. It uses `_approve(sender, spender, _allowance - amount)` directly. In Solidity 0.8.0+, arithmetic operations automatically check for underflows and overflows, meaning `_allowance - amount` will revert if `amount` is greater than `_allowance`. The `UINT256_MAX` check correctly handles infinite approvals. This custom logic appears safe due to Solidity's built-in checks, but any deviation from standard library implementations warrants careful review (7.2 Code Security).

**Recommendation:** Document the rationale for custom overrides, especially for core ERC20 functionalities. Ensure thorough unit and integration testing covers all edge cases for allowance spending to confirm its robustness.


### `I-02` — Inline Assembly Usage  *(Severity: Informational · Status: Unresolved)*

The contract and its inherited `RolesBase` utilize inline assembly for direct storage manipulation (e.g., `sload`, `sstore`) for initialization flags and role management. This approach is used for gas optimization and specific storage patterns (like `keccak256` based mapping keys). While assembly can introduce subtle bugs if not handled correctly, the patterns observed (e.g., using a large constant for `INITIALIZED_SLOT`, `keccak256` for mapping keys) are standard and generally considered safe for preventing storage collisions (7.2 Code Security).

**Recommendation:** Ensure comprehensive unit and integration tests cover all code paths involving inline assembly. Maintain clear and up-to-date documentation for the storage layout and assembly logic to facilitate future audits and maintenance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc87b...056c`](https://arbiscan.io/address/0xc87b37a581ec3257b734886d9d3a581f5a9d056c) |
| **Network** | Arbitrum |
| **Price** | $0.004526 |
| **24h Volume** | $54.2K |
| **Liquidity** | $49.6K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 74.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 93 buys / 153 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x5cbddc44f31067df328aa7a8da03aca6f2edd2ad)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aethir-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
