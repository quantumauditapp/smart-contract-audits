---
token: Gnosis Token
ticker: GNO
network: ethereum
risk_score: 55
status: high
date: 2026-08-16
---

# Gnosis Token (GNO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gnosis-token-eth)

---

## Audit Summary

The GnosisToken contract, an ERC-20 compliant token, was audited for security vulnerabilities. The contract exhibits several issues related to its use of an older Solidity compiler version (0.4.10), including the `throw` keyword for error handling and susceptibility to the ERC-20 `approve` race condition. While core token functionalities are present, adherence to modern security practices is lacking, contributing to a Medium overall risk level.

> **Final Recommendation:** It is strongly recommended to migrate to a newer Solidity compiler version (0.8.x) and adopt modern best practices, including the use of `require()`/`revert()` for error handling and SafeMath for all arithmetic operations to prevent potential overflows. Implement a robust solution for the ERC-20 `approve` race condition, such as the `increaseAllowance`/`decreaseAllowance` pattern, to enhance security and user experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The GnosisToken contract implements a standard ERC-20 token with a fixed supply and initial distribution logic (7.1 Architecture). The core `transfer` and `transferFrom` functions include checks to… |
| **Governance / Economics** | 1/10 | High | The token's economic model is straightforward, with a fixed total supply and initial distribution defined in the constructor (7.4 Economic). There are no complex governance mechanisms or external… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism, meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks but also prevents future bug fixes or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.5% |
| **Top-3 Unlocked** | ⚠️ 98.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 2 Informational_

### `H-01` — Deprecated `throw` Keyword for Error Handling  *(Severity: High · Status: Unresolved)*

The contract uses the `throw` keyword for error handling, which is deprecated since Solidity 0.4.22. `throw` consumes all remaining gas, making it less gas-efficient than `revert()` or `require()`, which were introduced later and allow for more precise error messages and gas refunds. This can lead to higher transaction costs for failed operations.

**Recommendation:** Update the contract to use `require()` or `revert()` statements for error handling. This improves gas efficiency and allows for clearer error messages, aligning with modern Solidity best practices.


### `H-02` — ERC-20 `approve` Race Condition Vulnerability  *(Severity: High · Status: Unresolved)*

The `approve` function is susceptible to a known ERC-20 race condition. If a user calls `approve(spender, newAmount)` while the `spender` is simultaneously trying to spend the `oldAmount`, the `spender` might be able to spend both `oldAmount` and `newAmount`, effectively doubling the allowance. This can lead to unintended token transfers.

**Recommendation:** Implement the `increaseAllowance` and `decreaseAllowance` pattern, as recommended by OpenZeppelin, to safely modify allowances. This pattern prevents the race condition by requiring explicit increments or decrements, ensuring atomic updates.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version 0.4.10. This version is significantly outdated and lacks numerous security features, bug fixes, and optimizations introduced in later versions (e.g., 0.5.x, 0.6.x, 0.8.x). Using an old compiler increases the risk of undiscovered compiler bugs or missing modern security patterns.

**Recommendation:** Upgrade the contract to a recent and stable Solidity compiler version (e.g., 0.8.x). This would allow leveraging modern language features, improved security checks (like built-in overflow/underflow checks for `uint` types), and better gas optimization.


### `M-02` — Potential Integer Overflow on Addition  *(Severity: Medium · Status: Unresolved)*

The contract performs addition operations (e.g., `balances[_to] += _value` in `transfer` and `transferFrom`, `assignedTokens += tokens[i]` in the constructor) without explicit overflow checks. While `uint256` provides a large range, a malicious or accidental input exceeding `type(uint256).max` could lead to an overflow, resulting in incorrect balance calculations.

**Recommendation:** Implement SafeMath or similar libraries for all arithmetic operations to prevent integer overflows. Modern Solidity versions (0.8.0+) include built-in overflow/underflow checks for `uint` types, which would mitigate this risk if the compiler is updated.


### `I-01` — Constructor Gas Limit Risk for Large Arrays  *(Severity: Informational · Status: Unresolved)*

The `GnosisToken` constructor iterates through `owners` and `tokens` arrays to assign initial balances. If these arrays are excessively large, the constructor's gas consumption could exceed the block gas limit, preventing the contract from being deployed successfully.

**Recommendation:** For very large initial distributions, consider an alternative mechanism such as a separate function for claiming tokens or a batched distribution function that can be called multiple times post-deployment to avoid hitting block gas limits.


### `I-02` — `totalSupply()` Signature Mismatch in Interface  *(Severity: Informational · Status: Unresolved)*

The `Token` interface declares `totalSupply() constant returns (uint256 supply) {}` with an empty body and `constant` keyword. While `StandardToken` correctly implements `totalSupply` as a public state variable, the interface definition is slightly inconsistent with modern ERC-20 interfaces which typically declare `function totalSupply() external view returns (uint256);`. The `constant` keyword for functions was deprecated in 0.5.0.

**Recommendation:** While not a functional bug in `StandardToken`, for future compatibility and clarity, the `Token` interface could be updated to reflect modern ERC-20 standards, using `view` instead of `constant` and removing the empty function body.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6810...6b96`](https://etherscan.io/address/0x6810e776880c02933d47db1b9fc05908e5386b96) |
| **Network** | Ethereum |
| **Price** | $103.4700 |
| **24h Volume** | $35.4K |
| **Liquidity** | $103.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 96.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 58 buys / 69 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa46466ad5507be77ff5abdc27df9dfeda9bd7aee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gnosis-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
