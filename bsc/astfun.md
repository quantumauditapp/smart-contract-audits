---
token: ast.fun
ticker: AST
network: bsc
risk_score: 29
status: low
date: 2026-08-31
---

# ast.fun (AST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/astfun-bsc)

---

## Audit Summary

The FourERC20 contract implements a custom ERC-20 token. While it adopts a structure similar to OpenZeppelin's ERC-20, critical vulnerabilities related to integer overflows in `unchecked` arithmetic operations for token balances and total supply were identified. Additionally, the contract lacks proper initialization mechanisms and access control for minting and burning, rendering it largely unusable as a standalone token upon direct deployment. These issues pose significant risks to the token's integrity and functionality.

> **Final Recommendation:** It is strongly recommended to address the critical integer overflow vulnerabilities by either removing the `unchecked` blocks for additions or implementing explicit overflow checks. The contract also requires a public constructor to properly initialize the token's name, symbol, and initial supply, along with well-defined access control mechanisms (e.g., using OpenZeppelin's `Ownable` or `AccessControl`) for `_mint` and `_burn` functions to enable token supply management. Without these fundamental changes, the token is not suitable for production deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract implements a standard ERC-20 interface, leveraging OpenZeppelin's `Context` and interface definitions, which provides a familiar structure (7.1 Architecture). It includes common ERC-20… |
| **Governance / Economics** | 6/10 | Medium | The contract is a basic ERC-20 token and does not introduce complex governance or economic models, simplifying its risk profile in these areas (7.5 Governance). Its design adheres to the fundamental… |
| **Upgrades** | 4/10 | Medium | The contract is a standard, non-upgradeable implementation, which eliminates the complexities and specific vulnerabilities associated with proxy patterns (7.7 Upgrades). This design choice ensures… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unchecked Addition Overflows in Token Balances and Total Supply  *(Severity: Critical · Status: Unresolved)*

The `_balances[to] += amount;` operation in `_transfer`, `_balances[account] += amount;` in `_mint`, and `_totalSupply += amount;` in `_mint` are all enclosed within `unchecked` blocks. These additions lack overflow protection, meaning if the sum exceeds `type(uint256).max`, the value will wrap around to zero. This can lead to incorrect token balances, an inaccurate total supply, and potential loss of funds or manipulation of the token's economic model (7.2 Code Security).

**Recommendation:** Remove the `unchecked` blocks around addition operations for `_balances` and `_totalSupply`. In Solidity 0.8+, arithmetic operations are checked by default, which will cause a revert on overflow, preventing this vulnerability. Alternatively, implement explicit overflow checks before performing the addition within the `unchecked` block.


### `H-01` — Unchecked Subtraction Underflow in `_burn` for Total Supply  *(Severity: High · Status: Unresolved)*

The `_totalSupply -= amount;` operation in the `_burn` function is within an `unchecked` block. While the `_balances[account] = accountBalance - amount;` operation is protected by a `require(accountBalance >= amount)` statement, `_totalSupply` itself is not explicitly checked against `amount`. If `_totalSupply` has been corrupted (e.g., by a prior overflow in `_mint`) or is otherwise less than `amount`, this operation will underflow, leading to an incorrect and potentially manipulable total supply (7.2 Code Security, 7.4 Economic).

**Recommendation:** Ensure that `_totalSupply` is always greater than or equal to `amount` before performing the subtraction. This can be done by adding a `require(_totalSupply >= amount, 'ERC20: burn amount exceeds total supply');` check, or by removing the `unchecked` block, allowing default Solidity 0.8+ checks to handle underflow.


### `H-02` — Missing Initialization and Access Control for Token Management  *(Severity: High · Status: Unresolved)*

The `_init`, `_mint`, and `_burn` functions are declared `internal virtual`, but the contract does not provide any public or external functions to call them or manage associated roles (e.g., a minter role). If `FourERC20` is deployed directly, it cannot be initialized with a name, symbol, or initial supply, and its supply cannot be managed (minted or burned). This renders the token unusable as a standalone ERC-20 contract, as its supply is effectively fixed at zero and unchangeable (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a public constructor that calls `_init` and performs an initial mint to a designated address. Additionally, introduce access control mechanisms (e.g., `Ownable` or `AccessControl` from OpenZeppelin) to expose `mint` and `burn` functions externally, allowing authorized entities to manage the token supply.


### `L-01` — Lack of Public Constructor for Direct Deployment  *(Severity: Low · Status: Unresolved)*

The contract lacks a public constructor to call the `_init` function or perform initial minting. While `_init` is internal, without a constructor to invoke it, the token's name, symbol, and initial supply cannot be set upon deployment. This reinforces the `H-02` issue, making direct deployment of `FourERC20` impractical for creating a functional token (7.8 Operations).

**Recommendation:** Add a public constructor to the `FourERC20` contract that takes `name_` and `symbol_` as arguments and calls `_init(name_, symbol_)`. Consider also adding an `initialSupply` parameter to the constructor to mint tokens to the deployer or a specified address upon deployment.


### `I-01` — Inconsistent Use of `unchecked` Blocks  *(Severity: Informational · Status: Unresolved)*

The contract uses `unchecked` blocks for certain subtractions (e.g., in `decreaseAllowance`, `_spendAllowance`, `_burn`) where `require` statements already prevent underflow. However, other additions (e.g., `allowance(owner, spender) + addedValue` in `increaseAllowance`) are not in `unchecked` blocks, relying on default Solidity 0.8+ checks. While the current usage for subtractions is safe due to preceding checks, the inconsistency in applying `unchecked` blocks without clear documentation can reduce code readability and maintainability (7.2 Code Security).

**Recommendation:** Review all arithmetic operations. For operations where `unchecked` is used, provide clear comments explaining the rationale and the guarantee that prevents overflow/underflow. For operations where default checks are sufficient, ensure consistency. Consider removing `unchecked` blocks where default checks are desired and `require` statements already provide safety.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x265b...ffff`](https://bscscan.com/address/0x265b3982ea730748100947f52561a4eab54affff) |
| **Network** | BNB Chain |
| **Price** | $0.000982 |
| **24h Volume** | $660.1K |
| **Liquidity** | $122.7K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | 21.9% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 4640 buys / 3338 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf49d9c79a07922d3846c762c73b4df65205ef772)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/astfun-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
