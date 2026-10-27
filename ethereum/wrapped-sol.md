---
token: Wrapped SOL
ticker: SOL
network: ethereum
risk_score: 31
status: low
date: 2026-09-28
---

# Wrapped SOL (SOL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-sol-eth)

---

## Audit Summary

This audit covers the implementation contract (TokenImplementation) for the BridgeToken proxy. The contract utilizes a UUPS proxy pattern with `ERC1967Upgrade` and `Ownable` for access control. Key findings include critical vulnerabilities related to upgrade authorization and proper initialization, which could lead to unauthorized contract upgrades or an unowned state. The contract employs good practices for storage management with a dedicated `TokenStorage` struct, but the core ERC-20 functionality is not fully provided for review.

> **Final Recommendation:** It is imperative to implement a robust `_authorizeUpgrade` function within the `TokenImplementation` contract, ensuring that only authorized entities (e.g., the contract owner) can initiate upgrades. Concurrently, a dedicated `initialize` function must be added to correctly set the contract owner and all other initial state variables in the proxy's storage, protected by an `initialized` flag to prevent re-initialization. These actions are crucial to secure the contract against unauthorized control and ensure proper operational setup.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract's architecture (7.1) follows a UUPS proxy pattern, utilizing `TokenStorage` for explicit state management and `Ownable` for access control. Code security (7.2) generally appears robust… |
| **Governance / Economics** | 7/10 | Low | The contract implements a centralized ownership model (7.5) via the `Ownable` pattern, allowing the owner to manage critical functions like `transferOwnership` and `renounceOwnership`. No complex… |
| **Upgrades** | 1/10 | High | The contract uses `ERC1967Upgrade` for UUPS upgradeability (7.7). However, two critical issues were identified: the `_authorizeUpgrade` function, essential for restricting who can initiate an… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 14.7% |
| **Top-3 Unlocked** | 37.2% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Missing `_authorizeUpgrade` Implementation in UUPS  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC1967Upgrade` abstract contract is included, indicating a UUPS proxy pattern. However, the critical `_authorizeUpgrade` function, which is responsible for restricting who can initiate an upgrade via `_upgradeTo`, is not provided in the given code. Without a proper implementation of `_authorizeUpgrade` (e.g., using `onlyOwner`), any address could potentially call `_upgradeTo` and change the contract's logic, leading to a complete loss of control over the contract and potential manipulation of assets.

**Recommendation:** Implement the `_authorizeUpgrade` function within the `TokenImplementation` contract. This function should enforce strict access control, typically allowing only the contract owner or a designated governance mechanism to authorize upgrades. For example: ```solidity function _authorizeUpgrade(address newImplementation) internal override onlyOwner {} ```


### `M-02` — Improper Initialization of Owner and State in UUPS  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In a UUPS proxy setup, the `constructor` of the implementation contract is executed only once upon its initial deployment, not when the proxy is initialized. The `Ownable` constructor attempts to set the `_owner` variable to `msg.sender`. However, this assignment affects the implementation's storage, not the proxy's storage, which is where the actual state resides. Consequently, the `_owner` variable within the `TokenStorage.State` struct (which is the proxy's storage) will remain unset. An explicit `initialize` function, protected by an `initialized` flag (which exists in `TokenStorage.State`), is required to correctl

**Recommendation:** Implement an `initialize` function that sets the owner and all other necessary initial state variables. This function must be callable only once and protected by the `initialized` flag. For example: ```solidity function initialize(string memory name_, string memory symbol_, uint8 decimals_, address owner_) public initializer {     require(!_state.initialized, "Already initialized");     _state.name = name_;     _state.symbol = symbol_;     _state.decimals = decimals_;     _setOwner(owner_); //…


### `L-01` — Incomplete ERC-20 Implementation Provided  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract defines state variables typical for an ERC-20 token (e.g., `balances`, `allowances`, `totalSupply`, `name`, `symbol`, `decimals`). However, the core functions for ERC-20 operations such as `transfer`, `transferFrom`, `approve`, `mint`, and `burn` are not included in the provided source code. While this is not a direct vulnerability in the provided snippet, it means the full functionality and security implications of the token's operations cannot be assessed. Any unreviewed token logic could introduce vulnerabilities.

**Recommendation:** Ensure that the complete ERC-20 implementation, including all transfer, approval, minting, and burning logic, adheres to the ERC-20 standard and best security practices. If these functions are implemented elsewhere or inherited, verify their correctness and security. Consider using battle-tested libraries like OpenZeppelin for standard token functionality.


### `I-01` — Explicit Storage Management with `TokenStorage` Struct  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes a `TokenStorage.State` struct to define all its state variables. This is a robust and recommended pattern for upgradeable contracts, particularly in UUPS proxies. By centralizing storage definition, it helps manage the storage layout and prevent storage collisions when upgrading to new implementation versions, provided the struct is only appended to and existing fields are not reordered or removed.

**Recommendation:** Continue to use this explicit storage management pattern. When performing upgrades, ensure that any changes to the `TokenStorage.State` struct are strictly additive (new variables are appended to the end) and that existing variable types or order are not modified to prevent storage collisions and data corruption.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd31a...b89c`](https://etherscan.io/address/0xd31a59c85ae9d8edefec411d448f90841571b89c) |
| **Network** | Ethereum |
| **Price** | $118.0026 |
| **24h Volume** | $120.0K |
| **Liquidity** | $1.01M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4y |
| **Top-10 Holders** | 21.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 94 buys / 91 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x127452f3f9cdc0389b0bf59ce6131aa3bd763598)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-sol-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
