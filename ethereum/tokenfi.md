---
token: TokenFi
ticker: TOKEN
network: ethereum
risk_score: 61
status: medium
date: 2026-08-30
---

# TokenFi (TOKEN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tokenfi-eth)

---

## Audit Summary

The T1 token contract implements ERC-20 and governance delegation features. A critical vulnerability was identified where the core `_transfer` function is missing, rendering the token non-functional for transfers. Additionally, the ERC-20 withdrawal mechanism is flawed, and a potential truncation issue exists in the governance delegation logic. The contract relies on an `Ownable` pattern, centralizing control over key parameters and fund withdrawals.

> **Final Recommendation:** Address the critical functional bugs immediately, particularly the missing `_transfer` function and the incorrect ERC20 `withdraw` logic. Thoroughly review the governance delegation mechanism to prevent `uint224` truncation and ensure accurate voting power representation. Consider implementing a multi-signature wallet for the owner address to mitigate centralized control risks and enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation attempts to combine ERC-20 functionality with governance delegation. Strengths include the use of OpenZeppelin's Ownable for access control and EIP-712 for… |
| **Governance / Economics** | 4/10 | Medium | The contract incorporates a standard governance delegation mechanism, allowing token holders to delegate their voting power and retrieve historical vote counts (7.5 Governance). This promotes… |
| **Upgrades** | 7/10 | Low | The T1 contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, no upgrade-specific risks are present. Any changes to the contract's logic would require a new deployment and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 90.5% — Null Address, OnlyMoons Lock |
| **Top-1 Unlocked Holder** | 9.4% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Missing `_transfer` Function Renders Token Non-Functional  *(Severity: Critical · Status: Unresolved)*

The `transfer` and `transferFrom` functions, which are core to ERC-20 functionality, both call an internal `_transfer` function. However, the provided contract code for `T1` does not define a `_transfer` function. This critical omission means that token transfers will always revert, making the token completely non-functional as an ERC-20 asset.

**Recommendation:** Implement the `_transfer` function, which should handle the logic for updating `_balances` and emitting the `Transfer` event, similar to standard ERC-20 implementations. Ensure it includes necessary checks for sender/recipient validity and sufficient balance.


### `H-01` — Incorrect ERC20 Withdrawal Logic in `withdraw` Function  *(Severity: High · Status: Unresolved)*

The `withdraw` function, when handling ERC20 tokens, uses `IERC20(tokenAddress).transferFrom(address(this), address(treasuryHandler), amount);`. For `transferFrom` to succeed, the `T1` contract itself (as `address(this)`) would need to have approved itself to spend `tokenAddress` tokens, which is an incorrect and non-standard pattern. Typically, a contract holding ERC20 tokens would use `IERC20(tokenAddress).transfer(address(treasuryHandler), amount);` to send tokens it owns. As implemented, the ERC20 withdrawal functionality is non-functional.

**Recommendation:** Change the ERC20 withdrawal logic to `IERC20(tokenAddress).transfer(address(treasuryHandler), amount);` to correctly transfer tokens held by the contract to the treasury handler. Ensure the contract actually holds the tokens it intends to withdraw.


### `H-02` — Potential `uint224` Truncation in `_moveDelegates`  *(Severity: High · Status: Unresolved)*

In the `_delegate` function, `delegatorBalance` (a `uint256`) is cast to `uint224` before being passed as `amount` to `_moveDelegates`. If a delegator's balance exceeds `type(uint224).max` (approximately 2^224 - 1), the `amount` will be truncated. This truncation would lead to an incorrect representation of voting power for delegates, potentially undermining the integrity of the governance mechanism.

**Recommendation:** Consider using `uint256` for `amount` in `_moveDelegates` and for `votes` in the `Checkpoint` struct to ensure that all possible token balances can be accurately represented as voting power. If `uint224` is strictly required for gas optimization or storage, implement a `require` check to prevent delegation of amounts exceeding `type(uint224).max`.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract utilizes the `Ownable` pattern, granting the deployer (owner) exclusive control over critical functions. The owner can unilaterally change the `taxHandler` and `treasuryHandler` addresses, and has the ability to withdraw any ETH or ERC20 tokens from the contract via the `withdraw` function. This centralization introduces a single point of failure and relies heavily on the trustworthiness of the owner.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to distribute control and require multiple approvals for sensitive operations. Alternatively, introduce a timelock mechanism for critical changes (e.g., changing handlers) to provide a window for community review or intervention.


### `M-02` — Incomplete Code Snippet  *(Severity: Medium · Status: Unresolved)*

The contract code ends abruptly with `emit DelegateVotesCh...`, indicating that the provided source code is incomplete or truncated. This suggests potential issues with the development process, code quality, or a copy-paste error, and raises concerns about the full functionality and security of the missing parts.

**Recommendation:** Provide the complete and correct source code for the contract. Ensure all events are properly emitted and all functions are fully implemented as intended.


### `L-01` — `numCheckpoints` `uint32` Overflow Possibility  *(Severity: Low · Status: Unresolved)*

The `numCheckpoints` variable, which tracks the number of checkpoints for a delegatee, is a `uint32`. In the `_writeCheckpoint` function, `numCheckpoints[delegatee]` is incremented. While highly unlikely in practical scenarios, if a delegatee accumulates `2^32 - 1` (approx. 4.2 billion) checkpoints, the next increment would cause an overflow, potentially leading to incorrect checkpoint indexing or state corruption.

**Recommendation:** While the likelihood is extremely low, consider adding a `require` check before incrementing `numCheckpoints` to ensure it does not exceed `type(uint32).max`. Alternatively, if the number of checkpoints is expected to be very large, use `uint256` for `numCheckpoints`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4507...b528`](https://etherscan.io/address/0x4507cef57c46789ef8d1a19ea45f4216bae2b528) |
| **Network** | Ethereum |
| **Price** | $0.002289 |
| **24h Volume** | $26.4K |
| **Liquidity** | $1.11M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 78.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 293 buys / 294 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc7e6b676bfc73ae40bcc4577f22aab1682c691c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tokenfi-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
