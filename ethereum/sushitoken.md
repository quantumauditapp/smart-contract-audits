---
token: SushiToken
ticker: SUSHI
network: ethereum
risk_score: 46
status: medium
date: 2026-09-01
---

# SushiToken (SUSHI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sushitoken-eth)

---

## Audit Summary

This audit covers a partial Solidity codebase for an ERC-20 token, including standard OpenZeppelin-like implementations for Context, IERC20, SafeMath, Address, ERC20, and Ownable. The contract leverages SafeMath for arithmetic safety. Key findings include centralized control via the owner, lack of an emergency pause mechanism, and the inherent ERC20 approve race condition. The audit is limited by the absence of the full SushiToken contract, which would define specific business logic and owner-callable functions.

> **Final Recommendation:** It is recommended to implement an emergency pause mechanism to provide a safety net against unforeseen issues. For critical owner-controlled functions, consider integrating a multi-signature wallet or a time-lock contract to decentralize control and introduce a delay for sensitive operations, enhancing security and transparency. Review the full `SushiToken` contract to confirm whether `_mint` and `_burn` functions are exposed to the owner and assess their implications on tokenomics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1 Architecture) is based on well-established ERC-20 standards and OpenZeppelin patterns, utilizing SafeMath for robust arithmetic operations (7.2 Code Security). This… |
| **Governance / Economics** | 5/10 | Medium | The contract employs an `Ownable` pattern (7.3 Access Control), granting significant centralized control to a single address. The prefill indicates this owner is an `OZ_ProxyAdmin` (7.5 Governance)… |
| **Upgrades** | 4/10 | Medium | Based on the provided prefill data, the contract itself is not a proxy (`is_proxy: false`), meaning it is not directly upgradeable (7.7 Upgrades). This reduces the risk associated with upgrade… |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract lacks a `Pausable` mechanism, which could be crucial for mitigating risks during emergencies such as critical vulnerabilities, market exploits, or unexpected behavior. Without the ability to pause transfers or other critical functions, the protocol would be unable to react swiftly to prevent further damage.

**Recommendation:** Integrate OpenZeppelin's `Pausable` contract or a similar mechanism to allow the owner (preferably a multi-sig or governance) to pause and unpause critical operations. This provides an essential emergency stop functionality.


### `M-02` — Centralized Control via Owner Privileges  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Ownable` pattern grants a single address significant control over the contract. While `_mint` and `_burn` functions are internal in the provided ERC20 base, if the full `SushiToken` contract exposes these to the owner, it would allow unilateral inflation or deflation of the token supply. Even without direct mint/burn, the owner can transfer ownership, which is a critical privilege. The current owner being an `OZ_ProxyAdmin` implies a potentially upgradeable or complex governance structure for the owner itself, which could change the entity controlling the token.

**Recommendation:** Implement a multi-signature wallet or a time-lock contract for ownership and critical administrative functions. This decentralizes control, adds a delay for sensitive operations, and reduces the risk of a single point of failure or malicious action. Clearly document the capabilities of the owner in the full `SushiToken` contract.


### `L-01` — ERC20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The standard `approve` function is susceptible to a known race condition. If a user approves an amount, and then attempts to approve a different amount, a malicious spender could front-run the second `approve` transaction. This could result in the spender being able to spend both the original and the new approved amounts, potentially draining funds beyond the user's intent. While `increaseAllowance` and `decreaseAllowance` mitigate this, direct `approve` calls remain vulnerable.

**Recommendation:** Educate users to use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying an existing allowance. If `approve` must be used, users should first set the allowance to zero before setting a new value.


### `I-01` — Incomplete Contract Context  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided code snippet represents core ERC20 and utility contracts (`Context`, `IERC20`, `SafeMath`, `Address`, `ERC20`, `Ownable`). However, the specific `SushiToken` contract implementation, which would inherit and potentially extend these with unique business logic, constructor parameters, and owner-callable functions, is missing. This limits the scope of a full security assessment, as specific functionalities and their interactions are not visible.

**Recommendation:** Provide the complete source code for the `SushiToken` contract to enable a comprehensive security audit of its specific logic, state variables, and function implementations.


### `I-02` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses Solidity `^0.6.0`. While this version is functional, newer compiler versions (e.g., 0.8.x) include additional safety checks by default (e.g., integer overflow/underflow protection without explicit SafeMath) and introduce language features that can improve code robustness, efficiency, and readability.

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent stable release (e.g., 0.8.x) to benefit from improved security features and optimizations. Ensure thorough testing if an upgrade is performed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6b35...0fe2`](https://etherscan.io/address/0x6b3595068778dd592e39a122f4f5a5cf09c90fe2) |
| **Network** | Ethereum |
| **Price** | $0.1999 |
| **24h Volume** | $58.4K |
| **Liquidity** | $971.3K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 42.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 163 buys / 173 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x87c7056bbe6084f03304196be51c6b90b6d85aa2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sushitoken-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
