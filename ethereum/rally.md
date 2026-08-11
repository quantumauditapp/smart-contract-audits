---
token: Rally
ticker: RALLY
network: ethereum
risk_score: 75
status: critical
date: 2026-08-11
---

# Rally (RALLY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 75/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rally-eth)

---

## Audit Summary

The audit of the Token contract identified several areas for improvement, primarily concerning ERC-20 standard compliance and centralization risks. A critical issue is the missing implementation of the `totalSupply()` function, which is essential for ERC-20 compatibility. High centralization of control through the owner and issuer roles presents significant economic risk. Additionally, certain administrative functions carry risks of accidental role locking or irreversible actions. The contract demonstrates good practices in preventing common integer overflows/underflows and includes necessary address checks.

> **Final Recommendation:** It is strongly recommended to implement the missing `totalSupply()` function to ensure full ERC-20 compatibility. Review the centralization model and consider implementing multi-signature control for critical roles like `owner` and `issuer` to mitigate single points of failure. Implement safeguards in `transferOwnership` to prevent setting `pendingOwner` to `address(0)` and consider adding a mechanism to revert `setIssuer` if it's set to `address(0)` or if minting is intended to be temporarily paused.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract exhibits a generally sound technical foundation, utilizing `unchecked` blocks correctly with preceding `require` statements to prevent integer overflows (7.2 Code Security). Necessary… |
| **Governance / Economics** | 2/10 | High | The contract design incorporates a highly centralized governance model, where an `owner` can control the `issuer` role, and the `issuer` can mint tokens up to `maxSupply` (7.5 Governance, 7.4… |
| **Upgrades** | 2/10 | High | This contract is not designed to be upgradeable, as it does not implement any proxy pattern (7.7 Upgrades). Therefore, there are no upgrade-related risks to assess. Any changes to the contract's… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 16.5% |
| **Top-3 Unlocked** | 45.7% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing `totalSupply()` Function Implementation  *(Severity: Critical · Status: Unresolved)*

The contract declares `IERC20` but does not implement the `totalSupply()` function as required by the ERC-20 standard. While a public `totalSupply` state variable exists, many dApps and tools rely on the explicit function call for compatibility. This omission can lead to integration issues and unexpected behavior with external systems expecting a standard ERC-20 token.

**Recommendation:** Implement the `totalSupply()` function to return the value of the `totalSupply` state variable, ensuring full ERC-20 compliance. Example: `function totalSupply() external view override returns (uint) { return totalSupply; }`


### `H-01` — High Centralization Risk  *(Severity: High · Status: Unresolved)*

The `owner` and `issuer` roles possess significant power. The `owner` can change the `issuer`, and the `issuer` has the ability to `mint` new tokens up to the `maxSupply`. This centralized control means that a compromise of the `owner` or `issuer`'s private key could lead to unauthorized token minting, market manipulation, or a complete loss of trust in the token's supply integrity.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` and `issuer` roles to distribute control and reduce the risk associated with a single point of failure. Explore time-locks or governance mechanisms for critical actions like changing the issuer or minting large amounts of tokens.


### `M-01` — Ownership Transfer to `address(0)` Possible  *(Severity: Medium · Status: Unresolved)*

The `transferOwnership` function allows the current `owner` to set `pendingOwner` to `address(0)`. If this occurs, the `confirmOwnership` function, which requires `msg.sender == pendingOwner`, can never be called, effectively locking the ownership transfer mechanism. The current `owner` would remain the owner indefinitely, unable to transfer ownership to a new, valid address.

**Recommendation:** Add a `require` statement in `transferOwnership` to prevent setting `newOwner` to `address(0)`. For example: `require(newOwner != address(0), 'New owner cannot be the zero address');`


### `M-02` — `setIssuer` to `address(0)` Disables Minting  *(Severity: Medium · Status: Unresolved)*

The `setIssuer` function allows the `owner` to set the `issuer` address to `address(0)`. If `issuer` is set to `address(0)`, the `mint` function becomes permanently unusable because the `only(issuer)` modifier will always fail. While the `owner` can later set a new valid issuer, this action could temporarily halt token issuance and might be an unintended consequence if not carefully managed.

**Recommendation:** Consider adding a `require` statement in `setIssuer` to prevent setting `newIssuer` to `address(0)` unless this is an explicit, intended mechanism to permanently disable minting. If temporary disablement is desired, implement a separate pause/unpause mechanism for minting.


### `L-01` — Standard ERC-20 `approve` Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

The `approve` function, as implemented, is susceptible to a known ERC-20 front-running vulnerability. If a user approves an amount for a spender and then attempts to change that approved amount to a different value (especially a lower one), an attacker can front-run the second transaction. The attacker could spend the original approved amount before the new allowance is set, potentially leading to a double-spend of the allowance.

**Recommendation:** While this is a common ERC-20 limitation, consider using `increaseAllowance` and `decreaseAllowance` functions (as seen in OpenZeppelin's ERC-20 implementation) instead of directly setting the allowance. This pattern mitigates the front-running risk by requiring explicit increments or decrements.


### `I-01` — Use of `unchecked` Blocks  *(Severity: Informational · Status: Unresolved)*

The contract utilizes `unchecked` blocks for arithmetic operations in functions like `mint`, `transferFrom`, and `updateBalance`. These blocks are correctly preceded by `require` statements (e.g., `require(totalSupply + value <= maxSupply)` or `require(balanceOf[from] >= value)`) that ensure the operations will not overflow or underflow. This is a valid optimization in Solidity 0.8.x to save gas by explicitly opting out of default overflow/underflow checks.

**Recommendation:** No direct action is required as the `unchecked` blocks are used safely. However, it is crucial to maintain rigorous testing and review of any changes to these functions to ensure that the preceding `require` statements always provide adequate protection against arithmetic overflows/underflows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1964...d08c`](https://etherscan.io/address/0x19640000000ba88d36206beb10d0e86011c8d08c) |
| **Network** | Ethereum |
| **Price** | $0.03519 |
| **24h Volume** | $526.7K |
| **Liquidity** | $5.45M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 35.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 146 buys / 162 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd6951c4cf75cba4b29efb80c0a53cb9d61abc8f07d2120d2b6138d8b8e7a6a20)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rally-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
