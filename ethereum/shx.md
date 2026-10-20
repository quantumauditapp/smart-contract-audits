---
token: SHX
ticker: SHX
network: ethereum
risk_score: 75
status: high
date: 2026-09-28
---

# SHX (SHX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shx-eth)

---

## Audit Summary

The audit of the InterchainToken contract, serving as an implementation behind a proxy, identified a critical architectural flaw related to the use of an immutable variable for a key service address. This design choice fundamentally breaks the proxy pattern, preventing the proxy from correctly controlling or referencing its interchain token service. Additionally, a portion of the access control logic was truncated, limiting full verification. The contract otherwise demonstrates standard ERC-20 functionality and a role-based access control system.

> **Final Recommendation:** It is critical to address the use of the `immutable` keyword for `interchainTokenService_`. This variable must be refactored to be a regular storage variable, allowing it to be properly initialized and managed via the proxy's storage. Ensure the `init` function correctly sets this variable for the proxy. Additionally, provide the complete source code for all inherited and utilized libraries, especially the `RolesBase` contract, to enable a comprehensive security review of the access control mechanisms.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The InterchainToken contract implements ERC-20 functionality with minting and burning capabilities, secured by a role-based access control system (7.3). It utilizes Axelar GMP SDK components for… |
| **Governance / Economics** | 1/10 | High | The contract employs a role-based access control system (7.5) where 'MINTER' roles are assigned to the 'interchainTokenService_' and an initial minter during initialization. This allows controlled… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a proxy (7.7), utilizing a custom initialization slot (`INITIALIZED_SLOT`) to prevent re-initialization. However, the declaration of… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Immutable Variable in Proxy Implementation Breaks Functionality  *(Severity: Critical · Status: Unresolved)*

The `interchainTokenService_` variable is declared as `internal immutable` and initialized in the constructor. In a proxy pattern, `immutable` variables are embedded in the implementation contract's bytecode and cannot be modified or controlled by the proxy's storage. This means that any call to `interchainTokenService()` through the proxy will always return the address that was set when the *implementation contract itself* was deployed, not an address that can be initialized or changed by the proxy. This fundamentally breaks the proxy's ability to manage its associated interchain service, impacting core functionality and access control (e.g., `_addMinter(interchainTokenService_)` will add…

**Recommendation:** Refactor `interchainTokenService_` to be a regular `internal` (or `public`) storage variable instead of `immutable`. Initialize this variable within the `init` function, which is called through the proxy, ensuring it is stored in the proxy's storage and can be correctly managed by the proxy instance.


### `M-01` — Incomplete Code for Role Management  *(Severity: Medium · Status: Unresolved)*

The provided source code for the `RolesBase` contract truncates the `_addAccountRoles` function. This prevents a complete audit of the role management logic, which is critical for access control (7.3). Without the full implementation, it's impossible to verify the correctness and security of how roles are added and managed within the system.

**Recommendation:** Provide the complete and untruncated source code for all inherited contracts and libraries, especially `RolesBase`, to allow for a thorough security review of the access control mechanisms.


### `I-01` — Use of Assembly for Storage Operations  *(Severity: Informational · Status: Unresolved)*

The contract utilizes inline assembly (`sload`, `sstore`) for custom initialization (`_initialize`, `_isInitialized`) and role management (`_getRoles`, `_setRoles`). While assembly can be efficient, it increases code complexity and the potential for subtle errors compared to high-level Solidity storage access. It requires a higher degree of scrutiny during audits (7.2).

**Recommendation:** Ensure that all assembly blocks are thoroughly tested and formally verified if possible. Document the exact storage slots being accessed and their purpose to maintain clarity and reduce the risk of storage collisions or incorrect state manipulation, especially in upgradeable contracts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x516d...9787`](https://etherscan.io/address/0x516d31321928700c6b4fb0db0c8c6bc5d6799787) |
| **Network** | Ethereum |
| **Price** | $0.004737 |
| **24h Volume** | $265.1K |
| **Liquidity** | $1.31M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 72.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 266 buys / 190 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xfd7908646f132efe38734a0da4166b7f1c5ea98958644b67fdf8ad8db9242712)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shx-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
