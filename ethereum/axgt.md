---
token: AXGT
ticker: AXGT
network: ethereum
risk_score: 64
status: medium
date: 2026-09-01
---

# AXGT (AXGT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/axgt-eth)

---

## Audit Summary

This audit covers the provided Solidity source code, which primarily consists of OpenZeppelin's abstract ERC20, ERC20Burnable, and ERC20Permit contracts, along with related interfaces and libraries. A significant limitation of this audit is the absence of the concrete 'AXGT' token contract that would inherit from these abstract components and define its specific logic, initial supply, and access control mechanisms. Therefore, the assessment is based on the provided building blocks and potential implications for a derived token. The underlying OpenZeppelin components are well-audited and robust, but the overall risk is elevated due to the inability to review the final implementation.

> **Final Recommendation:** To enhance the security posture, it is crucial to provide the full source code for the concrete AXGT token contract for a comprehensive audit. This would allow for a thorough review of its constructor, initial supply, any custom logic, and critically, the access control mechanisms around sensitive functions like `_mint`. If a centralized minting capability is intended, consider implementing a timelock or multi-signature wallet for the owner address to mitigate single points of failure. Additionally, consolidate Solidity pragma directives for improved code clarity and consistency.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is based on standard, well-vetted OpenZeppelin ERC20 components, which is a significant strength, ensuring robust code security (7.2) against common vulnerabilities… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) is that of a standard ERC20 token with burn functionality. The `_mint` function is internal, meaning its exposure in the concrete token contract could introduce centralized… |
| **Upgrades** | 8/10 | Low | Based on the provided information, the contract is not identified as a proxy (`is_proxy: false`) and has no associated implementation contract. Therefore, the contract is not upgradeable (7.7). This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 11.7% — UNCX Locker |
| **Top-1 Unlocked Holder** | ⚠️ 88.0% |
| **Top-3 Unlocked** | ⚠️ 88.3% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing Concrete Token Implementation  *(Severity: High · Status: Unresolved)*

The provided source code consists primarily of abstract contracts and interfaces (e.g., `ERC20`, `ERC20Burnable`, `ERC20Permit`, `ECDSA`). The actual concrete token contract, which would inherit from these abstract components and define its constructor, initial supply, and any custom logic, is not included. This prevents a complete security assessment of the token's specific behavior, initial state, and critical access control mechanisms.

**Recommendation:** Provide the full source code for the concrete AXGT token contract. This is essential for a comprehensive audit to evaluate its specific implementation details, initial minting, any additional custom logic, and access control for sensitive functions.


### `M-01` — Centralized Minting Capability (Potential)  *(Severity: Medium · Status: Unresolved)*

The `_mint` function, which increases the total supply, is internal to the `ERC20` contract. If the concrete AXGT token contract exposes a public or external function that calls `_mint` and this function is protected by an `onlyOwner` or similar access control, it introduces a centralized point of control over the token supply. A compromise of the owner's private key could lead to arbitrary token inflation, devaluing existing tokens.

**Recommendation:** If centralized minting is intended, ensure robust access control (e.g., a multi-signature wallet or a timelock) for the owner address. Consider a mechanism to renounce minting capabilities after initial supply distribution if a fixed supply is desired long-term. Clearly document the minting policy and its implications.


### `L-01` — Multiple Solidity Pragma Directives  *(Severity: Low · Status: Unresolved)*

The codebase uses multiple `pragma solidity` directives across different files/sections (e.g., `>=0.4.16`, `>=0.6.2`, `^0.8.20`, `>=0.8.4`). While the compiler typically resolves this by using the highest compatible version, it can lead to confusion and potential inconsistencies in compiler behavior or linting tools.

**Recommendation:** It is best practice to use a single, explicit `pragma solidity` directive (e.g., `pragma solidity 0.8.20;` or `pragma solidity ^0.8.20;`) consistently across all contract files within the project. This improves clarity and ensures consistent compilation behavior.


### `I-01` — Standard OpenZeppelin Implementation  *(Severity: Informational · Status: Resolved)*

The core ERC20, ERC20Burnable, and ERC20Permit functionalities are implemented using well-audited and widely adopted OpenZeppelin contracts. This significantly reduces the likelihood of common vulnerabilities such as reentrancy, integer overflows/underflows (outside of explicitly `unchecked` blocks where safety is guaranteed by preceding logic), and standard ERC20 compliance issues. The `permit` function correctly utilizes `nonces` to prevent replay attacks.

**Recommendation:** Continue to leverage battle-tested libraries like OpenZeppelin for core functionalities. Ensure that any custom logic added in the concrete token contract adheres to similar security standards and best practices.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6112...274d`](https://etherscan.io/address/0x6112c3509a8a787df576028450febb3786a2274d) |
| **Network** | Ethereum |
| **Price** | $0.0262 |
| **24h Volume** | $89.0K |
| **Liquidity** | $326.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 75.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 917 buys / 112 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf9c56a9ccc1398bed3c519ef2f0b42ce52aaa440)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/axgt-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
