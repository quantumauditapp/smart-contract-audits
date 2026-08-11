---
token: REPPO
ticker: REPPO
network: base
risk_score: 77
status: critical
date: 2026-08-11
---

# REPPO (REPPO) — Smart Contract Security Analysis | Base

> **Risk Score: 77/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/reppo-base)

---

## Audit Summary

This audit covers the provided snippet of the AgentTokenV2 contract. The contract implements an upgradeable ERC-20 token with tax mechanisms, bot protection, and Uniswap V2 integration. While utilizing standard OpenZeppelin patterns for upgradeability and access control, significant centralization risk exists due to extensive owner/factory privileges. A full security assessment is limited by the absence of critical functions like `_transfer` and `_swapAndLiquify`, which are essential for evaluating core token logic and tax collection mechanisms.

> **Final Recommendation:** It is recommended to thoroughly review the full contract code, especially the `_transfer` and `_swapAndLiquify` functions, to ensure all security best practices are followed and no hidden vulnerabilities exist. Implement a robust multi-signature wallet for the owner and factory addresses to mitigate the high centralization risk. Clearly document the intended use and security implications of the `_validCallerCodeHashes` mechanism.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin upgradeable patterns and `SafeERC20` for external token interactions, contributing to robust code security (7.2). A reentrancy guard… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the owner and factory having significant control over critical functions (7.3, 7.5). This includes the ability to blacklist addresses… |
| **Upgrades** | 1/10 | High | The contract correctly implements the `Initializable` and `Ownable2StepUpgradeable` patterns from OpenZeppelin, providing a secure and well-understood framework for future upgrades (7.7). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — High Centralization Risk via Owner/Factory Control  *(Severity: High · Status: Unresolved)*

The `onlyOwnerOrFactory` modifier grants significant control to the contract owner and the designated factory address. Functions such as `addBlacklistAddress`, `removeBlacklistAddress`, `addLiquidityPool`, `removeLiquidityPool`, `addValidCaller`, and `removeValidCaller` are protected by this modifier. This level of control allows a single entity (or two, if factory is distinct) to significantly impact token operations, including censoring users, manipulating liquidity pools, and controlling whitelisted callers. A compromise of the owner's or factory's private key could lead to severe consequences.

**Recommendation:** Implement a multi-signature wallet for the owner and factory addresses to distribute control and reduce the risk of a single point of failure. Consider implementing a time-lock for critical administrative actions to allow users to react to potentially malicious changes. Clearly communicate the extent of centralized control to users.


### `M-01` — Potential for MEV/Front-running in Initial Liquidity Provision  *(Severity: Medium · Status: Unresolved)*

The `addInitialLiquidity` function, while protected by `onlyOwnerOrFactory`, involves transferring tokens and creating LP tokens. If the `lpOwner` is a publicly known address or the timing of this transaction is predictable, MEV bots could potentially front-run or sandwich the liquidity addition, especially if the `pairToken` is volatile. This could lead to unfavorable pricing for the initial liquidity provider or exploit opportunities.

**Recommendation:** Consider using a private transaction relay or a trusted third-party service for the `addInitialLiquidity` transaction to mitigate front-running risks. Ensure the `lpOwner` address is secure and the transaction is executed at an unpredictable time.


### `M-02` — Unclear Purpose and Usage of `_validCallerCodeHashes` Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract includes a mechanism to manage `_validCallerCodeHashes` via `addValidCaller` and `removeValidCaller` functions. The purpose of this whitelist (i.e., which functions check `isValidCaller`) is not evident from the provided snippet. If this mechanism is used to restrict who can call certain critical functions (e.g., `_transfer` or `_swapAndLiquify`), it could introduce an unusual access control pattern that might be difficult to understand, audit, or manage, potentially leading to unintended restrictions or vulnerabilities if the whitelisted contracts are compromised or have their own flaws.

**Recommendation:** Clearly document the intended use cases and security implications of the `_validCallerCodeHashes` mechanism. Ensure that any functions relying on `isValidCaller` are thoroughly reviewed for potential bypasses or unintended consequences. If possible, consider if a more standard access control pattern (e.g., role-based access control) would achieve the same goal with greater clarity and auditability.


### `L-01` — Unused `CALL_GAS_LIMIT` Constant  *(Severity: Low · Status: Unresolved)*

The constant `CALL_GAS_LIMIT` is defined with a value of 50000, but it is not utilized anywhere in the provided contract snippet. This suggests either an incomplete implementation, a feature that was planned but not implemented, or dead code. If it was intended for external calls (e.g., in `_swapAndLiquify`), its absence could lead to out-of-gas errors for complex transactions or reentrancy vulnerabilities if external calls are not properly guarded.

**Recommendation:** Either remove the unused constant to improve code clarity and reduce bytecode size, or implement its intended functionality, ensuring it is applied correctly to external calls to prevent gas-related issues or reentrancy.


### `I-01` — Reentrancy Guard `_autoSwapInProgress` Implemented  *(Severity: Informational · Status: Unresolved)*

The contract utilizes an `_autoSwapInProgress` boolean flag, which is set to `true` during initialization and `false` after initial liquidity is added. This pattern is commonly used as a reentrancy guard for functions involving external calls, particularly in `_swapAndLiquify` operations. This is a good practice to prevent reentrant calls during sensitive operations.

**Recommendation:** Ensure that all external calls that could potentially lead to reentrancy are properly guarded by this flag or other appropriate mechanisms. Verify that the flag's state transitions are correctly managed throughout the contract's lifecycle, especially in the missing `_swapAndLiquify` function.


### `I-02` — Initial Ownership Transfer via `initialize` Function  *(Severity: Informational · Status: Unresolved)*

The `_transferOwnership(projectOwner_)` function is called within the `_decodeBaseParams` function, which is part of the `initialize` function. This sets the initial owner of the contract based on the `projectOwner_` parameter provided during initialization. This is a standard and secure way to establish ownership for upgradeable contracts deployed via a factory or proxy.

**Recommendation:** Ensure that the `projectOwner_` address provided during the contract's initialization is a secure, controlled address, preferably a multi-signature wallet, to maintain robust access control from the outset.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xff81...83d6`](https://basescan.org/address/0xff8104251e7761163fac3211ef5583fb3f8583d6) |
| **Network** | Base |
| **Price** | $0.01206 |
| **24h Volume** | $33.9K |
| **Liquidity** | $618.2K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 73.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 76 buys / 60 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xff8104251e7761163fac3211ef5583fb3f8583d6:bpool)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/reppo-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
