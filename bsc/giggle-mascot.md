---
token: Giggle Mascot
ticker: MAX
network: bsc
risk_score: 16
status: low
date: 2026-08-11
---

# Giggle Mascot (MAX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/giggle-mascot-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an upgradeable ERC20 token designed with a dynamic tax mechanism, anti-farmer features, and a state machine to manage its lifecycle. It leverages OpenZeppelin's upgradeable contracts for robustness. The audit identified a high level of centralization of control by the owner, critical dependencies on external contracts, and a potential integer overflow in a time-based calculation. The contract implements reentrancy guards for its tax liquidation process, which is a positive security practice.

> **Final Recommendation:** It is recommended to implement robust validation and constraints for input parameters, particularly for time-related values, to prevent potential overflows. A comprehensive audit of all external dependencies, specifically the `ITaxProcessor` and `IDividend` contracts, is crucial to ensure the overall security and economic stability of the system. Consider decentralizing critical owner-controlled functions or implementing a multi-signature wallet for sensitive operations to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates good technical architecture, utilizing OpenZeppelin's upgradeable standards and a well-defined state machine for its tax and anti-farmer mechanisms. The `_liquidateTax`… |
| **Governance / Economics** | 9/10 | Low | The contract exhibits a high degree of centralization, with the `Owner` role possessing extensive control over critical parameters and state transitions (7.5 Governance). The owner can initiate… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements OpenZeppelin's `Initializable` pattern for upgradeability, including `_disableInitializers()` in the constructor and the `initializer` modifier. However, as with all… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.5% (≈ permanent lock) |
| **LP Locked** | 99.5% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralization of Control  *(Severity: High · Status: Unresolved)*

The `Owner` role has significant control over critical contract parameters and state transitions. Functions like `startMigration`, `finalizeMigration`, and the ability to set `taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, and `pools` are restricted to the owner. This centralization introduces a single point of failure and a high trust assumption in the owner's integrity and operational security, as a compromised owner key could lead to severe economic manipulation or system disruption.

**Recommendation:** Consider implementing a multi-signature wallet for the `Owner` role to distribute control and enhance security. For highly sensitive operations, explore mechanisms for decentralized governance or time-locked changes to provide transparency and allow community oversight.


### `M-01` — Potential Integer Overflow in `antiFarmerExpirationTime`  *(Severity: Medium · Status: Unresolved)*

The `antiFarmerExpirationTime` is stored as a `uint48`. In the `finalizeMigration` function, this value is set by `block.timestamp + antiFarmerDuration`. If `block.timestamp + antiFarmerDuration` exceeds the maximum value of `uint48` (approximately 2.8e14 seconds or ~8921 years from epoch), an integer overflow will occur. This would result in an incorrect, much smaller expiration time, potentially disrupting the intended anti-farmer mechanism and leading to unexpected behavior.

**Recommendation:** Implement a `require` statement to ensure that `block.timestamp + antiFarmerDuration` does not exceed `type(uint48).max`. Alternatively, consider using a larger integer type (e.g., `uint64`) for `antiFarmerExpirationTime` if the intended duration could realistically exceed the `uint48` limit.


### `M-02` — Critical External Dependencies  *(Severity: Medium · Status: Unresolved)*

The `FlapTaxTokenV3` contract relies heavily on external contracts, specifically `ITaxProcessor` and `IDividend`, for its core tax processing and dividend distribution logic. The security and correctness of these external contracts are paramount to the overall system's integrity. If these external contracts contain vulnerabilities, are maliciously implemented, or are controlled by a compromised entity, they could lead to fund loss, incorrect tax calculations, or disruption of dividend distribution.

**Recommendation:** Conduct thorough security audits of the `ITaxProcessor` and `IDividend` contracts. Ensure that their implementations are robust, secure, and align with the expected behavior. Implement strict access control on these external contracts and consider mechanisms to update their addresses safely in case of a vulnerability or upgrade.


### `L-01` — Storage Collision Risk in Upgrades  *(Severity: Low · Status: Unresolved)*

While the contract correctly uses OpenZeppelin's `Initializable` pattern for upgradeability, adding new state variables to the contract in future implementations without careful consideration of storage slot packing, especially with the `PackedPoolState` struct, could lead to storage collisions. If new variables are inserted before existing ones or if the `PackedPoolState` struct's internal layout changes in a way that shifts its slot, it could corrupt existing data.

**Recommendation:** Adhere strictly to OpenZeppelin's upgradeable storage layout guidelines. When adding new state variables, always append them to the end of the contract's storage. For complex structs like `PackedPoolState`, ensure any modifications are backward-compatible or use a dedicated storage gap to prevent future collisions.


### `I-01` — Gas Inefficiency in `_liquidateTax` State Updates  *(Severity: Informational · Status: Unresolved)*

The `_liquidateTax` function reads `poolState` into a local variable `currentPoolState`, modifies it, writes it back to storage (`poolState = currentPoolState`), then reads it again (after the external call), modifies it, and writes it back again. While the multiple reads and writes are part of a robust reentrancy guard, this pattern involves multiple SLOAD and SSTORE operations within a single function call. This could be slightly optimized for gas by consolidating storage writes if the reentrancy guard logic allows for it without compromising security.

**Recommendation:** Review the `_liquidateTax` function to determine if the `poolState` variable can be written to storage fewer times without compromising the reentrancy guard. For example, if the second `currentPoolState = poolState;` read is not strictly necessary for security after the external call, the final `poolState = currentPoolState;` could potentially be combined.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe9bc...7777`](https://bscscan.com/address/0xe9bc5c6a86caa44fd7b469bf3cc7c563e4f77777) |
| **Network** | BNB Chain |
| **Price** | $0.001281 |
| **24h Volume** | $511.1K |
| **Liquidity** | $120.3K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 10d |
| **Top-10 Holders** | 24.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1516 buys / 1033 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa2b1926cb477e92445cf70602f1a7200361f761d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/giggle-mascot-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
