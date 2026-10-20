---
token: Atoshi
ticker: ATOS
network: ethereum
risk_score: 69
status: high
date: 2026-09-23
---

# Atoshi (ATOS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/atoshi-eth)

---

## Audit Summary

The Atoshi contract is a basic ERC-20 token implementation. The audit identified a critical integer overflow vulnerability in addition operations, which can lead to incorrect balance updates and potential loss of funds. Additionally, the standard ERC-20 `approve` function is susceptible to a known front-running attack. Several minor issues related to missing zero-address and zero-value checks were also noted. The contract is not upgradeable and has a simple economic model.

> **Final Recommendation:** It is strongly recommended to address the critical integer overflow vulnerability by implementing SafeMath for all arithmetic operations, especially additions, to prevent potential loss of funds or incorrect balance states. Developers should also consider implementing the ERC-20 `approve` mitigation pattern (e.g., `increaseAllowance`/`decreaseAllowance`) or advising users to set allowance to zero before changing it to mitigate front-running risks. Additionally, adding checks for zero addresses and zero values in transfer functions can improve robustness and user experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1) is a standard ERC-20 implementation, which is straightforward. However, the code security (7.2) is significantly compromised by a critical integer overflow… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) is very simple: a fixed supply token minted entirely to the deployer at creation, with no further minting, burning, or fee mechanisms. This simplicity reduces complexity and… |
| **Upgrades** | 5/10 | Medium | The Atoshi contract is not designed to be upgradeable (7.7). It does not implement any proxy patterns (e.g., UUPS, Transparent, Beacon) or other mechanisms for future modification. This means there… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟢 2 Low_

### `C-01` — Integer Overflow in Addition Operations  *(Severity: Critical · Status: Unresolved)*

The `balances[_to] += _value` operations in both the `transfer` and `transferFrom` functions are susceptible to integer overflow. In Solidity versions prior to 0.8.0, arithmetic operations do not automatically revert on overflow. If `balances[_to]` is a large number and `_value` is also large, their sum could exceed `2**256 - 1`, causing the balance to wrap around to a smaller number. This can lead to incorrect balance tracking and potential loss of funds for users or manipulation of the total supply.

**Recommendation:** Implement a SafeMath library for all arithmetic operations, especially additions, to ensure that overflows are checked and revert the transaction if they occur. For example, use `add(balances[_to], _value)` from OpenZeppelin's SafeMath.


### `H-01` — ERC-20 `approve` Race Condition Vulnerability  *(Severity: High · Status: Unresolved)*

The standard ERC-20 `approve` function is vulnerable to a known front-running attack. If a user approves an amount for a spender, and then later approves a different (usually higher) amount without first setting the allowance to zero, a malicious actor can front-run the second `approve` transaction. The attacker can spend the original allowance, and then the second `approve` transaction will succeed, allowing the attacker to spend the newly approved amount as well, effectively spending more than the user intended.

**Recommendation:** While this is a known ERC-20 design flaw, it can be mitigated. Advise users to always set their allowance to zero before approving a new, non-zero amount. Alternatively, consider implementing `increaseAllowance` and `decreaseAllowance` functions (as seen in later ERC-20 standards) which are not susceptible to this race condition.


### `L-01` — Missing Zero-Address Checks  *(Severity: Low · Status: Unresolved)*

The `transfer` and `transferFrom` functions do not include checks to prevent sending tokens to the zero address (`address(0)`). While sending tokens to the zero address effectively burns them, this might be an unintended action by the user and can lead to irreversible loss of tokens.

**Recommendation:** Add a `require(_to != address(0), "ERC20: transfer to the zero address")` check at the beginning of the `transfer` and `transferFrom` functions to prevent accidental burning of tokens.


### `L-02` — Missing Zero-Value Checks  *(Severity: Low · Status: Unresolved)*

The `transfer` and `transferFrom` functions do not explicitly check if the `_value` parameter is zero. While transferring zero tokens has no functional impact on balances, it still consumes gas and emits an event. This can lead to unnecessary transaction costs.

**Recommendation:** Consider adding a `require(_value > 0, "ERC20: transfer amount must be greater than zero")` check to the `transfer` and `transferFrom` functions to prevent zero-value transfers and save gas.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4d05...4b18`](https://etherscan.io/address/0x4d0528598f916fd1d8dc80e5f54a8feedcfd4b18) |
| **Network** | Ethereum |
| **Price** | $0.04839 |
| **24h Volume** | $67.5K |
| **Liquidity** | $159.9K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 98.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 102 buys / 116 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc3abd8c07f0d669906f4be495389f2dcc598020f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/atoshi-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
