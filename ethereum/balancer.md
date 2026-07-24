---
token: Balancer
ticker: BAL
network: ethereum
risk_score: 30
status: medium
date: 2026-07-23
---

# Balancer (BAL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 30/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/balancer-eth)

---

## Audit Summary

This audit covers the provided Solidity source code for the `EnumerableSet` and `Address` libraries, which are OpenZeppelin dependencies. The full source code for the main contract, `BalancerGovernanceToken`, was not provided for analysis. The audited libraries are well-established and widely used, exhibiting high code quality and adherence to best practices. No critical or high-severity vulnerabilities were identified within the scope of the provided library code.

> **Final Recommendation:** It is recommended to conduct a comprehensive security audit of the main `BalancerGovernanceToken` contract, which utilizes these libraries, to ensure its overall security posture. Pay close attention to how `EnumerableSet`'s non-guaranteed order is handled and how `Address.isContract` is used, if at all, in the main contract's logic. Ensure that the main contract pins a specific Solidity compiler version for production deployments to avoid potential inconsistencies.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical review of the `EnumerableSet` and `Address` libraries reveals robust and efficient implementations (7.2 Code Security). Both libraries are standard OpenZeppelin components, benefiting… |
| **Governance / Economics** | 4/10 | Medium | As the provided source code consists solely of utility libraries (`EnumerableSet`, `Address`), there are no direct governance or economic mechanisms to assess (7.4 Economic, 7.5 Governance). The… |
| **Upgrades** | 3/10 | High | The provided source code consists of utility libraries and the prefill indicates `is_proxy: false`, therefore, upgradeability mechanisms are not directly applicable to these components (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 25.6% |
| **Top-3 Unlocked** | 55.0% |

## Security Findings

_⚪ 5 Informational_

### `I-01` — EnumerableSet Order Instability  *(Severity: Informational · Status: Unresolved)*

The `EnumerableSet` library explicitly states that the order of elements returned by `at(index)` is not guaranteed and may change upon addition or removal of other elements. This is an inherent design choice for achieving O(1) complexity for add/remove operations (7.1 Architecture).

**Recommendation:** Developers using `EnumerableSet` must not rely on the order of elements. If a stable order is required, an alternative data structure or additional logic to maintain order should be implemented in the consuming contract.


### `I-02` — `Address.isContract` Limitations  *(Severity: Informational · Status: Unresolved)*

The `Address.isContract` function, as noted in its NatSpec, has limitations and cannot reliably determine if an address is an Externally Owned Account (EOA) or a contract under all circumstances (e.g., during contract construction, after self-destruct, or for addresses where a contract will be created) (7.2 Code Security).

**Recommendation:** Avoid using `Address.isContract` for critical access control or security-sensitive logic where a definitive determination of contract vs. EOA is required. Consider alternative mechanisms like role-based access control or explicit registration for trusted contracts.


### `I-03` — Potential Gas Costs for Large Set Iteration  *(Severity: Informational · Status: Unresolved)*

While `add` and `remove` operations in `EnumerableSet` are O(1), iterating over a very large set using the `at(index)` function in a loop within a transaction could become prohibitively expensive in terms of gas. The `_values` array grows linearly with the number of elements (7.4 Economic).

**Recommendation:** If the consuming contract is expected to manage a very large number of elements and requires frequent iteration, consider off-chain processing or alternative designs that do not require on-chain iteration over the entire set. Implement pagination or limits for on-chain iteration if necessary.


### `I-04` — Compiler Version Flexibility  *(Severity: Informational · Status: Unresolved)*

The `pragma solidity ^0.6.0` directive allows compilation with any Solidity compiler version from 0.6.0 up to, but not including, 0.7.0. While this offers flexibility, minor compiler behavior changes across patch versions could theoretically lead to subtle differences in bytecode or execution (7.2 Code Security).

**Recommendation:** For production deployments of the main contract, it is a best practice to pin to a specific, immutable compiler version (e.g., `pragma solidity 0.6.8;`) to ensure consistent bytecode generation and behavior across deployments and audits.


### `I-05` — Explicit Type Casting for `bytes32` Conversion  *(Severity: Informational · Status: Unresolved)*

The library uses explicit type casting, such as `bytes32(uint256(value))` for `address` to `bytes32` conversions. This is a standard and correct way to handle these conversions in Solidity, ensuring that the values fit within the `bytes32` storage slot (7.2 Code Security).

**Recommendation:** No direct recommendation for the library itself. However, developers integrating or extending this library should be mindful of these type conversions and ensure similar explicit casting is used when converting between types to avoid truncation or unexpected behavior in their custom logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xba10...4e3d`](https://etherscan.io/address/0xba100000625a3754423978a60c9317c58a424e3d) |
| **Network** | Ethereum |
| **Price** | $0.1231 |
| **24h Volume** | $509.6K |
| **Liquidity** | $4.78M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 66.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 155 buys / 382 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5c6ee304399dbdb9c8ef030ab642b10820db8f56)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/balancer-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
