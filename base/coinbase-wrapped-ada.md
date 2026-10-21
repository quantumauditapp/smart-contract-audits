---
token: Coinbase Wrapped ADA
ticker: CBADA
network: base
risk_score: 66
status: high
date: 2026-09-19
---

# Coinbase Wrapped ADA (CBADA) — Smart Contract Security Analysis | Base

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-ada-base)

---

## Audit Summary

This audit covers the FiatTokenV2_2 contract, which serves as the implementation logic for an upgradeable ERC-20 token. The contract incorporates advanced features such as EIP-712 authorizations, blacklisting, and a custom bit-packed storage solution for balances and blacklist states. While the contract demonstrates careful implementation, the custom storage pattern introduces significant complexity and potential upgradeability challenges. Several findings highlight areas for review, particularly concerning storage layout, EIP-712 versioning, and non-standard initialization behaviors.

> **Final Recommendation:** It is recommended to thoroughly review the custom bit-packed storage pattern, especially in the context of future upgrades, to ensure robust storage compatibility and prevent potential data corruption. Consider external audits or formal verification for this critical component. For EIP-712 functionality, evaluate the implications of the hardcoded domain separator version and plan for potential future changes. Additionally, ensure all administrative roles (owner, pauser, blacklister) are secured with multi-signature wallets and follow robust operational security practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes SafeMath for arithmetic operations, mitigating common integer overflow/underflow vulnerabilities (7.2 Code Security). It also implements EIP-712 for gasless approvals and… |
| **Governance / Economics** | 1/10 | High | As a centralized stablecoin, the economic model inherently relies on an issuer with capabilities such as minting, burning, pausing, and blacklisting (7.4 Economic). The contract includes blacklisting… |
| **Upgrades** | 1/10 | High | The contract is designed to be upgradeable via a proxy pattern, with `FiatTokenV2_2` serving as an implementation contract. The `initializeV2_2` function manages the upgrade logic, including symbol… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Complex Custom Storage for Balances and Blacklisting  *(Severity: High · Status: Unresolved)*

The `balanceAndBlacklistStates` mapping uses a custom bit-packing strategy to store both the account balance (lower 255 bits) and the blacklist status (highest bit, 2^255) within a single `uint256`. While the `_setBalance`, `_balanceOf`, `_isBlacklisted`, and `_setBlacklistState` functions are designed to manage this, this non-standard storage pattern significantly increases complexity (7.1 Architecture, 7.2 Code Security). Any subtle error in bitwise operations or a misunderstanding of this pattern by future developers could lead to incorrect balances, incorrect blacklist states, or critical storage collisions during upgrades, potentially corrupting token data.

**Recommendation:** Thoroughly document the custom storage pattern, including its design rationale, invariants, and potential pitfalls. Consider formal verification for the bitwise operations to ensure their correctness under all conditions. For future versions, evaluate if a more standard storage approach (e.g., separate mappings for balances and blacklist status) could be adopted, even if it incurs higher gas costs, to reduce complexity and improve maintainability and upgrade safety.


### `M-01` — Hardcoded EIP-712 Domain Separator Version  *(Severity: Medium · Status: Unresolved)*

The `_domainSeparator()` function hardcodes the EIP-712 domain separator version as the string literal `"2"`. This value is used in the EIP-712 signature generation for functions like `permit` and `transferWithAuthorization` (7.2 Code Security). If a future protocol upgrade or a change in EIP-712 standards requires modifying this version identifier (e.g., to `"3"`), it would necessitate deploying an entirely new implementation contract. This limits the flexibility of future upgrades related to EIP-712 functionality.

**Recommendation:** Consider making the EIP-712 domain separator version configurable by an authorized role (e.g., owner or admin) through a setter function, or store it in a state variable that can be updated during an upgrade. This would allow for greater flexibility in adapting to future EIP-712 standard changes or protocol versioning without requiring a full contract redeployment.


### `M-02` — Unusual Self-Blacklisting in Initialization  *(Severity: Medium · Status: Unresolved)*

The `initializeV2_2` function explicitly blacklists `address(this)` (the contract itself) using `_blacklist(address(this))` (7.3 Access Control, 7.8 Operations). While this might be an intentional design choice to prevent the token contract from holding its own tokens, it is an unusual pattern. If the contract's functionality were to evolve to require holding tokens (e.g., for staking, liquidity provision, or integration with other protocols), this self-blacklisting would prevent such operations and could lead to unexpected behavior or stuck funds if tokens are inadvertently sent to the contract.

**Recommendation:** Clearly document the rationale behind blacklisting `address(this)` and its intended implications. Ensure that all current and future integrations and operational procedures are aware of this behavior and account for it. If there's any possibility the contract might need to hold tokens in the future, consider removing this self-blacklisting or implementing a mechanism for an authorized role to unblacklist the contract.


### `L-01` — Potential for User Front-running in EIP-712 Functions  *(Severity: Low · Status: Unresolved)*

Functions like `permit`, `transferWithAuthorization`, and `receiveWithAuthorization` rely on EIP-712 signed messages. While this enables gasless transactions, users are susceptible to front-running attacks (7.4 Economic, 7.6 External). A malicious actor could observe a pending signed transaction, reconstruct it, and submit their own transaction with a higher gas price to execute it first, potentially exploiting the user's signed intent. This is a common risk for off-chain signed transactions.

**Recommendation:** Advise users to always set a sufficiently short `deadline` for EIP-712 signed messages to minimize the window for front-running. Provide clear warnings and best practices in user-facing documentation regarding the risks associated with signed transactions and the importance of transaction deadlines.


### `I-01` — Use of Assembly for `_chainId()`  *(Severity: Informational · Status: Unresolved)*

The `_chainId()` function retrieves the chain ID using inline assembly (`assembly { chainId := chainid() }`) (7.2 Code Security). While this is a valid and common pattern in Solidity versions prior to 0.8.0, the `block.chainid` global variable provides a more readable and idiomatic way to access the chain ID in newer Solidity versions. Using assembly can sometimes introduce subtle bugs if not handled carefully.

**Recommendation:** For future upgrades to Solidity 0.8.0 or higher, consider replacing the inline assembly with `block.chainid` for improved readability and maintainability. For the current version, ensure the assembly code is thoroughly tested and understood.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcbad...7b8c`](https://basescan.org/address/0xcbada732173e39521cdbe8bf59a6dc85a9fc7b8c) |
| **Network** | Base |
| **Price** | $0.2233 |
| **24h Volume** | $691.3K |
| **Liquidity** | $105.7K |
| **Volume / Liquidity** | 6.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 472 buys / 532 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8782d97c8b25b4d17dbfbaa03f25dc18e51e909d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-ada-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-19*
