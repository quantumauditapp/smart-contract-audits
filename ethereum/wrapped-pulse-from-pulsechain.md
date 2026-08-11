---
token: Wrapped Pulse from PulseChain
ticker: WPLS
network: ethereum
risk_score: 61
status: high
date: 2026-08-11
---

# Wrapped Pulse from PulseChain (WPLS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 61/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-pulse-from-pulsechain-eth)

---

## Audit Summary

This report details the security audit of an ERC20 token contract and associated libraries. The provided source code appears to be a collection of standard OpenZeppelin 0.4.x contracts (BasicToken, StandardToken, MintableToken, BurnableToken, Ownable, SafeMath) along with some custom utilities (AddressUtils, SafeERC20, Claimable, Sacrifice). The main token contract, identified as 'PermittableToken' in prefill data, is not fully provided in the source, with 'ERC677BridgeToken' being truncated. The audit focuses on the provided code snippets. Key findings include the use of an outdated Solidity compiler, a potential access control vulnerability in the `Claimable` pattern if not properly protected, and the known ERC20 `approve` race condition.

> **Final Recommendation:** It is strongly recommended to upgrade the Solidity compiler version to a modern, supported release (e.g., 0.8.x) to benefit from recent security patches and language improvements. This would involve a comprehensive review and update of the codebase to align with newer Solidity syntax and best practices. Additionally, ensure that any external functions inheriting the `Claimable` pattern, such as `claimTokens`, are rigorously protected with appropriate access control mechanisms, typically `onlyOwner`, to prevent unauthorized asset withdrawals. Consider implementing a more robust and gas-efficient method for Ether transfers than `selfdestruct` in utility functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture leverages well-established ERC20 patterns and includes `SafeMath` for arithmetic safety (7.1 Architecture, 7.2 Code Security). However, the use of Solidity `^0.4.24` is a… |
| **Governance / Economics** | 5/10 | Medium | The token implements standard `Ownable` access control, ensuring that critical functions like `mint` and `finishMinting` are restricted to the contract owner (7.5 Governance). The economic model… |
| **Upgrades** | 4/10 | Medium | The provided contracts do not implement an explicit upgrade mechanism (7.7 Upgrades). The prefill data indicates the contract is not a proxy. Therefore, upgrade safety issues are not directly… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 30.0% |
| **Top-3 Unlocked** | 77.6% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Outdated Solidity Compiler Version  *(Severity: High · Status: Unresolved)*

The contract uses `pragma solidity ^0.4.24;`. This Solidity version is significantly outdated and is known to have compiler bugs and lacks many security features and optimizations present in newer versions (e.g., 0.8.x). Using an old compiler version increases the risk of undiscovered vulnerabilities or known exploits that have been patched in later versions.

**Recommendation:** Upgrade the Solidity compiler version to a recent, stable release (e.g., `^0.8.0`). This will require a thorough review and adaptation of the code to comply with new syntax and semantics, including changes to `SafeMath` usage (which is often no longer needed in 0.8.x due to default overflow/underflow checks) and `require` statements.


### `H-02` — Potential Access Control Flaw in `Claimable` Pattern  *(Severity: High · Status: Unresolved)*

The `IBurnableMintableERC677Token` interface defines an `external` function `claimTokens(address _token, address _to)`. The `Claimable` contract provides `internal` functions (`claimValues`, `claimNativeCoins`, `claimErc20Tokens`) to facilitate claiming assets. If the main token contract (e.g., `ERC677BridgeToken`) implements `claimTokens` without an `onlyOwner` or similar access control modifier, any user could call this function to drain arbitrary ERC20 tokens or native ETH from the contract's balance to any address.

**Recommendation:** Ensure that any public or external function that calls `claimValues` (or its internal derivatives) is protected by a robust access control mechanism, such as the `onlyOwner` modifier. This prevents unauthorized users from claiming funds held by the contract.


### `M-01` — ERC20 `approve` Race Condition  *(Severity: Medium · Status: Unresolved)*

The `approve` function is susceptible to a known ERC20 race condition. If a user calls `approve(spender, newAmount)` while a `spender` is concurrently trying to spend the `oldAmount`, the `spender` might be able to spend both the `oldAmount` and the `newAmount`, or neither, depending on transaction ordering. While `increaseApproval` and `decreaseApproval` mitigate this, the `approve` function itself remains vulnerable.

**Recommendation:** While `increaseApproval` and `decreaseApproval` are provided, users should be strongly advised to use these functions instead of `approve` when modifying an existing allowance. For new allowances, a zero-value `approve` followed by the desired `approve` value can also mitigate the risk, but this is not enforced by the contract.


### `L-01` — `SafeMath.div` Lacks Division by Zero Check  *(Severity: Low · Status: Unresolved)*

The `div` function in the `SafeMath` library does not explicitly check for division by zero. While Solidity's EVM will revert on division by zero, an explicit `require(_b != 0)` check would provide a clearer error message and prevent unnecessary gas consumption from the implicit revert.

**Recommendation:** Add an explicit `require(_b != 0, "SafeMath: division by zero")` check at the beginning of the `div` function in the `SafeMath` library for improved clarity and user experience.


### `L-02` — Unusual `selfdestruct` for Ether Transfer Fallback  *(Severity: Low · Status: Unresolved)*

The `Address.safeSendValue` library function uses `selfdestruct(_receiver)` as a fallback if `_receiver.send(_value)` fails. While `selfdestruct` can force Ether to a contract, it is an unconventional and potentially gas-inefficient method. It might also lead to unexpected behavior if the recipient contract is not designed to handle Ether received via `selfdestruct`, potentially locking funds if the contract has no `receive` or `fallback` function, or if it has specific logic for `selfdestruct` calls.

**Recommendation:** Consider using a direct `call` with a gas limit as a fallback for `send` if a more robust Ether transfer is required, rather than `selfdestruct`. This provides more control and is generally a more standard approach for handling failed `send` calls.


### `I-01` — Missing `transferAndCall` Implementation  *(Severity: Informational · Status: Unresolved)*

The `ERC677` interface is imported, which includes the `transferAndCall(address, uint256, bytes) external returns (bool)` function. However, the provided code snippets do not include an implementation for this function. If the main token contract intends to be ERC677 compliant, this function would need to be implemented.

**Recommendation:** If ERC677 compliance is desired, implement the `transferAndCall` function. Ensure that its implementation is secure, particularly regarding reentrancy risks if it interacts with the recipient contract's `tokenFallback` function.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa882...d68a`](https://etherscan.io/address/0xa882606494d86804b5514e07e6bd2d6a6ee6d68a) |
| **Network** | Ethereum |
| **Price** | $0.0000101 |
| **24h Volume** | $52.5K |
| **Liquidity** | $92.1K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 3y |
| **Top-10 Holders** | 38.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 106 buys / 63 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x8cd6c8c449918d92d2ad4658c32f2e2ff1e7096d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-pulse-from-pulsechain-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
