---
token: Radicle
ticker: RAD
network: ethereum
risk_score: 60
status: high
date: 2026-08-11
---

# Radicle (RAD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/radicle-eth)

---

## Audit Summary

The audit of the RadicleToken contract identified a critical issue due to incomplete source code, preventing a full security assessment of core functionalities. Key helper functions and a significant portion of the transfer logic are missing. Additionally, the contract deviates from the ERC-20 standard by using `uint96` for internal balances and allowances, which could lead to integration challenges and potential value truncation. While the contract implements EIP-712 for delegation and permits, the foundational issues with code completeness and non-standard data types pose significant risks.

> **Final Recommendation:** It is critical to provide the complete and accurate source code, including all helper functions (`safe96`, `sub96`, `getChainId`) and the full `_transferTokens` implementation, to enable a comprehensive security audit. The project should carefully evaluate the implications of using `uint96` for internal balances and allowances, considering potential compatibility issues and limitations for future growth, and consider migrating to `uint256` for full ERC-20 compliance. Additionally, consider upgrading the Solidity compiler to version 0.8.0 or higher to benefit from built-in overflow/underflow checks and other security enhancements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a standard ERC-20 token with additional governance features, including EIP-712 based delegation and permit functionality (7.2 Code Security). Nonces are correctly managed to… |
| **Governance / Economics** | 1/10 | High | The contract includes a Compound-style delegation mechanism, allowing token holders to delegate their voting power, which is a positive for decentralized governance (7.5 Governance). The `burnFrom`… |
| **Upgrades** | 6/10 | Medium | The RadicleToken contract is a standard implementation and does not incorporate any proxy patterns or upgradeability mechanisms (7.7 Upgrades). Therefore, it is not subject to upgrade-related risks. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Incomplete Code Provided for Audit  *(Severity: Critical · Status: Unresolved)*

The provided contract code is truncated, specifically the `_transferTokens` function, which is central to the token's core transfer logic. Additionally, the `safe96`, `sub96`, and `getChainId` helper functions, which are critical for arithmetic safety and EIP-712 domain separation, are not included. This prevents a comprehensive security assessment of critical arithmetic and core functionality, leaving significant portions of the contract unaudited.

**Recommendation:** Provide the complete and accurate source code for the RadicleToken contract, including the full `_transferTokens` function and all referenced helper functions (`safe96`, `sub96`, `getChainId`). Without the complete code, a thorough security assessment cannot be performed.


### `H-01` — Non-Standard `uint96` for ERC-20 Balances and Allowances  *(Severity: High · Status: Unresolved)*

The contract uses `uint96` for internal `balances` and `allowances` mappings, deviating from the ERC-20 standard's expectation of `uint256`. While external functions cast to `uint256`, this non-standard internal representation limits the maximum possible balance/allowance to `2^96 - 1` (approximately 7.9 x 10^28), which is significantly less than `2^256 - 1`. This could lead to unexpected behavior, truncation, or integration issues with systems expecting full `uint256` capacity, potentially causing loss of funds or operational failures if token values exceed `uint96` limits.

**Recommendation:** Consider refactoring the contract to use `uint256` for `balances` and `allowances` to fully comply with the ERC-20 standard and avoid potential issues with value truncation or integration with other DeFi protocols. If `uint96` is intentionally used for gas optimization, ensure all external interfaces and integrations are fully aware of and compatible with this limitation.


### `M-01` — Direct `uint256` Subtraction for `totalSupply`  *(Severity: Medium · Status: Unresolved)*

In the `burnFrom` function, `totalSupply -= rawAmount;` performs a direct `uint256` subtraction without explicit `SafeMath` or Solidity 0.8+ checked arithmetic. While `rawAmount` is constrained by `safe96` to fit `uint96` and `balances[account]` is checked via `sub96`, relying on these indirect checks for `totalSupply`'s `uint256` arithmetic is less robust. An edge case where `totalSupply` is less than `rawAmount` (e.g., due to an external bug or unexpected state) could lead to an underflow if not implicitly handled by the `sub96` check on `balances[account]`.

**Recommendation:** Implement explicit `SafeMath` for `uint256` operations, or upgrade the Solidity compiler to version 0.8.0 or higher, which includes built-in overflow/underflow checks. This would provide a more robust and explicit guarantee against `totalSupply` underflow.


### `I-01` — Use of Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with `pragma solidity ^0.7.5;`. While not a direct vulnerability, using an older compiler version means the contract does not benefit from security enhancements, bug fixes, and optimizations introduced in newer versions (e.g., implicit overflow/underflow checks in Solidity 0.8.0+).

**Recommendation:** Consider upgrading the Solidity compiler version to 0.8.0 or higher. This would allow the contract to leverage newer language features, security improvements, and optimizations, such as built-in overflow/underflow checks, reducing the need for custom `SafeMath` implementations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x31c8...64a3`](https://etherscan.io/address/0x31c8eacbffdd875c74b94b077895bd78cf1e64a3) |
| **Network** | Ethereum |
| **Price** | $0.2831 |
| **24h Volume** | $1.49M |
| **Liquidity** | $2.13M |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 5y |
| **Top-10 Holders** | 75.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 474 buys / 574 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8c1c499b1796d7f3c2521ac37186b52de024e58c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/radicle-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
