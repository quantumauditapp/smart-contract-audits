---
token: Wootrade Network
ticker: WOO
network: ethereum
risk_score: 70
status: high
date: 2026-09-06
---

# Wootrade Network (WOO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wootrade-network-eth)

---

## Audit Summary

The WootradeNetwork contract is an ERC-20-like token implementation. The audit identified critical vulnerabilities related to integer overflows, a high-severity ERC-20 `approve` race condition, and the use of an outdated Solidity compiler version. These issues pose significant risks to token integrity and user funds.

> **Final Recommendation:** It is strongly recommended to migrate this contract to a newer Solidity version (e.g., 0.8.x) and implement robust integer overflow/underflow protection using SafeMath or similar libraries. The ERC-20 `approve` function should be carefully reviewed, and users should be advised on the race condition. For the `approveAndCall` function, consider implementing reentrancy guards or ensuring the called contract is trusted and audited.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a basic ERC-20 token with an `approveAndCall` extension. Strengths include a fallback function that prevents accidental Ether transfers and basic checks for `_value > 0` in… |
| **Governance / Economics** | 1/10 | High | The WootradeNetwork token is a standard ERC-20-like asset with no complex economic models or governance mechanisms (7.4 Economic, 7.5 Governance). The initial token supply is minted to the deployer… |
| **Upgrades** | 5/10 | Medium | The WootradeNetwork contract is not designed to be upgradeable (7.7 Upgrades). It is a standard, non-proxy implementation, meaning its logic cannot be modified after deployment. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.6% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Integer Overflow in Token Balances  *(Severity: Critical · Status: Unresolved)*

The `balances[_to] += _value;` operation in both `transfer` and `transferFrom` functions lacks protection against integer overflow. In Solidity versions prior to 0.8.0, arithmetic operations do not automatically revert on overflow. A malicious actor could potentially cause an overflow if `_value` is sufficiently large and `balances[_to]` is near `type(uint256).max`, leading to an incorrect balance (wrapping around to a small number) and effectively minting tokens.

**Recommendation:** Upgrade to Solidity 0.8.0 or higher, which includes built-in overflow/underflow checks. Alternatively, for older Solidity versions, use a SafeMath library for all arithmetic operations to prevent overflows and underflows.


### `H-01` — ERC-20 `approve` Race Condition  *(Severity: High · Status: Unresolved)*

The `approve` function is vulnerable to a known ERC-20 race condition. If a user approves an amount `X` for a spender, then decides to change it to `Y` (where `Y < X`), a front-running attacker could observe the transaction changing `X` to `Y`, quickly execute a `transferFrom` for amount `X` before the `approve(Y)` transaction is mined. The `approve(Y)` transaction would then proceed, leaving the spender with an allowance of `Y` after having already spent `X`, allowing the spender to spend more than intended. The `approveAndCall` function also sets `allowed` and is thus susceptible to this initial race condition before the external call.

**Recommendation:** Advise users to first set the allowance to zero with `approve(spender, 0)` and wait for that transaction to confirm before setting a new allowance. Alternatively, implement a `decreaseAllowance` and `increaseAllowance` pattern, or use a more robust `approve` mechanism that prevents this race condition.


### `H-02` — Outdated Solidity Compiler Version  *(Severity: High · Status: Unresolved)*

The contract uses Solidity `^0.4.4`, which is likely compiled with version `0.4.18` as per the provided metadata. This compiler version is significantly outdated and lacks many security features, optimizations, and bug fixes present in newer compilers (e.g., `0.8.x`). Notably, it does not include built-in overflow/underflow checks for arithmetic operations, which is a major source of vulnerabilities if not manually mitigated (e.g., with SafeMath).

**Recommendation:** Upgrade the contract to a modern Solidity compiler version (e.g., 0.8.x). This will automatically enable important security features like checked arithmetic, reducing the risk of integer overflows/underflows, and benefit from other compiler improvements and bug fixes.


### `M-01` — Risky `approveAndCall` External Call  *(Severity: Medium · Status: Unresolved)*

The `approveAndCall` function performs an external call to an arbitrary `_spender` address. While the allowance is updated before the call, external calls to untrusted contracts introduce risks. A malicious or buggy `_spender` contract could revert, causing the `approveAndCall` transaction to fail, or potentially attempt reentrancy (though less direct in this specific pattern due to state changes preceding the call). The use of `keccak256` for selector generation is also an older, less explicit pattern compared to `abi.encodeWithSelector`.

**Recommendation:** Ensure that any `_spender` contract called via `approveAndCall` is fully trusted and audited. Consider implementing reentrancy guards if the contract's logic were to involve more complex interactions. For new development, use `abi.encodeWithSelector` for clarity and type safety when encoding function calls.


### `L-01` — Redundant `totalSupply` Declaration  *(Severity: Low · Status: Unresolved)*

The `totalSupply` state variable is declared multiple times across the inheritance chain: in `Token`, `StandardToken`, and `WootradeNetwork`. While the declaration in `WootradeNetwork` effectively shadows the others, this redundancy can lead to confusion for developers and is considered poor coding practice.

**Recommendation:** Declare `totalSupply` only once in the base `Token` contract or the most appropriate contract in the inheritance hierarchy, and ensure derived contracts do not redeclare it. This improves code clarity and maintainability.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4691...5d4b`](https://etherscan.io/address/0x4691937a7508860f876c9c0a2a617e7d9e945d4b) |
| **Network** | Ethereum |
| **Price** | $0.01217 |
| **24h Volume** | $670.5K |
| **Liquidity** | $638.8K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 76.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 434 buys / 422 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x6ada49aeccf6e556bb7a35ef0119cc8ca795294a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wootrade-network-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
