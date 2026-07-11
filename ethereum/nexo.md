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

The audit of the NexoToken contract revealed several areas for improvement, primarily concerning inconsistent application of SafeMath, the use of an outdated Solidity compiler, and centralized control by the contract owner. While the contract implements basic ERC-20 functionality and a two-step ownership transfer, critical arithmetic operations bypass SafeMath, posing a risk of integer underflow. The vesting logic, though defined, is incomplete in the provided source, limiting a full assessment.

> **Final Recommendation:** It is strongly recommended to update the Solidity compiler to a more recent, stable version (e.g., 0.8.x) to benefit from modern security features and bug fixes. Crucially, all arithmetic operations involving user balances and allowances must consistently utilize the `SafeMath` library to prevent potential integer underflow vulnerabilities. A thorough review of the owner's privileges and the complete vesting logic is also advised to ensure alignment with the project's security and economic requirements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture (7.1) is a standard ERC-20 token inheriting from `Owned` and `SafeMath`. Code security (7.2) is a primary concern due to inconsistent SafeMath usage in `_transfer` and… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4) involves fixed allocations for investors, overdraft, and team, with defined vesting parameters, though the full vesting implementation is not provided. Governance… |
| **Upgrades** | 4/10 | Medium | The contract is not designed with any upgradeability mechanism (7.7). It is a standard, non-proxy implementation, meaning its logic cannot be modified after deployment. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.0% |
| **Top-3 Unlocked** | ⚠️ 91.5% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Inconsistent SafeMath Usage Leading to Potential Underflow  *(Severity: High · Status: Unresolved)*

The `StandardToken._transfer` function directly uses `balances[_from] -= _value;` and the `StandardToken.transferFrom` function directly uses `allowed[_from][msg.sender] -= _value;` without utilizing the `SafeMath.sub` function. This bypasses the intended underflow protection provided by the `SafeMath` library, making these operations vulnerable to integer underflow if `_value` exceeds the current balance or allowance.

**Recommendation:** Ensure all subtraction operations on `uint256` variables, especially those involving user balances or allowances, consistently use `SafeMath.sub`. For example, change `balances[_from] -= _value;` to `balances[_from] = sub(balances[_from], _value);` and `allowed[_from][msg.sender] -= _value;` to `allowed[_from][msg.sender] = sub(allowed[_from][msg.sender], _value);`.


### `M-01` — Outdated Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract is compiled with Solidity version `0.4.23`. This version is significantly outdated and lacks many security improvements, bug fixes, and best practices introduced in later versions (e.g., 0.5.x, 0.6.x, 0.8.x). Using an old compiler version can expose the contract to known compiler-specific vulnerabilities or less efficient gas usage patterns.

**Recommendation:** Upgrade the Solidity compiler version to a recent, stable release (e.g., `^0.8.0`). This will provide access to modern security features, improved error handling (e.g., `require` for revert reasons), and better gas optimization. Thoroughly test the contract after upgrading the compiler to ensure compatibility and correct behavior.


### `M-02` — Use of `now` for `creationTime`  *(Severity: Medium · Status: Unresolved)*

The `creationTime` variable is set using `now` (an alias for `block.timestamp`). While common, `block.timestamp` can be manipulated by miners within a certain range (up to 900 seconds on Ethereum). If `creationTime` is used in any time-sensitive logic that requires precise, unmanipulable timing, this could be a concern.

**Recommendation:** Evaluate if the `creationTime` variable is used in any critical, time-sensitive operations. If so, consider alternative, more robust time sources or acknowledge the potential for miner manipulation. For simple informational purposes, `block.timestamp` is generally acceptable.


### `L-01` — Missing Division by Zero Check in SafeMath.div  *(Severity: Low · Status: Unresolved)*

The `SafeMath.div` function does not explicitly check if the divisor `b` is zero. While Solidity's default behavior for division by zero is to revert, an explicit `require(b != 0, 'SafeMath: division by zero');` would provide clearer error messaging and adhere to a more robust defensive programming style.

**Recommendation:** Add an explicit check for division by zero at the beginning of the `div` function: `require(b != 0, 'SafeMath: division by zero');`.


### `L-02` — Centralized Control by Owner  *(Severity: Low · Status: Unresolved)*

The `Owned` pattern grants significant control to a single `owner` address. This owner can recover any ERC20 tokens accidentally sent to the contract via `transferERC20Token`. While the `setOwner` and `confirmOwnership` functions provide a two-step transfer mechanism, the owner remains a single point of failure and trust, which could pose a risk if the owner's private key is compromised.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` address to distribute control and reduce the risk associated with a single point of failure. This enhances security by requiring multiple approvals for critical operations.


### `I-01` — Truncated Vesting Logic  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `NexoToken` contract includes definitions for vesting parameters (e.g., `overdraftCliff`, `overdraftPeriodLength`, `teamPeriodAmount`) but the actual functions responsible for implementing the vesting schedule, such as claiming or distributing vested tokens, are truncated or missing from the provided snippet. This prevents a full security assessment of the vesting mechanism.

**Recommendation:** Provide the complete source code for all relevant contracts, especially those implementing critical economic logic like vesting, to enable a comprehensive security review.

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
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-03*
