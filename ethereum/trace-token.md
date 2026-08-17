---
token: Trace Token
ticker: TRAC
network: ethereum
risk_score: 69
status: high
date: 2026-08-17
---

# Trace Token (TRAC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trace-token-eth)

---

## Audit Summary

The TracToken contract is an ERC-20 compliant token with minting and vesting functionalities. While it incorporates SafeMath for arithmetic safety and includes mechanisms to prevent the ERC20 approve race condition, it operates on an outdated Solidity compiler version. A critical vulnerability exists where the contract owner can mint an unlimited supply of tokens, exceeding the stated TOTAL_NUM_TOKENS, which severely impacts tokenomics. Additionally, the owner retains significant control over token supply and transferability, posing a high centralization risk. Vesting schedules rely on block timestamps and are dependent on the owner enabling transfers, introducing potential delays for beneficiaries.

> **Final Recommendation:** It is strongly recommended to address the critical vulnerability allowing unlimited token minting by implementing a hard cap check within the `mint` function. Review and reduce the extensive centralization of control by considering multi-signature wallets for critical operations or implementing time-locks where appropriate. Update the contract to a modern Solidity compiler version (e.g., 0.8.x) to benefit from security enhancements and gas optimizations. Evaluate the vesting logic to ensure it aligns with economic expectations, particularly regarding the dependency on the `mintingFinished` flag.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes the SafeMath library, which is a strong practice for preventing integer overflows/underflows (7.2 Code Security). However, the `SafeMath.div` function lacks a division-by-zero… |
| **Governance / Economics** | 1/10 | High | The contract exhibits high centralization, with the `owner` having extensive control over token minting, transferability, and allocation (7.3 Access Control). A critical economic vulnerability allows… |
| **Upgrades** | 2/10 | High | The TracToken contract is not designed with upgradeability in mind (7.1 Architecture). It does not implement any proxy patterns (e.g., UUPS, Transparent) or other mechanisms for future upgrades.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `C-01` — Owner Can Mint Tokens Beyond `TOTAL_NUM_TOKENS` Limit  *(Severity: Critical · Status: Unresolved)*

The `MintableToken.mint` function, which is called by `TracToken.mint`, does not include a check to ensure that the `totalSupply` does not exceed the `TOTAL_NUM_TOKENS` constant defined in `TracToken`. While `allocateRestOfTokens` has a `require(totalSupply < TOTAL_NUM_TOKENS)` check, this only applies before that specific function call. The owner can directly call `mint` multiple times, or after `allocateRestOfTokens`, to inflate the total supply beyond the intended maximum, severely devaluing existing tokens.

**Recommendation:** Implement a `require(totalSupply.add(_amount) <= TOTAL_NUM_TOKENS)` check within the `mint` function to enforce the maximum token supply. This check should be present in the `MintableToken.mint` function or the overridden `TracToken.mint` function.


### `H-01` — High Centralization of Control  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants the `owner` address extensive control over critical functions, including `mint`, `finishMinting` (which enables transfers), `endMinting`, `allocateRestOfTokens`, and `transferOwnership`. This creates a single point of failure; if the owner's private key is compromised, an attacker could mint unlimited tokens, prevent transfers, or transfer ownership to themselves, leading to a complete loss of control and trust in the token.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` address to distribute control among multiple trusted parties. For highly sensitive operations like `mint` or `finishMinting`, consider adding time-locks or a decentralized governance mechanism if feasible.


### `M-01` — Vesting Functions Dependent on `mintingFinished` Flag  *(Severity: Medium · Status: Unresolved)*

The `withdrawTokenToFounders` and `withdrawTokensToAdvisors` functions use `this.transfer`, which internally calls `TracToken.transfer`. Both `TracToken.transfer` and `TracToken.transferFrom` are guarded by the `canTransfer` modifier, which requires `mintingFinished` to be true. This means that founders and advisors cannot withdraw their vested tokens until the contract owner calls `finishMinting()` or `endMinting()`. An malicious or inactive owner could indefinitely delay these withdrawals, causing economic harm to beneficiaries.

**Recommendation:** Re-evaluate the design of the vesting functions. If the intention is for vesting to occur independently of general token transferability, consider modifying `withdrawTokenToFounders` and `withdrawTokensToAdvisors` to directly update balances without calling the restricted `transfer` function, or ensure the `canTransfer` modifier is not applied to internal `this.transfer` calls within these specific vesting functions.


### `M-02` — Use of `block.timestamp` for Vesting Schedules  *(Severity: Medium · Status: Unresolved)*

The `withdrawTokenToFounders` and `withdrawTokensToAdvisors` functions use `now` (an alias for `block.timestamp`) to determine if vesting periods have passed. While common, `block.timestamp` can be manipulated by miners within a certain range (up to 900 seconds on Ethereum). This could allow a miner to slightly accelerate or delay vesting withdrawals, though the impact on long-term vesting schedules is typically minor.

**Recommendation:** For critical time-sensitive operations, consider using an oracle for time if precise, unmanipulable time is required. For vesting schedules, `block.timestamp` is generally acceptable given the long durations, but users should be aware of this minor manipulation potential.


### `L-01` — Outdated Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract is compiled with `pragma solidity ^0.4.18`. This version is significantly outdated. Newer Solidity versions (e.g., 0.8.x) include numerous security enhancements, bug fixes, and gas optimizations. Using an older compiler version may expose the contract to known compiler-related vulnerabilities or lead to less efficient code.

**Recommendation:** Consider migrating the contract to a modern Solidity compiler version (e.g., 0.8.x). This would require thorough re-auditing and testing due to breaking changes between versions, but would significantly improve the contract's security posture and efficiency.


### `L-02` — Redundant `Transfer` Event Declaration  *(Severity: Low · Status: Unresolved)*

The `TracToken` contract re-declares the `Transfer` event (`event Transfer(address indexed from, address indexed to, uint256 value);`) which is already declared in `ERC20Basic`. While not a functional vulnerability, this is redundant and can lead to minor confusion or slight gas inefficiency if the compiler processes it multiple times.

**Recommendation:** Remove the redundant `Transfer` event declaration from the `TracToken` contract. The event declared in `ERC20Basic` is sufficient and will be inherited and emitted correctly.


### `I-01` — `SafeMath.div` Lacks Division-by-Zero Check  *(Severity: Informational · Status: Unresolved)*

The `SafeMath.div` function is implemented as `uint256 c = a / b; return c;`. It does not explicitly check if the divisor `b` is zero before performing the division. While Solidity's built-in division operation would revert on division by zero, an explicit `require(b != 0)` check is a best practice for clarity and consistency in a SafeMath library.

**Recommendation:** Add a `require(b != 0, "SafeMath: division by zero")` check at the beginning of the `div` function in the `SafeMath` library.


### `I-02` — `approve` Function's Anti-Race Condition Assertion  *(Severity: Informational · Status: Unresolved)*

The `approve` function in `StandardToken` includes an assertion: `assert(allowed[msg.sender][_spender] == 0 \|\| _value == 0);`. This assertion prevents the known ERC20 `approve` race condition where a user might approve a new amount before the spender has spent the old amount, potentially allowing the spender to spend both amounts. This is a positive security measure, although it forces users to set allowance to 0 first before increasing it, which can be inconvenient. The `increaseApproval` and `decreaseApproval` functions are provided as safer alternatives.

**Recommendation:** No direct recommendation for change, as this is a deliberate security choice. Users should be educated to use `increaseApproval` and `decreaseApproval` for modifying allowances to avoid the `approve` race condition and the inconvenience of setting allowance to zero first.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaa7a...0a6f`](https://etherscan.io/address/0xaa7a9ca87d3694b5755f213b5d04094b8d0f0a6f) |
| **Network** | Ethereum |
| **Price** | $0.2618 |
| **24h Volume** | $84.1K |
| **Liquidity** | $349.8K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 51.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 84 buys / 79 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xb1914469141ebb6e244e75cee3f35d43bf6b85e5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trace-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
