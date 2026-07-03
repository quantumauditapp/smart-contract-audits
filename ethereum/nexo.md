---
token: NEXO
ticker: NEXO
network: ethereum
risk_score: 100
status: critical
date: 2026-07-03
---

# NEXO (NEXO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nexo-eth)

---

## Audit Summary

The NexoToken contract implements the ERC-20 standard with additional features like a two-step ownership transfer and a mechanism for the owner to recover accidentally sent ERC20 tokens. It utilizes SafeMath for arithmetic safety. However, the contract is compiled with an outdated Solidity version (0.4.23), which introduces inherent risks. Key allocation addresses are hardcoded, and a significant portion of the vesting logic was truncated in the provided source, preventing a full security assessment of that critical component.

> **Final Recommendation:** The NexoToken contract provides a functional ERC-20 implementation with basic access control and arithmetic safety. However, the use of an outdated Solidity compiler version is a significant concern that should be addressed. The hardcoded allocation addresses limit future flexibility, and the incomplete vesting logic prevents a full audit of the token's distribution mechanics. 

It is recommended to migrate to a newer Solidity version, review the hardcoded addresses for potential future flexibility, and provide the complete vesting logic for a thorough security assessment. For critical deployments, consider a Premium Deploy option, which includes a comprehensive post-audit review and continuous monitoring to ensure ongoing security and address any emerging threats.

## Security Analysis

The NexoToken contract implements the ERC-20 standard with additional features like a two-step ownership transfer and a mechanism for the owner to recover accidentally sent ERC20 tokens. It utilizes SafeMath for arithmetic safety. However, the contract is compiled with an outdated Solidity version (0.4.23), which introduces inherent risks. Key allocation addresses are hardcoded, and a significant portion of the vesting logic was truncated in the provided source, preventing a full security assessment of that critical component.

The NexoToken contract provides a functional ERC-20 implementation with basic access control and arithmetic safety. However, the use of an outdated Solidity compiler version is a significant concern that should be addressed. The hardcoded allocation addresses limit future flexibility, and the incomplete vesting logic prevents a full audit of the token's distribution mechanics. 

It is recommended to migrate to a newer Solidity version, review the hardcoded addresses for potential future flexibility, and provide the complete vesting logic for a thorough security assessment. For critical deployments, consider a Premium Deploy option, which includes a comprehensive post-audit review and continuous monitoring to ensure ongoing security and address any emerging threats.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes the `SafeMath` library for arithmetic operations, preventing common integer overflow/underflow vulnerabilities in `add`, `sub`, `mul`, and `pow`. The `_transfer` function correct |
| **Governance / Economics** | 1/10 | High | The token adheres to the ERC-20 standard, ensuring broad compatibility within the ecosystem. The `transferERC20Token` function allows the owner to recover accidentally sent ERC20 tokens, protecting as |
| **Upgrades** | 4/10 | Medium | The contract is not designed with an upgrade mechanism, which eliminates the complexities and potential risks associated with proxy-based upgrades (7.7 Upgrades). This lack of upgradeability means tha |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.0% |
| **Top-3 Unlocked** | ⚠️ 91.5% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 2 Informational_

### `H-01` — Outdated Solidity Compiler Version  *(Severity: High · Status: Unresolved)*

The contract is compiled with Solidity version 0.4.23. This version is significantly outdated and lacks many security features, optimizations, and bug fixes present in newer compiler versions. Using an old compiler can expose the contract to known or undiscovered compiler bugs and makes it harder to integrate with modern tooling and best practices. For example, newer versions include features like `revert()` for gas refunds, improved optimizer, and more robust type checking.

**Recommendation:** It is strongly recommended to upgrade the Solidity compiler version to a recent stable release (e.8. 0.8.x). This would require a thorough review and potential refactoring of the code to adapt to syntax changes and new best practices. A full re-audit would be necessary after such an upgrade.


### `M-01` — ERC-20 `approve` Race Condition  *(Severity: Medium · Status: Unresolved)*

The standard ERC-20 `approve` function is susceptible to a known race condition. If a user calls `approve(spender, newAmount)` while `spender` is simultaneously trying to `transferFrom` an `oldAmount`, the `spender` might be able to spend both `oldAmount` and `newAmount` if the `newAmount` transaction is mined before the `transferFrom` transaction, but after the `approve` transaction has been broadcast. While `increaseApproval` and `decreaseApproval` functions are provided, the base `approve` function remains vulnerable.

**Recommendation:** While `increaseApproval` and `decreaseApproval` mitigate this for new approvals, users should be advised to use these functions instead of directly calling `approve` when modifying an existing allowance. For `approve` itself, consider implementing the 'approve and call' pattern or requiring the allowance to be zero before setting a new one, though this adds complexity.


### `M-02` — Hardcoded Allocation Addresses  *(Severity: Medium · Status: Unresolved)*

The allocation addresses (`investorsAllocation`, `overdraftAllocation`, `teamAllocation`) are hardcoded as `constant` variables. This design choice means these addresses cannot be changed after contract deployment. If any of these addresses become compromised, or if there's a need to update the recipient for legitimate reasons (e.g., multi-sig upgrade, change in team structure), it would be impossible without deploying a new contract.

**Recommendation:** Consider making critical allocation addresses configurable by the `owner` through setter functions. This would provide flexibility to adapt to future operational changes or security requirements. Any such setter functions should implement robust access control (e.g., `onlyOwner`) and potentially a multi-step confirmation process.


### `I-01` — Incomplete Vesting Logic Provided  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `NexoToken` contract is truncated, specifically cutting off in the middle of the vesting logic for 'Tokens reserved for Founders and Team'. This prevents a comprehensive security analysis of the vesting mechanisms, including how tokens are unlocked, distributed, and if there are any potential vulnerabilities related to timing, calculations, or access control within these critical functions.

**Recommendation:** Provide the complete and unabridged source code for all contracts, especially for critical components like vesting logic, to enable a thorough and accurate security audit.


### `I-02` — Use of `now` for `creationTime`  *(Severity: Informational · Status: Unresolved)*

The `creationTime` variable is set using `now` (an alias for `block.timestamp`). While generally acceptable for non-critical timestamps, `block.timestamp` can be manipulated by miners to a small extent (within a few seconds of the actual time). For `creationTime`, this is unlikely to be a critical issue as it's a one-time assignment.

**Recommendation:** For critical time-dependent operations, consider using a more robust time source if precise, unmanipulable timestamps are required, or acknowledge the minor manipulability of `block.timestamp`. In this specific context, the impact is minimal.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb621...5206`](https://etherscan.io/address/0xb62132e35a6c13ee1ee0f84dc5d40bad8d815206) |
| **Network** | Ethereum |
| **Price** | $0.7781 |
| **24h Volume** | $119.9K |
| **Liquidity** | $1.22M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 93.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27 buys / 86 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4c54ff7f1c424ff5487a32aad0b48b19cbaf087f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nexo-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-03*
