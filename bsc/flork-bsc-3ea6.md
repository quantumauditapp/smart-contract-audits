---
token: FLORK
ticker: FLORK
network: bsc
risk_score: 0
status: low
date: 2026-09-04
---

# FLORK (FLORK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flork-bsc-3ea6)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and a multi-state pool system. The audit identified a critical logic error in the calculation of `taxExpirationTime` during state transitions, which could lead to unintended tax durations. Other findings include potential integer overflow for `antiFarmerExpirationTime`, a moderate reentrancy risk in the `_liquidateTax` function (pending full code review), and significant centralization of control with the contract owner. The contract utilizes OpenZeppelin's upgradeable standards and struct packing for gas efficiency.

> **Final Recommendation:** Address the critical logic error in `taxExpirationTime` calculation immediately to ensure the tax mechanism operates as intended. Implement robust validation and consider multi-signature control for critical external contract addresses (`taxProcessor`, `dividendContract`) to mitigate centralization and dependency risks. Thoroughly review the `_liquidateTax` function's external interactions once the full code is available to confirm reentrancy safeguards and ensure proper handling of collected taxes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract employs OpenZeppelin's upgradeable ERC20 standards, ensuring a robust foundation (7.1 Architecture). Struct packing is used for `PackedPoolState`, optimizing gas usage. However, a… |
| **Governance / Economics** | 8/10 | Low | The contract's economic model is driven by a dynamic tax mechanism and a multi-state pool system, with `maxSupply` minted to the owner at initialization (7.4 Economic). The `OwnableUpgradeable`… |
| **Upgrades** | 9/10 | Low | The contract is designed for upgradeability using OpenZeppelin's `Initializable` pattern, with `_disableInitializers()` correctly called in the constructor (7.7 Upgrades). `immutable` variables are… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 14.4% |
| **Top-3 Unlocked** | 35.4% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Potential `uint48` Overflow for `antiFarmerExpirationTime`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In `finalizeMigration`, `antiFarmerExpirationTime` is set to `uint48(block.timestamp + antiFarmerDuration)`. While `block.timestamp` is currently within `uint48` limits, `antiFarmerDuration` could be set by the owner to a value large enough that `block.timestamp + antiFarmerDuration` exceeds `type(uint48).max` (approximately 2.8e14). If this occurs, the value will silently truncate, leading to an `antiFarmerExpirationTime` that is significantly earlier than intended, potentially prematurely ending the anti-farmer period.

**Recommendation:** Consider using a larger data type (e.g., `uint64` or `uint256`) for `antiFarmerExpirationTime` to prevent potential overflow, especially if `antiFarmerDuration` is expected to be very long. Alternatively, implement a `require` statement to ensure `block.timestamp + antiFarmerDuration` does not exceed `type(uint48).max` before assignment.


### `M-02` — Reentrancy Risk in `_liquidateTax` (Partial Code)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called during `_transfer`. While the `poolState` is updated *before* potential external calls (implied by the `taxProcessor` and `dividendContract` addresses), the full implementation of the `_liquidateTax` function is truncated. If the truncated portion involves external calls to `taxProcessor` or `dividendContract` that transfer funds or can re-enter the token contract, there is a moderate reentrancy risk. An attacker could potentially re-enter the contract and manipulate `balanceOf(address(this))` or other state before the external call completes, leading to unexpected behavior or dou

**Recommendation:** Complete the audit of the `_liquidateTax` function's full implementation, paying close attention to any external calls. Ensure that all state changes related to `taxAmount` or internal balances are completed *before* any external calls are made. Implement reentrancy guards (e.g., OpenZeppelin's `ReentrancyGuard`) if external calls are made and critical state is modified after them, or if the external contracts themselves are untrusted.


### `M-03` — Critical Logic Error in `taxExpirationTime` Calculation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `finalizeMigration` function incorrectly calculates `currentPoolState.taxExpirationTime = uint64(currentPoolState.taxExpirationTime + block.timestamp);`. In `initialize`, `taxExpirationTime` is set to `uint64(params.taxDuration)`, meaning it initially holds a duration value. Adding `block.timestamp` (an absolute timestamp) to this duration results in an incorrect future timestamp, potentially making the tax active for an unintended and excessively long period, or causing unexpected behavior in tax expiration logic.

**Recommendation:** If `taxExpirationTime` is intended to be an absolute timestamp, it should be initialized as `block.timestamp + params.taxDuration` in `initialize`. In `finalizeMigration`, if a new duration is to be added, it should be `block.timestamp + newDuration` or `currentPoolState.taxExpirationTime + newDuration` (if `currentPoolState.taxExpirationTime` is already an absolute timestamp). Ensure consistent interpretation of `taxExpirationTime` as either a duration or an absolute timestamp throughout the c…


### `L-01` — Centralization Risk with Owner Privileges  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes `OwnableUpgradeable`, granting significant control to a single owner address. The owner can unilaterally initiate and finalize migration states (`startMigration`, `finalizeMigration`), which directly impacts the token's tax rates and operational phases. This high degree of centralization means the project's security and integrity heavily depend on the owner's trustworthiness and the security of their private key.

**Recommendation:** Consider migrating ownership to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and reduce the risk of a single point of failure. For critical operations, implement a time-lock mechanism to allow users to react to pending changes.


### `L-02` — Reliance on External Contracts without Robust Checks  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract relies on external `taxProcessor` and `dividendContract` addresses, which are set during initialization. Beyond checking for `address(0)`, there are no further validations (e.g., interface checks, trusted registry checks) to ensure these addresses point to legitimate, non-malicious, or correctly implemented contracts. A compromised or malicious external contract could potentially disrupt the token's tax collection or dividend distribution mechanisms.

**Recommendation:** Implement more robust validation for external contract addresses. Consider adding checks to ensure the addresses implement the expected interfaces (e.g., `ITaxProcessor`, `IDividend`). If possible, use a trusted registry or allow only pre-approved addresses to be set. For critical external contracts, consider making them immutable after initialization or requiring a multi-sig for updates.


### `I-01` — Inconsistent Use of `pools` and `mainPool` for Tax Calculation  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_getTaxWithPoolState` function applies tax logic differently based on the `PoolState`. For `PoolState.TaxEnforcedAntiFarmer`, it checks `pools[from]` and `pools[to]`. However, for `PoolState.TaxEnforced`, it specifically checks `from == mainPool` and `to == mainPool`. This inconsistency, while potentially intentional, could lead to confusion or unexpected tax behavior if the distinction between `pools` (a mapping of multiple addresses) and `mainPool` (a single address) is not clearly understood and documented.

**Recommendation:** Clearly document the rationale behind the different tax application logic for `PoolState.TaxEnforcedAntiFarmer` versus `PoolState.TaxEnforced`. Ensure that this distinction is well-understood by developers and users to prevent misinterpretations of the token's tax mechanics.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf405...7777`](https://bscscan.com/address/0xf40592daacb3e5abf358789f5688c0b4f64d7777) |
| **Network** | BNB Chain |
| **Price** | $0.02015 |
| **24h Volume** | $2.59M |
| **Liquidity** | $591.3K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 6d |
| **Top-10 Holders** | 27.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4416 buys / 3094 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x9793a9cbb04f781433254e4530398107e6a8dcee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flork-bsc-3ea6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
