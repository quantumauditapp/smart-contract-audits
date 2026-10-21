---
token: Origin Ether
ticker: OETH
network: ethereum
risk_score: 70
status: high
date: 2026-09-03
---

# Origin Ether (OETH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/origin-ether-eth)

---

## Audit Summary

This audit covers the `OETH` token contract, which inherits from `OUSD`, and the `Governable` contract, which provides access control and reentrancy protection. The system operates behind an EIP-1967 UUPS proxy. A critical limitation of this audit is the absence of the `OUSD` contract's source code, which is expected to contain the core token logic and potentially complex vault interactions. This prevents a full assessment of the protocol's primary functionality and introduces significant unknown risks. The provided `Governable` contract implements a robust two-step governance transfer and a secure reentrancy guard. However, the high centralization of power with the governor role and potential storage collision risks due to the missing `OUSD` source are notable concerns.

> **Final Recommendation:** A comprehensive security audit of the `OUSD` contract and all its dependencies is paramount to ensure the overall integrity and security of the Origin Ether protocol. Implement a multi-signature wallet for the governor address to mitigate centralization risks and consider time-locks for sensitive administrative actions. Thoroughly review and test the storage layout of all contracts in the inheritance chain to prevent potential storage collisions during future upgrades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture includes a UUPS proxy and a `Governable` contract providing robust access control and a reentrancy guard. The `nonReentrant` modifier is correctly implemented using… |
| **Governance / Economics** | 1/10 | High | The governance model features a secure two-step transfer process for the governor role, enhancing operational safety. The governor holds significant power, as is typical for such protocols, with the… |
| **Upgrades** | 1/10 | High | The system utilizes an EIP-1967 UUPS proxy pattern, with the `Governable` contract correctly employing fixed storage slots for its state variables to prevent collisions during upgrades. This design… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Core Logic (`OUSD`) Source Code Not Provided for Audit  *(Severity: Critical · Status: Unresolved)*

The `OETH` contract inherits from `OUSD`, which is expected to contain the primary ERC-20 token logic (minting, burning, transfers) and potentially the complex vault and strategy interactions hinted at by the `IVault` interface. Without the source code for `OUSD`, a comprehensive security audit of the `OETH` token's core functionality and its interactions within the broader protocol is impossible. This leaves a significant portion of the system unaudited, posing an unknown but potentially critical risk. (7.1 Architecture, 7.2 Code Security, 7.4 Economic)

**Recommendation:** Provide the complete source code for the `OUSD` contract and all its dependencies for a full security review. All inherited contracts and their logic are crucial for understanding the overall system's security posture.


### `H-01` — High Centralization of Power with Governor Role  *(Severity: High · Status: Unresolved)*

The `Governable` contract implements an `onlyGovernor` modifier, granting a single address extensive control over critical functions. While the specific functions controlled by the governor in `OUSD` are unknown, the `IVault` interface suggests the governor can manage strategies, set fees, pause/unpause capital and rebases, update price providers, and change various thresholds. A compromise of the governor's private key could lead to significant financial loss, manipulation of the protocol, or even a rug pull. (7.3 Access Control, 7.5 Governance, 7.8 Operations)

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the governor address to distribute control and reduce the single point of failure risk. Consider time-locks for critical operations to allow users to react to malicious actions.


### `M-01` — Potential Storage Collisions in UUPS Proxy Implementation  *(Severity: Medium · Status: Unresolved)*

The `Governable` contract uses fixed storage slots (`governorPosition`, `pendingGovernorPosition`, `reentryStatusPosition`) for its state variables, which is a standard practice for UUPS proxy implementations to prevent storage collisions with the proxy contract itself. However, without the `OUSD` source code, it's impossible to verify that `OUSD` (and any contracts it inherits from) also correctly manages its storage slots, especially if it introduces new state variables or uses `_initialize` functions. Incorrect storage slot management in `OUSD` could lead to critical state corruption upon upgrade. (7.1 Architecture, 7.7 Upgrades)

**Recommendation:** Ensure that the `OUSD` contract and all its base contracts adhere to a strict storage layout, explicitly defining storage slots for all state variables using `bytes32` positions or ensuring no new state variables are introduced in the first storage slot of the implementation contract if using the standard UUPS layout. A thorough storage slot analysis of the entire inheritance hierarchy is required.


### `L-01` — Extensive `IVault` Interface Implies High Complexity  *(Severity: Low · Status: Unresolved)*

The `IVault` interface, which `OUSD` is likely to implement or interact with, exposes a large number of functions for managing assets, strategies, fees, and various protocol parameters. While interfaces themselves don't introduce vulnerabilities, the sheer volume and scope of configurable parameters and external interactions implied by this interface suggest a highly complex system. Increased complexity inherently leads to a larger attack surface and a higher potential for subtle bugs or misconfigurations, especially when interacting with multiple external strategies and price providers. (7.1 Architecture, 7.2 Code Security)

**Recommendation:** Implement robust testing, including unit, integration, and fuzz testing, for all functions related to the `IVault` interface. Ensure comprehensive documentation of all configurable parameters and their impact. Consider modularizing complex logic where possible to reduce cognitive load and potential for errors.


### `I-01` — Missing `_initialize` Function in Provided Scope  *(Severity: Informational · Status: Unresolved)*

For UUPS proxy contracts, an `_initialize` function is crucial for setting initial state variables (like the governor) upon deployment of the implementation contract through the proxy. While `Governable` provides `_setGovernor`, the actual `_initialize` function is not present in the provided `OETH` or `Governable` code. It is presumed to exist in the `OUSD` contract. Without it, the contract would not be properly initialized, leading to an unowned or unconfigured state. (7.1 Architecture, 7.8 Operations)

**Recommendation:** Ensure that the `OUSD` contract or one of its base contracts correctly implements an `_initialize` function that is called exactly once upon proxy deployment to set up the initial state, including the governor. This function should include an `initializer` modifier to prevent re-initialization attacks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x856c...8dc3`](https://etherscan.io/address/0x856c4efb76c1d1ae02e20ceb03a2a6a08b0b8dc3) |
| **Network** | Ethereum |
| **Price** | $2,505.4600 |
| **24h Volume** | $1.54M |
| **Liquidity** | $59.70M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 97.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 60 buys / 74 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xcc7d5785ad5755b6164e21495e07adb0ff11c2a8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/origin-ether-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
