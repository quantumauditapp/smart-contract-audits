---
token: WebKey DAO 2.0
ticker: WKEYDAO2
network: bsc
risk_score: 67
status: high
date: 2026-07-23
---

# WebKey DAO 2.0 (WKEYDAO2) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/webkey-dao-20-bsc)

---

## Audit Summary

The wkeyDAO2 contract implements an ERC20 token with EIP-2612 permit functionality and OpenZeppelin's AccessControl. While it utilizes SafeMath for arithmetic operations and correctly implements the permit mechanism, a critical vulnerability exists due to a truncated access control modifier. Additionally, the contract uses an outdated Solidity compiler version and lacks an upgrade mechanism, posing further risks. Centralized control over administrative roles is also noted.

> **Final Recommendation:** Address the critical issue of the truncated `onlyVault` modifier immediately by completing or removing it, as it poses a severe security risk. Consider upgrading the Solidity compiler to a more recent version (0.8.x or higher) to benefit from native overflow checks and improved security features. Evaluate the need for an upgradeability mechanism to allow for future bug fixes or feature enhancements without requiring a full redeployment. Clearly define and implement the intended access control for all sensitive functions, especially those related to token minting, to ensure proper decentralization or controlled administration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates a foundational understanding of ERC20 standards and integrates OpenZeppelin's AccessControl and SafeMath libraries, mitigating common integer overflow/underflow risks (7.2… |
| **Governance / Economics** | 2/10 | High | The contract utilizes OpenZeppelin's AccessControl, with the deployer assigned the `DEFAULT_ADMIN_ROLE` in the `VaultOwned` constructor, centralizing significant administrative power (7.5… |
| **Upgrades** | 4/10 | Medium | The contract is deployed as a standard, non-upgradeable contract (7.7 Upgrades). This means that once deployed, its logic cannot be modified. Any discovered vulnerabilities, bugs, or desired feature… |

## Security Findings

_🔴 1 Critical · 🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incomplete `onlyVault` Modifier Leads to Critical Access Control Flaw  *(Severity: Critical · Status: Unresolved)*

The `onlyVault` modifier in the `VaultOwned` contract is truncated (`require(ha...`). This incomplete code will either cause any function using this modifier to permanently revert upon deployment (if 'ha' is an undeclared variable or invalid expression) or, more critically, could be interpreted by the compiler in a way that bypasses the intended access control entirely, allowing unauthorized execution of restricted functions. This represents a severe vulnerability, compromising the integrity of any function it protects.

**Recommendation:** Complete the `onlyVault` modifier with its intended logic. Ensure the `require` statement correctly validates the caller's address against a designated vault address or role. If this modifier is not intended for use, it should be removed to prevent unexpected behavior.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version 0.7.5. While `SafeMath` is used to prevent integer overflows/underflows, newer compiler versions (0.8.x and above) include native overflow/underflow checks, which can simplify code and potentially reduce gas costs by removing the need for `SafeMath` library calls. Additionally, older compiler versions may have undiscovered bugs or lack optimizations and security features present in more recent releases.

**Recommendation:** Consider upgrading the Solidity compiler to a more recent stable version (e.g., 0.8.x or higher). This would allow for the removal of `SafeMath` and benefit from native overflow checks, improving code readability and potentially security. Thoroughly test the contract after any compiler upgrade.


### `M-02` — Centralized Control Over Critical Roles  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` is assigned to the contract deployer in the `VaultOwned` constructor. This grants the deployer significant control over the contract's access control, including the ability to grant and revoke other roles. A `MINT` role is defined but not explicitly used in the provided `ERC20` snippet to restrict the `_mint` function. If minting is intended to be restricted, this centralization of administrative power, especially if the `MINT` role is also controlled by a single entity, introduces a single point of failure and a high degree of trust in the deployer.

**Recommendation:** Implement a multi-signature wallet or a more decentralized governance mechanism for managing critical roles like `DEFAULT_ADMIN_ROLE` and `MINT`. If the `MINT` role is intended to restrict token minting, ensure it is properly applied to the `_mint` function. Clearly document the responsibilities and powers associated with each role.


### `M-03` — Lack of Upgradeability  *(Severity: Medium · Status: Unresolved)*

The contract is deployed as a standard, non-upgradeable contract. This design choice means that the contract's logic is immutable once deployed. Any future bug fixes, security patches, or desired feature enhancements would require deploying an entirely new contract and migrating all existing users and assets, which is a complex, costly, and risky operation. This lack of flexibility can hinder long-term maintenance and responsiveness to unforeseen issues.

**Recommendation:** For long-lived protocols, consider implementing an upgradeability pattern (e.g., UUPS or Transparent Proxy) to allow for future contract logic updates. If upgradeability is not desired, ensure the contract is thoroughly audited and tested to minimize the risk of needing a redeployment. Clearly communicate the immutability to users.


### `L-01` — Permit Function Susceptible to Front-Running  *(Severity: Low · Status: Unresolved)*

The `permit` function, while correctly implemented according to EIP-2612, is inherently susceptible to front-running. A malicious actor could observe a pending `permit` transaction and front-run it. For example, if the `owner` has an existing allowance for the `spender`, the `spender` could front-run with a `transferFrom` call to drain funds before the `permit` transaction updates the allowance. While the `nonces` mechanism prevents replay attacks, it does not fully mitigate front-running risks related to allowance manipulation.

**Recommendation:** Educate users about the potential for front-running when using the `permit` function. While this is a known characteristic of EIP-2612 and not a specific implementation flaw, users should be aware of the risks, especially when interacting with untrusted or high-latency networks. Consider using transaction relays that can help mitigate some front-running vectors.


### `I-01` — Unused `MINT` Role Definition  *(Severity: Informational · Status: Unresolved)*

The `MINT` role is defined in the `VaultOwned` contract (`bytes32 public constant MINT = keccak256("MINT");`) but is not utilized in the provided `ERC20` contract snippet to restrict the `_mint` function. If the intention is to control who can mint tokens, this role should be enforced on the `_mint` function or a wrapper around it.

**Recommendation:** If the `MINT` role is intended to restrict token minting, ensure it is applied to the `_mint` function (or a public/external function that calls `_mint`) using `onlyRole(MINT)`. If the role is not intended for use, consider removing its definition to avoid confusion and unnecessary code.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe0a2...b82e`](https://bscscan.com/address/0xe0a281deff5c9d8d67af09d39340e134ac81b82e) |
| **Network** | BNB Chain |
| **Price** | $1.0350 |
| **24h Volume** | $352.1K |
| **Liquidity** | $26.63M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3505 buys / 16586 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb720ea2a201c03578cca05191e8b4ab859704cfe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/webkey-dao-20-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
