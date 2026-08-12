---
token: Wrapped liquid staked Ether 2.0
ticker: WSTETH
network: base
risk_score: 47
status: high
date: 2026-08-12
---

# Wrapped liquid staked Ether 2.0 (WSTETH) — Smart Contract Security Analysis | Base

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-liquid-staked-ether-20-base)

---

## Audit Summary

The ERC20Bridged token, deployed via an OssifiableProxy, implements standard ERC20 functionality with additional bridge-specific minting and burning capabilities. The core logic for token transfers and allowances appears robust, utilizing Solidity 0.8.10's default overflow/underflow checks and explicit `unchecked` blocks where appropriate. However, critical design flaws exist in the contract's interaction with the proxy pattern, specifically regarding state variable initialization and the use of `immutable` variables, leading to an uninitialized bridge address and an ineffective `initialize` function. These issues severely impact the token's intended functionality and upgradeability.

> **Final Recommendation:** It is critical to refactor the `ERC20Bridged` contract to correctly implement the proxy pattern. All state-modifying logic, especially for critical parameters like the `bridge` address, `name`, `symbol`, and `decimals`, must be moved from the constructor to an initializer function. The `bridge` variable should be a regular state variable, not `immutable`, and set by this initializer. The initializer function must be protected with robust access control (e.g., `onlyOwner` or a dedicated initializer role) and called exactly once on the proxy contract after deployment. Thoroughly test the initialization process in a development environment before redeployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The ERC20Bridged contract implements standard ERC20 functionalities (7.2 Code Security) with custom `_mint` and `_burn` methods protected by an `onlyBridge` modifier (7.3 Access Control). The use of… |
| **Governance / Economics** | 1/10 | High | The economic model of the ERC20Bridged token is straightforward, functioning as a standard ERC20 with controlled minting and burning capabilities (7.4 Economic). The `bridgeMint` and `bridgeBurn`… |
| **Upgrades** | 1/10 | High | The contract is deployed behind an OssifiableProxy, indicating an intention for upgradeability (7.7 Upgrades). However, the current implementation has critical upgrade safety issues. The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 59.0% |
| **Top-3 Unlocked** | 72.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟢 1 Low_

### `C-01` — Critical Proxy Initialization Flaw & Uninitialized Bridge Address  *(Severity: Critical · Status: Unresolved)*

The `ERC20Bridged` implementation contract's constructor sets critical state variables (`decimals`, `name`, `symbol`, and crucially, the `bridge` address) using `immutable` for `bridge`. When deployed behind a proxy (like `OssifiableProxy`), the constructor is only executed once during the implementation's deployment, not during the proxy's initialization. Consequently, the `bridge` address in the proxy's storage will remain `address(0)`, rendering the `bridgeMint` and `bridgeBurn` functions unusable as they are protected by `onlyBridge`. This fundamentally breaks the core functionality of a bridged token (7.1 Architecture, 7.7 Upgrades).

**Recommendation:** All state-modifying logic, especially for critical parameters like the `bridge` address, `name`, `symbol`, and `decimals`, must be moved from the constructor to an initializer function (e.g., `initialize`). The `bridge` variable should not be `immutable` but a regular state variable set by the initializer. The initializer must then be called *once* on the proxy contract after deployment.


### `H-01` — Unprotected and Ineffective `initialize` Function  *(Severity: High · Status: Unresolved)*

The `initialize` function in `ERC20Bridged` is intended for proxy initialization but lacks access control, allowing any external caller to execute it (7.3 Access Control). Furthermore, it attempts to set `name` and `symbol`, which are already set by the `ERC20Metadata` constructor. The `_setERC20MetadataName` and `_setERC20MetadataSymbol` functions revert if the metadata is already set, making `initialize` ineffective and prone to reverting if called. This design flaw prevents proper initialization of metadata via the proxy (7.7 Upgrades, 7.8 Operations).

**Recommendation:** Implement robust access control (e.g., `onlyOwner` or `onlyInitializer`) for the `initialize` function to ensure it can only be called once by an authorized entity. Refactor the `ERC20Metadata` constructor logic into the `initialize` function to avoid conflicts and ensure proper proxy initialization.


### `L-01` — Custom Storage Slot Usage for Metadata  *(Severity: Low · Status: Unresolved)*

The `ERC20Metadata` contract uses a custom storage slot (`DYNAMIC_METADATA_SLOT`) for storing `name` and `symbol`. While this is a valid technique, it introduces a dependency on this specific slot for future upgrades. Any change in the storage layout of `ERC20Metadata` or its base contracts must carefully account for this custom slot to prevent storage collisions or data corruption (7.7 Upgrades).

**Recommendation:** Document the custom storage slot usage clearly. During future upgrades, ensure that the storage layout of the new implementation contract is compatible with the existing proxy's storage, paying particular attention to this custom slot to avoid overwriting or misinterpreting data.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc1cb...e452`](https://basescan.org/address/0xc1cba3fcea344f92d9239c08c0568f6f2f0ee452) |
| **Network** | Base |
| **Price** | $2,361.6600 |
| **24h Volume** | $222.8K |
| **Liquidity** | $2.92M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 78.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 215 buys / 113 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x861a2922be165a5bd41b1e482b49216b465e1b5f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-liquid-staked-ether-20-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
