---
token: 你们的胆子真是肥嘟嘟的
ticker: 肥嘟嘟
network: bsc
risk_score: 16
status: low
date: 2026-08-30
---

# 你们的胆子真是肥嘟嘟的 (肥嘟嘟) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-7a73dd-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex tax mechanism and a multi-state machine. The audit identified a High-severity risk related to the critical external dependency on the `taxProcessor` contract, which can lead to a denial of service for token transfers. Medium-severity issues include the immutability of other key external addresses and the direct DoS risk from `_processTax` reverts. The contract utilizes OpenZeppelin's upgradeable standards and incorporates reentrancy guards for its tax liquidation logic, demonstrating good security practices in some areas.

> **Final Recommendation:** It is strongly recommended to implement an owner-controlled mechanism to update critical external contract addresses, especially for the `taxProcessor`, `v2Router`, `quoteToken`, and `dividendContract`. This would mitigate the single point of failure and enhance operational flexibility without requiring a full contract upgrade for dependency changes. Additionally, consider implementing robust error handling or a circuit breaker mechanism for the `_processTax` external call to prevent a complete denial of service for token transfers if the `taxProcessor` reverts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 standard, providing a solid foundation (7.2 Code Security). A reentrancy guard is implemented around the `_processTax` call within… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model relies heavily on the `taxProcessor` for tax collection and liquidation threshold adjustments, centralizing significant control (7.4 Economic). Owner-controlled… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's `Initializable` and `Upgradeable` contracts, including `_disableInitializers()` in the constructor and proper `__init`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Critical External Dependency and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The `taxProcessor` contract is a critical external dependency, responsible for processing collected taxes and potentially adjusting the `liquidationThreshold`. It is set during initialization and cannot be changed. This introduces a significant centralization risk and a single point of failure. If the `taxProcessor` contract is compromised, becomes malicious, or is unfunctional, it can halt all token transfers (via `_processTax` reverting) or manipulate key economic parameters, leading to a denial of service or economic exploit.

**Recommendation:** Implement an owner-controlled function to update the `taxProcessor` address. This function should include a timelock and/or a multi-signature approval process to provide a window for review and prevent immediate malicious changes. Ensure the new `taxProcessor` contract is thoroughly audited.


### `M-01` — Immutability of Key External Addresses  *(Severity: Medium · Status: Unresolved)*

Several critical external contract addresses (`v2Router`, `quoteToken`, `taxProcessor`, `dividendContract`) are set only during initialization and lack setter functions. This makes them effectively immutable. Should any of these dependencies require an update (e.g., due to an upgrade, security vulnerability, or market changes), the entire `FlapTaxTokenV3` contract would need to undergo a full upgrade, which is a more complex and costly operation compared to simply updating an address via an owner-controlled setter.

**Recommendation:** Introduce owner-controlled setter functions for `v2Router`, `quoteToken`, and `dividendContract`. These setters should include appropriate access control (e.g., `onlyOwner`) and potentially a timelock for critical addresses to allow for community review or emergency response.


### `M-02` — Denial of Service Risk from External Call Revert  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function, which is invoked during every `_transfer` operation, makes an external call to `taxProcessor.processTax()`. If this external call reverts for any reason (e.g., `taxProcessor` is paused, drained, or encounters an internal error), it will cause the entire `_transfer` transaction to revert. This creates a denial of service vulnerability for all token transfers, effectively freezing the token's utility.

**Recommendation:** Consider implementing a circuit breaker or a fallback mechanism for the `_processTax` call. For example, if `_processTax` reverts, the contract could temporarily disable tax processing or allow transfers to proceed without tax, while alerting the owner. Alternatively, ensure the `taxProcessor` contract is extremely robust and cannot be easily bricked or made to revert.


### `L-01` — Potential for `uint48` Overflow in `antiFarmerExpirationTime`  *(Severity: Low · Status: Unresolved)*

The `antiFarmerExpirationTime` variable is stored as a `uint48`. While `block.timestamp` is currently far from exceeding the maximum value of `uint48` (approximately 2.8 x 10^14, which corresponds to roughly 89,000 years from the Unix epoch), in extremely long-lived contracts, this could theoretically lead to an overflow. Although a very low risk for typical contract lifespans, it's a consideration for extreme longevity.

**Recommendation:** For maximum future-proofing, consider using `uint64` for `antiFarmerExpirationTime` to align with `taxExpirationTime` and provide a significantly longer safe operating period. Alternatively, document this limitation and its implications for the contract's expected lifespan.


### `I-01` — Complex State Machine and Logic  *(Severity: Informational · Status: Unresolved)*

The contract implements a multi-state machine (`PoolState`) with several transitions and conditional logic within the `_transfer` and `_liquidateTax` functions. While designed to manage different phases of the token, this complexity increases the surface area for potential logic errors or unexpected behavior, particularly during state transitions. Comprehensive testing of all state paths is crucial to ensure correct operation.

**Recommendation:** Ensure comprehensive unit and integration tests cover all possible state transitions and edge cases within the `_transfer` and `_liquidateTax` functions. Consider formal verification for the state machine logic to mathematically prove its correctness and prevent unintended behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x03c5...7777`](https://bscscan.com/address/0x03c59bbf8ba49ce79831403b86acbc40d3167777) |
| **Network** | BNB Chain |
| **Price** | $0.0008376 |
| **24h Volume** | $172.5K |
| **Liquidity** | $106.1K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 7d |
| **Top-10 Holders** | 15.4% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1899 buys / 1322 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x07f159d04ad8011337627c9874cd59a4b2fc120a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-7a73dd-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
