---
token: 717ai by Virtuals
ticker: WIRE
network: base
risk_score: 55
status: medium
date: 2026-09-19
---

# 717ai by Virtuals (WIRE) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/717ai-by-virtuals-base)

---

## Audit Summary

This audit report covers the provided source code for the AgentToken contract, which serves as the implementation for a proxy. A critical limitation of this audit is that the provided source code is truncated, missing essential ERC-20 transfer functions and the entire tax/auto-swap logic. This prevents a comprehensive assessment of the token's core functionality, economic model, and potential vulnerabilities. While the available code demonstrates good practices for upgradeability and access control, the absence of critical components means the overall security posture cannot be fully determined.

> **Final Recommendation:** To ensure the security and integrity of the AgentToken contract, it is imperative to provide the complete and untruncated source code for a comprehensive audit. Without the full implementation of core ERC-20 functions and the tax/auto-swap logic, a thorough security assessment cannot be performed, leaving critical vulnerabilities potentially undiscovered. Once the full code is available, a detailed review of the economic model, external interactions, and state management for flags like `_autoSwapInProgress` should be prioritized.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes OpenZeppelin's upgradeable patterns, `SafeERC20` for secure external token interactions, and `EnumerableSet` for managing dynamic lists, indicating a solid architectural… |
| **Governance / Economics** | 2/10 | High | The contract defines clear parameters for project buy/sell taxes, swap thresholds, and bot protection duration, indicating a structured economic model (7.4 Economic). The `onlyOwnerOrFactory`… |
| **Upgrades** | 6/10 | Medium | The contract correctly implements the OpenZeppelin `Initializable` pattern, including `_disableInitializers()` in the constructor and the `initializer` modifier for the setup function. This standard… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Incomplete Code for Critical Functionality  *(Severity: High · Status: Unresolved)*

The provided source code for the AgentToken contract is truncated, missing essential ERC-20 functions such as `transfer`, `transferFrom`, and `approve`, as well as the entire implementation of the tax calculation and auto-swap logic. This prevents a comprehensive security audit of the token's primary functionality and economic model, leaving critical attack vectors unexamined. Without these core components, it is impossible to assess potential reentrancy vulnerabilities, integer overflows in transfer amounts, or flaws in the tax collection and liquidity provision mechanisms.

**Recommendation:** Provide the complete and untruncated source code for the AgentToken contract, including all ERC-20 standard functions and the full implementation of the tax and auto-swap logic. A full audit cannot be performed without these critical components.


### `M-01` — Inconsistent `maxSupply` Type Check  *(Severity: Medium · Status: Unresolved)*

In the `_processSupplyParams` function, there is a check `erc20SupplyParameters_.maxSupply > type(uint128).max`. However, the contract's `_totalSupply` variable is declared as `uint256`. This check is either redundant if `_totalSupply` is truly intended to be `uint256` without an effective `uint128` limit, or it indicates a potential design inconsistency where the initial supply is limited to `uint128.max` but the total supply can theoretically exceed it, leading to confusion or unexpected behavior if not properly managed.

**Recommendation:** Clarify the intended maximum supply limit. If `_totalSupply` is meant to be limited to `uint128.max`, consider changing its type to `uint128` or explicitly document why the check is present for a `uint256` variable. If no `uint128` limit is intended for `_totalSupply`, remove the misleading check.


### `L-01` — Unclear `_autoSwapInProgress` State Management  *(Severity: Low · Status: Unresolved)*

The `_autoSwapInProgress` flag is initialized to `true` in the `initialize` function and then set to `false` in `_addInitialLiquidity`. While this sequence appears intentional for initial setup, the full logic for how this flag is used, reset, or prevented from being manipulated in the missing `_transfer` or `_swapAndLiquify` functions is crucial. Improper management or lack of clear state transitions for this flag could lead to tax collection failures, unexpected swap behavior, or denial of service for the auto-swap mechanism.

**Recommendation:** Ensure that the full implementation of the tax and auto-swap logic clearly defines and securely manages the state transitions of the `_autoSwapInProgress` flag. Implement robust checks to prevent unauthorized or unintended manipulation of this flag, and document its lifecycle thoroughly.


### `I-01` — `validCallerCodeHashes` Mechanism Brittleness  *(Severity: Informational · Status: Unresolved)*

The contract includes a mechanism to add and remove `bytes32` code hashes for 'valid callers'. While this provides a form of granular access control, it can be brittle. If a valid caller contract undergoes an upgrade, its code hash will change, requiring manual updates to the `_validCallerCodeHashes` set. This also relies on the hash calculation being robust and consistent across different deployment environments and compiler versions.

**Recommendation:** Consider the operational overhead and potential for errors when managing `validCallerCodeHashes`. If possible, explore alternative, more flexible access control mechanisms for contracts that are expected to be upgradeable. If this mechanism is critical, ensure clear documentation and operational procedures for updating hashes upon contract upgrades.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0b3a...aee0`](https://basescan.org/address/0x0b3ae50babe7ffa4e1a50569cee6bdefd4ccaee0) |
| **Network** | Base |
| **Price** | $0.001417 |
| **24h Volume** | $48.2K |
| **Liquidity** | $245.3K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 27.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 104 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8ffd336d457ada04a2d5112f8f0c1f1a84577f2f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/717ai-by-virtuals-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-19*
