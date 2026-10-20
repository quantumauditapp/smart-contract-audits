---
token: EtherStreet
ticker: STREET
network: ethereum
risk_score: 62
status: medium
date: 2026-09-25
---

# EtherStreet (STREET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/etherstreet-eth)

---

## Audit Summary

The RobinVistaToken contract, deployed as an upgradeable proxy, exhibits a critical initialization vulnerability. The `initialize` function, intended for one-time setup, can be called by any address due to the proxy's storage being uninitialized for the `factory` variable. This allows an attacker to front-run the legitimate initializer, seize control of the token's initial supply, and dictate critical pool parameters. This severe flaw undermines the token's integrity and security.

> **Final Recommendation:** Immediately address the critical proxy initialization vulnerability by implementing a secure initialization pattern. This typically involves using an `initializer` modifier from OpenZeppelin's UUPS or TransparentUpgradeableProxy contracts, ensuring that the `initialize` function can only be called once by a designated address (e.g., the deployer or a trusted multisig). Additionally, review the roles and permissions of the `factory` address to ensure its capabilities align with the protocol's security model. Consider implementing a timelock for critical administrative actions if the `factory` retains significant control post-initialization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is a standard ERC20 token leveraging OpenZeppelin's robust base implementation, which generally provides strong code security against common vulnerabilities like integer overflows (7.2… |
| **Governance / Economics** | 1/10 | High | The contract design grants significant control to the `factory` address, which is responsible for initial token minting and setting critical `poolId` and `baseToken` parameters (7.4 Economic). While… |
| **Upgrades** | 5/10 | Medium | The contract is designed as an upgradeable proxy implementation (7.7 Upgrades). A critical vulnerability arises from the constructor setting `factory = address(0xdead)`, which only affects the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Critical: Proxy Initialization Vulnerability  *(Severity: Critical · Status: Unresolved)*

The `RobinVistaToken` contract is intended to be deployed behind an upgradeable proxy. The `initialize` function is designed for one-time setup, setting the `factory` address, token metadata, and minting the initial supply. However, the constructor of the implementation contract sets `factory = address(0xdead)`. In a proxy setup, the constructor of the implementation contract is called only once upon its deployment, not when the proxy is initialized. Therefore, when the `initialize` function is called through the proxy, the `factory` state variable in the proxy's storage will initially be `address(0)`. This means the `if (factory != address(0)) revert AlreadyInitialized();` check will pass…

**Recommendation:** Implement a secure initialization pattern. For UUPS proxies, use the `UUPSUpgradeable` base contract and its `_disableInitializers()` in the constructor. For Transparent proxies, ensure the `initialize` function is protected by an `initializer` modifier and called only once by a trusted address (e.g., the proxy admin) immediately after proxy deployment. The constructor of the implementation contract should not set any state variables that are meant to be initialized via the `initialize` functio…


### `M-01` — Medium: Centralized Control Over Pool Parameters  *(Severity: Medium · Status: Unresolved)*

The `setPool` function allows the `factory` address to set the `poolId` and `baseToken` once. While this is an intended design choice for initial setup, it represents a single point of control. If the `factory`'s private key is compromised (especially given the proxy initialization vulnerability), an attacker could set these critical parameters to malicious values, potentially disrupting the associated pool or ecosystem. The `deployer` address is also stored but has no associated privileges.

**Recommendation:** Consider adding a timelock for the `setPool` function if the `factory` is a single EOA, or transition control to a multi-signature wallet or a robust governance mechanism after initial setup. This would provide a delay for critical parameter changes, allowing for community review or intervention in case of a compromised key.


### `I-01` — Informational: Unused ERC20 Base Variables  *(Severity: Informational · Status: Unresolved)*

The `RobinVistaToken` contract inherits from OpenZeppelin's `ERC20` contract. The `ERC20` base contract has private state variables `_name` and `_symbol` which are initialized in its constructor. However, `RobinVistaToken` overrides the `name()` and `symbol()` functions to return its own private `_tokenName` and `_tokenSymbol` variables, which are set during the `initialize` call. As the `ERC20` constructor is not called on the proxy's storage, the base `_name` and `_symbol` variables will remain uninitialized (empty strings) in the proxy's storage, effectively wasting storage slots and potentially causing confusion.

**Recommendation:** To optimize storage and improve clarity, consider removing the `_tokenName` and `_tokenSymbol` variables from `RobinVistaToken` and instead directly initialize the `_name` and `_symbol` variables of the `ERC20` base contract within the `initialize` function. This would require making `_name` and `_symbol` in the base `ERC20` contract `internal` or providing internal setters.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2b1d...eac1`](https://etherscan.io/address/0x2b1d5b26efbd1ab8019dcd353adac3c09d04eac1) |
| **Network** | Ethereum |
| **Price** | $0.0002746 |
| **24h Volume** | $630.4K |
| **Liquidity** | $68.7K |
| **Volume / Liquidity** | 9.2× |
| **Token Age** | 16h |
| **Top-10 Holders** | 45.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 813 buys / 668 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8038e43ed1ba32c4259ce1cc537a08fa4b2a86d2616c22482a3af1641306d1a9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/etherstreet-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
