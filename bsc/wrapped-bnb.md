---
token: Wrapped BNB
ticker: WBNB
network: bsc
risk_score: 66
status: high
date: 2026-07-22
---

# Wrapped BNB (WBNB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-bnb-bsc)

---

## Audit Summary

The WBNB contract functions as a standard Wrapped BNB token, allowing users to deposit BNB to mint WBNB and withdraw WBNB to redeem BNB. The contract is deployed on an older Solidity compiler version (0.4.18), which introduces several security concerns, including potential integer overflows and a reentrancy vulnerability in the withdrawal mechanism. While the contract's core functionality is straightforward, the use of an outdated compiler and lack of modern security patterns elevate the overall risk to High.

> **Final Recommendation:** It is strongly recommended to migrate to a contract compiled with a modern Solidity version (e.g., 0.8.x) to leverage built-in safety features like SafeMath. Implement robust reentrancy guards for any functions performing external calls that transfer value. Thoroughly review and test all arithmetic operations to prevent integer overflows and underflows, ideally using OpenZeppelin's SafeMath library or Solidity's native overflow checks. Additionally, consider the implications of the ERC-20 `approve` race condition and advise users to set approvals to zero before increasing them.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture (7.1 Architecture) is a simple ERC-20-like token. However, the code security (7.2 Code Security) is significantly impacted by the use of Solidity 0.4.18, which lacks… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) of WBNB is straightforward: 1 BNB can be wrapped into 1 WBNB and vice-versa, maintaining a 1:1 peg. There are no complex fee structures, staking mechanisms, or… |
| **Upgrades** | 5/10 | Medium | The WBNB contract is not designed to be upgradeable (7.7 Upgrades). It is a standard, immutable contract without any proxy patterns (e.g., UUPS, Transparent, Beacon). This eliminates any risks… |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 1 Informational_

### `H-01` — Integer Overflow Vulnerabilities  *(Severity: High · Status: Unresolved)*

The contract uses Solidity 0.4.18, which does not include built-in overflow/underflow checks for arithmetic operations. Specifically, the `balanceOf[msg.sender] += msg.value;` in `deposit()` and `balanceOf[dst] += wad;` in `transferFrom()` are vulnerable to integer overflow. If a user's balance or the amount being added causes the `uint` to exceed its maximum value (`2^256 - 1`), the value will wrap around to zero, leading to incorrect balances and potential loss of funds or system manipulation.

**Recommendation:** Migrate to Solidity 0.8.0 or higher, which automatically reverts on arithmetic overflows/underflows. Alternatively, for older Solidity versions, integrate and use a SafeMath library (e.g., from OpenZeppelin) for all arithmetic operations involving user-controlled inputs or state variables.


### `H-02` — Reentrancy Vulnerability in `withdraw`  *(Severity: High · Status: Unresolved)*

The `withdraw` function transfers BNB to `msg.sender` using `msg.sender.transfer(wad);` before updating the user's balance (`balanceOf[msg.sender] -= wad;`). This violates the 'checks-effects-interactions' pattern. Although `transfer()` has a 2300 gas limit which mitigates some reentrancy attacks, it does not fully prevent them, especially against sophisticated attackers or if the recipient contract can re-enter within that gas limit. A malicious contract could potentially re-enter the `withdraw` function multiple times before the balance is updated, draining more BNB than intended.

**Recommendation:** Adhere to the 'checks-effects-interactions' pattern. Update the contract state (`balanceOf[msg.sender] -= wad;`) *before* performing any external calls (`msg.sender.transfer(wad);`). Additionally, consider using a reentrancy guard mechanism (e.g., OpenZeppelin's ReentrancyGuard) for critical functions involving external calls.


### `M-01` — ERC-20 `approve` Race Condition  *(Severity: Medium · Status: Unresolved)*

The `approve` function is susceptible to a known ERC-20 race condition. If a user approves an amount `X` for a spender, and then attempts to change that approval to `Y` (where `Y` is not zero), a malicious spender could front-run the transaction changing the approval. The spender could spend `X` tokens, and then the second `approve` transaction would execute, granting approval for `Y` tokens as well, effectively allowing the spender to spend `X+Y` tokens.

**Recommendation:** Advise users to always set the allowance to zero (`approve(spender, 0)`) before increasing it to a new non-zero value. Alternatively, implement a `increaseAllowance` and `decreaseAllowance` pattern (as seen in modern ERC-20 implementations) to mitigate this race condition.


### `M-02` — Fixed Gas Limit for BNB Transfers  *(Severity: Medium · Status: Unresolved)*

The `msg.sender.transfer(wad)` call in the `withdraw` function uses a fixed gas stipend of 2300. While this is a security measure against reentrancy for simple contracts, it can cause legitimate transfers to fail if the recipient is a contract that requires more than 2300 gas in its fallback function to process the incoming BNB. This could lead to users being unable to withdraw their funds if they are using certain types of smart contract wallets or other complex contract addresses.

**Recommendation:** Consider using `call.value(wad)('')` instead of `transfer()` for sending BNB, combined with a reentrancy guard. `call` forwards all available gas by default, which is more flexible for recipient contracts. However, using `call` requires careful implementation of reentrancy protection.


### `I-01` — Use of Outdated Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with `pragma solidity ^0.4.18;`. This Solidity version is significantly outdated and lacks many security features, optimizations, and bug fixes present in newer Solidity versions (e.g., built-in SafeMath, `require`/`revert` for error handling, improved optimizer, clearer semantics). Developing with such an old version increases the risk of subtle vulnerabilities and makes the code harder to maintain and audit against modern standards.

**Recommendation:** It is highly recommended to migrate the contract to a recent and stable Solidity compiler version (e.g., 0.8.x). This would allow leveraging modern language features and security improvements, reducing the attack surface and improving code robustness.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbb4c...095c`](https://bscscan.com/address/0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c) |
| **Network** | BNB Chain |
| **Price** | $570.8900 |
| **24h Volume** | $1.78M |
| **Liquidity** | $33.02M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20443 buys / 23941 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x16b9a82891338f9ba80e2d6970fdda79d1eb0dae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-bnb-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
