---
token: MetaSoilVerseProtocol
ticker: MSVP
network: bsc
risk_score: 42
status: medium
date: 2026-08-20
---

# MetaSoilVerseProtocol (MSVP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/metasoilverseprotocol-bsc)

---

## Audit Summary

This audit focused on a set of utility libraries (`Context`, `IERC165`, `SignedMath`, `Math`, `ERC165`, `Strings`). The core `MSVP` contract, which would utilize these libraries and define the protocol's primary logic, was not provided. Therefore, the assessment is limited to the security and correctness of these foundational components. The libraries demonstrate robust mathematical operations and string utilities, but the use of inline assembly in `Math.mulDiv` and `unchecked` blocks requires careful integration and validation by the consuming contracts.

> **Final Recommendation:** It is crucial to conduct a comprehensive audit of the main `MSVP` contract once it becomes available, focusing on how these utility libraries are integrated and utilized. Particular attention should be paid to the inputs provided to functions using `unchecked` blocks and the `mulDiv` assembly to ensure all edge cases and potential overflow/underflow scenarios are robustly handled. Implement thorough unit and integration tests for all critical paths involving these mathematical operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture consists of well-defined utility libraries for mathematical operations and string conversions (7.1 Architecture). The `Math` library provides advanced functions like… |
| **Governance / Economics** | 3/10 | High | The provided contracts are utility libraries and do not contain any economic mechanisms (7.4 Economic) or governance structures (7.5 Governance). Therefore, economic and governance risks cannot be… |
| **Upgrades** | 8/10 | Low | The provided code consists of standalone utility libraries and abstract contracts, which are not designed to be upgradeable themselves (7.7 Upgrades). The prefill data indicates `is_proxy: false`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Complex Inline Assembly in `Math.mulDiv`  *(Severity: High · Status: Unresolved)*

The `mulDiv` function in the `Math` library utilizes complex inline assembly for critical arithmetic operations. While assembly can offer performance benefits and precise control, it is significantly more difficult to audit, verify, and maintain compared to high-level Solidity. Subtle errors in assembly can lead to incorrect calculations, unexpected behavior, or even critical vulnerabilities that are hard to detect. The current implementation involves intricate bitwise operations and `mulmod` calls.

**Recommendation:** Thoroughly review and formally verify the `mulDiv` assembly code to ensure its correctness across all possible input ranges. Consider adding extensive unit tests specifically for `mulDiv` covering edge cases, large numbers, and zero values. If possible, provide detailed comments explaining each step of the assembly logic. Alternatively, consider using a well-vetted and simpler `mulDiv` implementation if the performance gains from this specific assembly are not strictly necessary.


### `M-01` — Extensive Use of `unchecked` Blocks Without Contextual Validation  *(Severity: Medium · Status: Unresolved)*

Several functions within the `Math` and `SignedMath` libraries, such as `abs`, `sqrt`, `log2`, `log10`, and `log256`, employ `unchecked` blocks. While `unchecked` is a valid optimization in Solidity 0.8.0+ to prevent automatic overflow/underflow checks, it shifts the responsibility of ensuring arithmetic safety to the caller. Without the context of the `MSVP` contract, it's unclear if all inputs to these `unchecked` operations are guaranteed to prevent overflows or underflows, potentially leading to incorrect state changes or unexpected behavior if not properly validated by the consuming contract.

**Recommendation:** Ensure that any contract utilizing these `unchecked` functions performs rigorous input validation or has strong invariants that guarantee arithmetic safety. Document the assumptions made about input ranges for each `unchecked` block. When integrating these libraries into `MSVP`, verify that all calls to these functions are safe from overflow/underflow based on the specific application logic.


### `L-01` — Potential for Precision Loss in `mulDiv` with Default Rounding  *(Severity: Low · Status: Unresolved)*

The `mulDiv` function, when called without a `Rounding` parameter or with `Rounding.Zero`, truncates the result, effectively rounding down. While this behavior is often desired, if not explicitly accounted for in economic calculations, repeated truncations can lead to a cumulative loss of precision. This could result in minor discrepancies over time, potentially affecting token balances or reward distributions if not properly managed.

**Recommendation:** Ensure that the consuming `MSVP` contract explicitly considers the rounding behavior of `mulDiv`. For sensitive economic calculations where precision is paramount, evaluate if `Rounding.Up` or a custom rounding logic is more appropriate. Document the chosen rounding strategy for all critical calculations to prevent misunderstandings and ensure consistent behavior.


### `I-01` — Missing Core Contract Logic (`MSVP`)  *(Severity: Informational · Status: Unresolved)*

The provided source code only includes utility libraries (`Context`, `IERC165`, `SignedMath`, `Math`, `ERC165`, `Strings`). The main `MSVP` contract, which would integrate these libraries and define the core business logic, state variables, and user interactions of the protocol, was not supplied for review. This significantly limits the scope of the audit, as the overall security posture, economic model, access control, and upgradeability of the actual protocol cannot be assessed.

**Recommendation:** Provide the complete source code for the `MSVP` contract and any other relevant contracts that comprise the protocol. A full audit requires access to all interconnected components to thoroughly evaluate potential vulnerabilities, interactions, and overall system design.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6199...fb20`](https://bscscan.com/address/0x619940c0f69f1612245f94b7659403623239fb20) |
| **Network** | BNB Chain |
| **Price** | $0.0004785 |
| **24h Volume** | $40.3K |
| **Liquidity** | $47.6K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 66.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 531 buys / 339 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb47afe51524ba76d9e2108558e04220d51b2c179)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/metasoilverseprotocol-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
