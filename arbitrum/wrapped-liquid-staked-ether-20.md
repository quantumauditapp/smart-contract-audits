---
token: Wrapped liquid staked Ether 2.0
ticker: WSTETH
network: arbitrum
risk_score: 53
status: high
date: 2026-08-11
---

# Wrapped liquid staked Ether 2.0 (WSTETH) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 53/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-liquid-staked-ether-20-arb)

---

## Audit Summary

The audit of the ERC20Bridged token implementation, deployed behind an OssifiableProxy, revealed critical vulnerabilities primarily stemming from incorrect handling of immutable variables and an unprotected initialization function within a proxy context. These issues lead to a complete bypass of the bridge's access control, allowing unauthorized minting/burning, and enable anyone to set the token's metadata. Additionally, significant centralization risk exists with the bridge address, and potential storage collision concerns were identified. The overall risk level is Critical.

> **Final Recommendation:** Immediate action is required to address the critical proxy implementation flaws. The use of 'immutable' variables for 'bridge' and 'decimals' must be removed; these values should be stored as regular state variables and initialized via an access-controlled initializer function. The 'initialize' function must be protected with an appropriate access control mechanism, such as 'onlyOwner' or a dedicated 'initializer' role, to prevent unauthorized metadata changes. A thorough review of the proxy's initialization process and storage layout is essential to ensure all critical state variables are correctly managed within the proxy's context. Consider adopting a well-audited proxy standard like UUPS or Transparent Proxy with OpenZeppelin's `Initializable` pattern to prevent similar issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The ERC20Bridged token implements standard ERC-20 functionality with custom mint/burn capabilities controlled by a 'bridge' address. The core ERC-20 logic in ERC20Core is generally well-structured… |
| **Governance / Economics** | 1/10 | High | The economic model of the ERC20Bridged token relies heavily on the security and integrity of the designated 'bridge' address. This address holds absolute power over the token's supply through the… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for an OssifiableProxy (Transparent Proxy), which is a standard upgradeability pattern (7.7 Upgrades). However, the use of 'immutable' variables… |

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
| **Top-1 Unlocked Holder** | ⚠️ 77.1% |
| **Top-3 Unlocked** | ⚠️ 96.9% |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 1 Medium_

### `C-01` — Critical: Immutable Variables Incompatible with Proxy Pattern  *(Severity: Critical · Status: Unresolved)*

The `ERC20Bridged` contract declares `bridge` as an `immutable` variable, and `ERC20Metadata` declares `decimals` as `immutable`. When an implementation contract with `immutable` variables is deployed behind a proxy, these variables are set during the implementation's constructor execution and are stored in the implementation's bytecode or a special storage area, not in the proxy's delegated storage. Consequently, when calls are made through the proxy, `bridge` will always evaluate to `address(0)` and `decimals` will always evaluate to `0`. This renders the `onlyBridge` modifier ineffective, allowing any non-zero address to call `bridgeMint` and `bridgeBurn`, and causes the `decimals()` fun…

**Recommendation:** Remove the `immutable` keyword from `bridge` and `decimals`. These variables should be declared as regular state variables and initialized via an access-controlled initializer function (e.g., `initialize(..., address bridge_, uint8 decimals_)`) that is called only once through the proxy. Ensure the initializer function is properly protected to prevent re-initialization.


### `C-02` — Critical: Unprotected Initialization Function  *(Severity: Critical · Status: Unresolved)*

The `initialize` function in `ERC20Bridged` allows setting the token's `name` and `symbol` via `_setERC20MetadataName` and `_setERC20MetadataSymbol`. This function lacks any access control (e.g., `onlyOwner` or `initializer` modifier). When the contract is deployed as an implementation behind a proxy, the proxy's storage for `name` and `symbol` will initially be empty. This allows any external caller to invoke `initialize` through the proxy and set arbitrary `name` and `symbol` values for the token, leading to potential manipulation of the token's identity.

**Recommendation:** Implement robust access control for the `initialize` function. It should be callable only once by a trusted entity (e.g., the contract owner or a dedicated deployer address) during the proxy's initialization. Consider using OpenZeppelin's `Initializable` base contract and its `initializer` modifier for secure proxy initialization.


### `H-01` — High: Centralization Risk with Bridge Address  *(Severity: High · Status: Unresolved)*

The `bridge` address has absolute control over the token's supply through the `bridgeMint` and `bridgeBurn` functions. If this address is compromised, an attacker could mint an arbitrary amount of tokens or burn existing tokens, leading to severe economic instability and loss of user funds. While this is a common design for bridged tokens, the single point of failure represents a significant centralization risk.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `bridge` address to distribute control and require multiple approvals for critical operations. Alternatively, explore time-locks or governance mechanisms to introduce delays or community oversight for `bridgeMint` and `bridgeBurn` operations.


### `M-01` — Medium: Potential for Storage Collisions with Custom Metadata Slot  *(Severity: Medium · Status: Unresolved)*

The `ERC20Metadata` contract uses a custom storage slot (`DYNAMIC_METADATA_SLOT = keccak256("ERC20Metdata.dynamicMetadata")`) for storing the token's `name` and `symbol`. While using a `keccak256` hash for a storage slot is a common technique to avoid collisions with standard storage variables, it introduces a potential risk in future upgrades. If a new version of the contract or a base contract introduces a state variable that happens to occupy this specific storage slot, it could lead to a storage collision, corrupting data or causing unexpected behavior.

**Recommendation:** Ensure that any future upgrades or modifications to the contract's storage layout are meticulously reviewed for potential collisions with this custom slot. Document this custom slot clearly in the contract's design specifications. Consider using a more explicit 'gap' array or OpenZeppelin's `ERC1967Storage` pattern for proxy-safe storage management, although the current approach is generally considered safer than direct slot assignment for custom data.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5979...0529`](https://arbiscan.io/address/0x5979d7b546e38e414f7e9822514be443a4800529) |
| **Network** | Arbitrum |
| **Price** | $2,333.9500 |
| **24h Volume** | $224.7K |
| **Liquidity** | $746.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 3y |
| **Top-10 Holders** | 77.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 115 buys / 46 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x35218a1cbac5bbc3e57fd9bd38219d37571b3537)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-liquid-staked-ether-20-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
