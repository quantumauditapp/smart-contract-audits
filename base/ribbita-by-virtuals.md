---
token: Ribbita by Virtuals
ticker: TIBBIR
network: base
risk_score: 57
status: high
date: 2026-08-11
---

# Ribbita by Virtuals (TIBBIR) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ribbita-by-virtuals-base)

---

## Audit Summary

The AgentToken contract is an upgradeable ERC20-like token with integrated tax mechanisms, liquidity management via Uniswap V2, and a custom access control model involving a factory contract. The contract utilizes OpenZeppelin's upgradeable patterns and libraries, contributing to a robust foundation. However, significant centralization risks associated with the factory address's extensive control and potential economic vulnerabilities related to tax parameters and Uniswap V2 price reliance have been identified, leading to an overall 'High' risk level.

> **Final Recommendation:** It is crucial to ensure the security and robustness of the `_factory` address, as it holds significant control over the token's parameters. Consider implementing a multi-signature wallet or a well-audited governance contract for the factory to mitigate centralization risks. Additionally, establish and enforce reasonable upper limits for tax rates to prevent potential economic instability. For critical operations relying on external price feeds, explore integrating more robust, decentralized oracle solutions or implementing time-weighted average price (TWAP) mechanisms to reduce susceptibility to price manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates good architectural practices by leveraging OpenZeppelin's upgradeable contracts and using custom error types (7.1 Architecture, 7.2 Code Security). The `_autoSwapInProgress`… |
| **Governance / Economics** | 2/10 | High | The contract's economic model includes configurable buy and sell taxes, which can be adjusted by the owner or factory (7.4 Economic). While this offers flexibility, the absence of explicit upper… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS proxy pattern by inheriting from `Initializable` and calling `_disableInitializers()` in the constructor, along with using the `initializer` modifier for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralization Risk via Factory Address  *(Severity: High · Status: Unresolved)*

The `_factory` address, set during initialization, is granted extensive administrative control through the `onlyOwnerOrFactory` modifier. This includes the ability to add/remove liquidity pools, manage valid callers, and set critical tax parameters. If the factory contract is compromised or poorly secured (e.g., a single EOA), it could lead to a complete compromise of the token's configurable parameters, allowing an attacker to manipulate taxes, liquidity, or block legitimate callers.

**Recommendation:** Implement robust security measures for the `_factory` address. Consider using a multi-signature wallet or a well-audited governance contract for the factory to distribute control and reduce the risk of a single point of failure. Clearly document the responsibilities and security requirements for the factory address.


### `M-01` — Potential for High Tax Rates  *(Severity: Medium · Status: Unresolved)*

The `projectBuyTaxBasisPoints` and `projectSellTaxBasisPoints` can be set by the owner or factory. While `MAX_SWAP_THRESHOLD_MULTIPLE` is defined, the provided code snippet does not show any explicit upper bounds or validation checks on the tax basis points themselves. Without such limits, an authorized entity could set excessively high tax rates, effectively rendering the token illiquid or unusable, leading to a loss of user funds or project failure.

**Recommendation:** Implement explicit upper limits for `projectBuyTaxBasisPoints` and `projectSellTaxBasisPoints` to prevent economically destructive configurations. These limits should be carefully chosen to maintain token utility and liquidity, and ideally, any changes to these limits should be subject to a time-lock or governance vote.


### `M-02` — Reliance on Uniswap V2 Price for Tax Swaps  *(Severity: Medium · Status: Unresolved)*

The contract relies on Uniswap V2 for price discovery when performing tax swaps (implied by `_uniswapRouter` and `swapThresholdBasisPoints`). Uniswap V2's spot price is susceptible to manipulation, especially for low-liquidity pairs, through flash loans or large trades. If the `pairToken` is easily manipulable, the automated tax swap mechanism could be exploited to execute swaps at unfavorable rates, leading to value loss for the protocol or its users.

**Recommendation:** For critical operations involving price-sensitive logic, consider integrating more robust and decentralized oracle solutions (e.g., Chainlink) or implementing a time-weighted average price (TWAP) mechanism from Uniswap V2 to mitigate flash loan and price manipulation risks. Ensure sufficient liquidity for the token's pair on Uniswap V2.


### `L-01` — Unused `CALL_GAS_LIMIT` Constant  *(Severity: Low · Status: Unresolved)*

The constant `CALL_GAS_LIMIT` is defined within the contract but is not utilized in the provided code snippet. While not a direct vulnerability, unused code can increase contract size, potentially leading to higher deployment costs, and may indicate incomplete or abandoned functionality.

**Recommendation:** Review the purpose of `CALL_GAS_LIMIT`. If it is intended for future functionality, ensure its value is appropriate for the intended external calls. If it is no longer needed, consider removing it to optimize contract size and clarity.


### `I-01` — `_autoSwapInProgress` Reentrancy Guard  *(Severity: Informational · Status: Unresolved)*

The contract utilizes a private boolean flag `_autoSwapInProgress` which is set to `true` during initialization and `false` after initial liquidity is added. This pattern is commonly used as a reentrancy guard to prevent reentrant calls during critical, multi-step operations, likely related to the automated tax swap mechanism (not fully shown in the snippet). This is a good security practice.

**Recommendation:** Ensure that all functions that modify or depend on the state protected by `_autoSwapInProgress` correctly set and reset the flag to maintain its effectiveness as a reentrancy guard.


### `I-02` — Use of `EnumerableSet` for Dynamic Sets  *(Severity: Informational · Status: Unresolved)*

The contract effectively uses OpenZeppelin's `EnumerableSet` for managing dynamic collections of addresses (`_liquidityPools`) and bytes32 hashes (`_validCallerCodeHashes`). This library provides efficient and secure ways to store and retrieve unique elements, which is a good practice for managing whitelists or lists of external contracts.

**Recommendation:** Continue to leverage `EnumerableSet` for managing dynamic sets where efficient iteration and membership checks are required. Ensure that access control for adding and removing elements from these sets remains robust.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa4a2...6e00`](https://basescan.org/address/0xa4a2e2ca3fbfe21aed83471d28b6f65a233c6e00) |
| **Network** | Base |
| **Price** | $0.1294 |
| **24h Volume** | $393.0K |
| **Liquidity** | $2.15M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 17.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 871 buys / 252 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0c3b466104545efa096b8f944c1e524e1d0d4888)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ribbita-by-virtuals-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
