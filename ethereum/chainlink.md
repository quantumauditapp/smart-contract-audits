---
token: Chainlink
ticker: LINK
network: ethereum
risk_score: 58
status: high
date: 2026-06-10
---

# Chainlink (LINK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chainlink-eth)

---

## Audit Summary

The ChainLink Token contract implements ERC-20 and ERC-677 standards, utilizing SafeMath for arithmetic safety. However, the audit identified a critical issue where the public `totalSupply()` function incorrectly returns zero due to variable shadowing, significantly impacting ERC-20 compliance and integrations. Inconsistent `Transfer` event signatures between standard transfers and `transferAndCall` also pose integration challenges. Additionally, the `approve` function is susceptible to a known race condition, and the `validRecipient` modifier's implementation is incomplete in the provided source. The contract uses an outdated Solidity compiler version.

> **Final Recommendation:** It is strongly recommended to address the critical `totalSupply` shadowing issue immediately to ensure ERC-20 compliance and proper integration with external systems. The inconsistent `Transfer` event signatures should also be harmonized to prevent indexing and application errors. Implement a robust `validRecipient` modifier, ensuring it prevents transfers to the zero address. Consider migrating to a newer Solidity compiler version to benefit from security improvements and optimizations. While `increaseApproval` and `decreaseApproval` mitigate the `approve` race condition, developers should be aware of the base `approve` function's vulnerability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract architecture (7.1) is a standard ERC-20 and ERC-677 token implementation, leveraging the SafeMath library for robust integer overflow/underflow protection in arithmetic operations. This… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) of the LinkToken is straightforward, featuring a fixed total supply minted to the deployer. There are no complex fee structures, staking, or governance mechanisms (7.5)… |
| **Upgrades** | 7/10 | Low | The contract is not designed with any upgradeability patterns (7.7) such as UUPS or Transparent proxies. Therefore, there are no specific upgrade-related risks. Any changes to the token's logic would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 57.2% |
| **Top-3 Unlocked** | 70.9% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incorrect ERC-20 `totalSupply` Implementation  *(Severity: Critical · Status: Unresolved)*

The `LinkToken` contract declares `uint public constant totalSupply = 10**27;`, which shadows the `uint256 public totalSupply;` state variable inherited from `ERC20Basic`. While the constructor correctly uses the constant `totalSupply` to assign initial balances, the public getter function `totalSupply()` (which refers to the state variable) will always return 0. This violates the ERC-20 standard and will cause any external application or exchange relying on this function to misinterpret the token's total supply.

**Recommendation:** Remove the `constant` keyword from `LinkToken`'s `totalSupply` declaration and ensure the inherited `totalSupply` state variable is correctly initialized in the constructor, or explicitly set to the desired value. For example, `ERC20Basic.totalSupply = 10**27;` (if `ERC20Basic.totalSupply` was not `public` but `internal` or `protected` and accessible, or if `LinkToken` directly managed it). A common pattern is to set `_totalSupply = initialSupply;` in the constructor of the base token contract.


### `H-01` — Inconsistent ERC-677 `Transfer` Event Signatures  *(Severity: High · Status: Unresolved)*

The `ERC677Token` contract defines a `Transfer` event with an additional `bytes data` parameter, which conflicts with the standard `ERC20Basic` `Transfer` event signature. Consequently, `transferAndCall` emits the `ERC677` specific `Transfer` event, while standard `transfer` and `transferFrom` functions (inherited from `BasicToken` and `StandardToken`) emit the `ERC20Basic` `Transfer` event. This inconsistency can lead to issues for block explorers, indexers, and applications that expect a single, consistent `Transfer` event signature for all token movements.

**Recommendation:** To maintain full ERC-20 compatibility while supporting ERC-677, consider emitting both the ERC-20 `Transfer` event and the ERC-677 `Transfer` event (with `data`) for `transferAndCall` operations, or ensure that the `ERC677` event is emitted for all transfers, potentially with empty `data` for standard transfers, if the consuming applications can handle it. The most robust solution for full compatibility is often to emit the ERC-20 event for all transfers, and a separate, distinct event for `tra…


### `M-01` — ERC-20 `approve` Race Condition Vulnerability  *(Severity: Medium · Status: Unresolved)*

The `approve` function is susceptible to a known front-running attack. If a user attempts to change an allowance from amount X to amount Y, a malicious spender could front-run the transaction, spend X tokens, and then allow the original `approve` transaction to proceed, resulting in the spender having an allowance of Y tokens in addition to the X tokens already spent. While `increaseApproval` and `decreaseApproval` functions are provided to mitigate this, the base `approve` function remains callable and vulnerable.

**Recommendation:** Educate users to primarily use `increaseApproval` and `decreaseApproval` instead of `approve` when modifying existing allowances. For new allowances, `approve` is generally safe. Consider deprecating or adding a warning to the `approve` function if `allowed[msg.sender][_spender]` is not zero, forcing users to use the safer `increaseApproval`/`decreaseApproval` pattern.


### `M-02` — Truncated `validRecipient` Modifier Implementation  *(Severity: Medium · Status: Unresolved)*

The provided source code for the `validRecipient` modifier is truncated. This prevents a full security assessment of its intended checks. Without the complete implementation, it's impossible to verify if critical checks, such as preventing transfers to `address(0)` (the zero address), are correctly enforced. A missing `address(0)` check could lead to tokens being permanently locked if sent to the zero address.

**Recommendation:** Provide the complete and correct implementation of the `validRecipient` modifier. Ensure it includes checks to prevent transfers to `address(0)` and any other necessary recipient validations to prevent loss of funds or unexpected behavior.


### `L-01` — Outdated Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract uses `pragma solidity ^0.4.16;`. This is an outdated compiler version. Newer Solidity versions include numerous bug fixes, security enhancements, and gas optimizations. Using older versions may expose the contract to known compiler-related vulnerabilities or result in less efficient bytecode.

**Recommendation:** Consider upgrading the contract to a more recent and stable Solidity compiler version (e.g., `^0.8.x`). This would require thorough re-auditing and testing to ensure compatibility and prevent new issues introduced by syntax changes or new compiler behaviors.


### `I-01` — Potential DoS via `onTokenTransfer` Revert  *(Severity: Informational · Status: Unresolved)*

The `transferAndCall` function calls the `onTokenTransfer` function on the recipient contract. If a malicious recipient contract implements `onTokenTransfer` to always revert, it could prevent successful `transferAndCall` operations to that specific contract. While this is standard behavior for external calls and not a vulnerability in the token contract itself, it's a consideration for users interacting with potentially untrusted recipient contracts.

**Recommendation:** Users should be aware that `transferAndCall` operations to untrusted or poorly implemented contracts might fail if the recipient's `onTokenTransfer` function reverts. This is an inherent risk when interacting with external contracts. No direct change is needed in the token contract, but documentation could highlight this behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5149...86ca`](https://etherscan.io/address/0x514910771af9ca656af840dff83e8264ecf986ca) |
| **Network** | Ethereum |
| **Price** | $9.0049 |
| **24h Volume** | $3.83M |
| **Liquidity** | $20.77M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 32.8% of supply |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xa6cc3c2531fdaa6ae1a3ca84c2855806728693e8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chainlink-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
