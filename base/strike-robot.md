---
token: Strike Robot
ticker: SR
network: base
risk_score: 96
status: critical
date: 2026-08-13
---

# Strike Robot (SR) — Smart Contract Security Analysis | Base

> **Risk Score: 96/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/strike-robot-base)

---

## Audit Summary

The AgentTokenV3 contract implements an upgradeable ERC-20 token with custom tax mechanisms, bot protection, and integration with Uniswap V2. The audit identified significant centralization risks due to extensive owner control over critical parameters, and a high-severity denial of service vulnerability in the tax swap mechanism that could also lead to loss of accumulated tax funds. Several medium and low-severity issues were also found, primarily related to unused code, lack of emergency fund recovery, and potential for unexpected behavior with critical parameter changes. The contract utilizes OpenZeppelin's upgradeable patterns and includes a reentrancy guard for the tax swap, which are positive security practices.

> **Final Recommendation:** Prioritize addressing the high-severity denial of service and potential loss of funds in the `_swapTaxTokens` function by implementing robust error handling and ensuring `projectTaxPendingSwap` is only reset upon successful fund transfer. Evaluate the extent of centralized control and consider implementing multi-signature governance or time-locks for critical parameter changes to mitigate single points of failure. Additionally, implement an emergency withdrawal mechanism for accidentally sent tokens and clarify or remove unused code to reduce complexity and potential for future misuse.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates good architectural practices by leveraging OpenZeppelin's upgradeable contracts and implementing a reentrancy guard (`_autoSwapInProgress`) for the tax swap mechanism (7.1… |
| **Governance / Economics** | 1/10 | High | The contract's economic model includes configurable buy/sell taxes and bot protection, which are positive features (7.4 Economic). However, the owner (and factory) retains extensive control over… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using OpenZeppelin's `Initializable` and `Ownable2StepUpgradeable` patterns, ensuring a secure and controlled upgrade path (7.7 Upgrades). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control Over Critical Parameters  *(Severity: High · Status: Unresolved)*

The contract owner (and in some cases, the factory) has extensive control over critical parameters, including `projectBuyTaxBasisPoints`, `projectSellTaxBasisPoints`, `projectTaxRecipient`, `botProtectionDurationInSeconds`, `blacklists`, and `pairToken`. This level of centralization introduces a single point of failure, allowing a malicious or compromised owner to significantly alter the token's economics, block users, or disrupt liquidity pools. For example, changing `pairToken` after initial liquidity is added could lead to unexpected behavior or loss of funds.

**Recommendation:** Consider decentralizing control over critical parameters by implementing multi-signature governance for sensitive functions or introducing time-locks for changes to allow users to react. For `setPairToken`, evaluate if this function is truly necessary post-deployment, or if it should be restricted to only be callable before initial liquidity is added.


### `H-02` — Denial of Service and Potential Loss of Funds in `_swapTaxTokens`  *(Severity: High · Status: Unresolved)*

The `_swapTaxTokens` function performs an external call to `IAgentTaxForToken(projectTaxRecipient).depositTax`. If this call reverts for any reason (e.g., `projectTaxRecipient` is a malicious contract, or it runs out of gas), the entire `_swapTaxTokens` transaction will revert. Since `_swapTaxTokens` is called within `_update` (which is part of `_transfer`), this can block all token transfers when the tax swap threshold is met, leading to a denial of service. Furthermore, `projectTaxPendingSwap` is zeroed out *before* the Uniswap swap attempt. If the swap fails (even with the `try/catch` block) and the `catch` path is taken, the tokens intended for tax remain in the contract but are no long…

**Recommendation:** Implement robust error handling for the `depositTax` call, potentially by wrapping it in a `try/catch` block and logging failures, or by allowing the owner to manually retry or recover funds. Crucially, `projectTaxPendingSwap` should only be reset *after* the successful completion of both the Uniswap swap and the `depositTax` call to prevent loss of funds. Consider adding a mechanism for the owner to recover 'stuck' tax tokens if swaps consistently fail.


### `M-01` — Unused `_validCallerCodeHashes` Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract includes `_validCallerCodeHashes` and functions to manage it (`addValidCaller`, `removeValidCaller`), but the provided code does not show any usage of this mechanism. This could be dead code, an incomplete feature, or a placeholder for future functionality. Unused code adds unnecessary complexity, increases the contract's attack surface, and can lead to confusion during audits or future development.

**Recommendation:** Either integrate the `_validCallerCodeHashes` mechanism into the contract's logic with a clear purpose, or remove it entirely to reduce complexity and potential for misuse. If it's intended for future use, document its purpose clearly.


### `L-01` — Lack of Emergency Withdrawal/Rescue Function  *(Severity: Low · Status: Unresolved)*

The contract lacks a mechanism to recover ERC-20 tokens (other than its own token or the `pairToken` used for liquidity) that might be accidentally sent to the contract address. If any arbitrary ERC-20 token is sent to the contract, it will be permanently locked and inaccessible.

**Recommendation:** Implement a generic `rescueERC20` function, callable only by the owner, that allows withdrawing arbitrary ERC-20 tokens from the contract. Ensure this function cannot be used to drain the contract's own token or the `pairToken` essential for its operation.


### `L-02` — Risky `setPairToken` Function  *(Severity: Low · Status: Unresolved)*

The `setPairToken` function allows the owner to change the `pairToken` after deployment. While this might be intended for flexibility, changing this critical parameter after initial liquidity has been added could break existing liquidity pools, disrupt the tax mechanism, and potentially lead to loss of funds or unexpected behavior if not handled carefully. There are no checks to prevent setting an invalid or malicious `pairToken`.

**Recommendation:** If `setPairToken` is truly necessary, add robust validation for the new `pairToken` address. Consider adding a time-lock or multi-signature requirement for this function due to its critical impact. Alternatively, restrict its callable window to only before initial liquidity is added or make it immutable after deployment.


### `I-01` — `_autoSwapInProgress` Initial State  *(Severity: Informational · Status: Unresolved)*

The `_autoSwapInProgress` flag is initialized to `true` in the `initialize` function and then set to `false` in `_addInitialLiquidity`. This means that any token transfers occurring between the contract's initialization and the addition of initial liquidity would attempt to trigger `_swapTaxTokens`. As there would be no Uniswap pair or liquidity at that stage, these early transfers would likely fail, potentially blocking early operations.

**Recommendation:** Consider initializing `_autoSwapInProgress` to `false` if transfers are expected before initial liquidity is added, or clearly document this behavior and its implications for early token operations.


### `I-02` — Complex `_transfer` Function Logic  *(Severity: Informational · Status: Unresolved)*

The `_update` function, which forms the core of the `_transfer` and `_transferFrom` logic, is quite complex. It incorporates checks for blacklisted addresses, bot protection, tax calculation, tax accumulation, and conditional tax swapping. While these features are integral to the token's design, the combined logic within a single function increases its cognitive load and the potential for subtle bugs.

**Recommendation:** Consider refactoring the `_update` function to separate concerns where possible, perhaps by extracting specific checks or calculations into smaller, more focused internal functions. This can improve readability, maintainability, and reduce the risk of errors.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x10c5...1ac9`](https://basescan.org/address/0x10c56f005a379f8eafc88ff5c3f40d30f0031ac9) |
| **Network** | Base |
| **Price** | $0.001317 |
| **24h Volume** | $133.7K |
| **Liquidity** | $104.0K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 94.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 239 buys / 165 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x93e7c445d77e6506b77c869c469e4305c15c075b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/strike-robot-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
