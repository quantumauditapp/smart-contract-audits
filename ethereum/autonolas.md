---
token: Autonolas
ticker: OLAS
network: ethereum
risk_score: 76
status: critical
date: 2026-08-14
---

# Autonolas (OLAS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 76/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/autonolas-eth)

---

## Audit Summary

The OLAS token contract is an ERC20 implementation with custom minting and inflation control. It features a centralized owner and minter role. Key technical issues include an underflow vulnerability in `decreaseAllowance`, a potential long-term denial-of-service in the `inflationRemainder` function due to an unbounded loop, and an overflow vulnerability in `increaseAllowance`. The contract's economic model relies on a centralized minting authority and a specific inflation schedule.

> **Final Recommendation:** Address the critical underflow vulnerability in `decreaseAllowance` by adding a proper check to ensure `spenderAllowance >= amount` before subtraction. Mitigate the potential denial-of-service in `inflationRemainder` by either capping the loop iterations or redesigning the calculation to avoid a linear loop over time, ensuring long-term usability of the minting function. Consider implementing a multi-signature wallet for the `owner` and `minter` roles to decentralize control and reduce single points of failure. Educate users to exclusively use `increaseAllowance` and `decreaseAllowance` to avoid the standard ERC20 `approve` race condition.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes Solmate's ERC20 implementation, generally known for its efficiency and security (7.2 Code Security). However, custom implementations for `decreaseAllowance` and… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with a single `owner` address controlling the ability to change the `minter` and the `minter` having sole authority to mint new tokens (7.3… |
| **Upgrades** | 3/10 | High | The contract is not designed to be upgradeable (7.7 Upgrades). It is a standard, non-proxy ERC20 implementation, meaning its logic is immutable once deployed. This eliminates upgrade-related risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Underflow Vulnerability in `decreaseAllowance`  *(Severity: Critical · Status: Unresolved)*

The `decreaseAllowance` function does not check if `spenderAllowance` is greater than or equal to `amount` before performing the subtraction `spenderAllowance -= amount;`. If `amount` is greater than the current `spenderAllowance`, the subtraction will result in an underflow, causing `spenderAllowance` to wrap around to a very large value (e.g., `type(uint256).max - (amount - spenderAllowance)`). This allows a malicious user or an attacker to effectively grant themselves an arbitrarily large allowance by calling `decreaseAllowance` with an `amount` larger than the current allowance.

**Recommendation:** Add a require statement to ensure `spenderAllowance >= amount` before performing the subtraction. Alternatively, use OpenZeppelin's `SafeMath` or Solidity 0.8+ default checked arithmetic, but explicitly ensure the condition is met for `decreaseAllowance`'s logic.


### `H-01` — Centralized Control of Token Minting and Ownership  *(Severity: High · Status: Unresolved)*

The contract design grants significant centralized control to the `owner` and `minter` addresses. The `owner` can change both the `owner` and `minter` roles, and the `minter` has the sole authority to mint new tokens, subject only to the internal inflation control mechanism. This creates a single point of failure and a high trust assumption in these privileged addresses. A compromise of the `owner` or `minter` private key could lead to unauthorized token minting or loss of control over the contract.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` and `minter` roles to distribute control and reduce the risk associated with a single compromised key. For future iterations, explore decentralized governance mechanisms for critical functions like changing roles or adjusting inflation parameters.


### `H-02` — Potential Denial-of-Service in `inflationRemainder` Due to Unbounded Loop  *(Severity: High · Status: Unresolved)*

The `inflationRemainder` function contains a `for` loop that iterates `numYears - 9` times if `numYears` is greater than 9. The `numYears` variable is derived from `(block.timestamp - timeLaunch) / oneYear`, meaning it will continuously increase as time passes. If the contract remains active for many decades or centuries, `numYears` could become very large, causing the loop to consume an excessive amount of gas. This could eventually lead to the `mint` function (which calls `inflationControl`, which in turn calls `inflationRemainder`) exceeding the block gas limit, rendering minting operations permanently unusable.

**Recommendation:** Redesign the `inflationRemainder` calculation to avoid a linear loop over time. This can be achieved by using a closed-form mathematical formula for compound interest or by capping the maximum number of iterations for the loop. For example, pre-calculate the `supplyCap` for a very distant future year and use that as a maximum, or implement a more efficient logarithmic calculation if possible.


### `M-01` — Overflow Vulnerability in `increaseAllowance`  *(Severity: Medium · Status: Unresolved)*

The `increaseAllowance` function performs `spenderAllowance += amount;` without checking for potential overflow. If the sum of `spenderAllowance` and `amount` exceeds `type(uint256).max`, the value will wrap around to a very small number (close to zero). While less critical than an underflow, this unexpected behavior could lead to an allowance being set much lower than intended, causing operational issues for users or integrated protocols.

**Recommendation:** While Solidity 0.8+ provides default checked arithmetic, it's good practice to be explicit about expected behavior. Ensure that the sum `spenderAllowance + amount` does not exceed `type(uint256).max`. If `spenderAllowance` is already `type(uint256).max`, the function should ideally revert or simply return true without modification, as it cannot be increased further.


### `L-01` — Standard ERC20 `approve` Race Condition Still Present  *(Severity: Low · Status: Unresolved)*

While the contract provides `increaseAllowance` and `decreaseAllowance` functions to mitigate the known ERC20 `approve` race condition, the standard `approve` function inherited from Solmate's ERC20 is still available. Users who are unaware of the race condition or the safer alternatives might still use `approve`, potentially exposing themselves to front-running attacks where an attacker can exploit a pending `approve` transaction to drain funds.

**Recommendation:** Strongly advise users to exclusively use `increaseAllowance` and `decreaseAllowance` instead of `approve`. Consider adding a comment in the contract or documentation to highlight this. While not strictly a contract vulnerability, it's a common user-side security concern that can be mitigated by clear guidance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0001...5cb0`](https://etherscan.io/address/0x0001a500a6b18995b03f44bb040a5ffc28e45cb0) |
| **Network** | Ethereum |
| **Price** | $0.01917 |
| **24h Volume** | $365.0K |
| **Liquidity** | $1.02M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 3y |
| **Top-10 Holders** | 75.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 199 buys / 112 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x09d1d767edf8fa23a64c51fa559e0688e526812f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/autonolas-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
