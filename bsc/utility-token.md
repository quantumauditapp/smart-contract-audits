---
token: utility token
ticker: UTILITY
network: bsc
risk_score: 54
status: high
date: 2026-08-13
---

# utility token (UTILITY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/utility-token-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms, anti-farmer features, and a state-based lifecycle. The contract utilizes OpenZeppelin's upgradeable standards, ensuring a robust foundation for upgradeability and standard ERC20 functionalities. Key features include a packed struct for gas efficiency and a reentrancy guard for tax processing. However, the audit identified a high-severity integer overflow vulnerability in expiration time calculations, medium-severity concerns regarding the immutability of critical external dependencies and centralized control over state transitions, and a low-severity issue related to gas inefficiency in tax liquidation. Informational findings highlight potential storage collision risks in future upgrades.

> **Final Recommendation:** Address the identified integer overflow vulnerability by implementing robust checks or using `SafeCast` to prevent incorrect expiration time calculations. Enhance the flexibility and security of critical external dependencies by implementing `onlyOwner` setter functions, ideally protected by a timelock, to allow for updates without requiring a full contract upgrade. Consider decentralizing control over critical state transitions by implementing a multi-signature wallet for the owner or introducing a timelock for sensitive operations. Evaluate the gas efficiency of the `_liquidateTax` function and explore alternative, less frequent liquidation mechanisms if feasible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 and access control modules, providing a solid architectural foundation (7.1 Architecture). It employs `SafeERC20` for external token… |
| **Governance / Economics** | 3/10 | High | The contract's economic model relies on dynamic tax rates and state transitions managed by the owner (7.4 Economic, 7.5 Governance). The owner has centralized control over critical state changes like… |
| **Upgrades** | 3/10 | High | The contract is designed as an upgradeable implementation using OpenZeppelin's `Initializable` pattern, with `_disableInitializers()` correctly called in the constructor (7.7 Upgrades). However, the… |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Integer Overflow in Expiration Time Calculations  *(Severity: High · Status: Unresolved)*

The `taxExpirationTime` (uint64) and `antiFarmerExpirationTime` (uint48) are updated by adding `block.timestamp` (uint256) and `antiFarmerDuration` (uint256) respectively. When the sum exceeds the maximum value of the target smaller type (uint64 or uint48), an integer overflow will occur due to implicit truncation during the cast. This can lead to expiration times being set incorrectly, potentially causing the tax or anti-farmer periods to end prematurely or extend indefinitely, disrupting the contract's economic model.

**Recommendation:** Ensure that the sum of `currentPoolState.taxExpirationTime + block.timestamp` and `block.timestamp + antiFarmerDuration` does not exceed `type(uint64).max` and `type(uint48).max` respectively before casting. Consider using `SafeCast` from OpenZeppelin or explicitly checking for overflow conditions and reverting if the sum is too large. Alternatively, use a larger data type (e.g., `uint256`) for these expiration times if their potential values can exceed `uint64` or `uint48` limits.


### `M-01` — Immutability of Critical External Dependencies  *(Severity: Medium · Status: Unresolved)*

The `taxProcessor` and `dividendContract` addresses are set only during the `initialize` function and are not mutable thereafter. These are critical external dependencies for the contract's core functionality (tax processing and dividend distribution). If these external contracts need to be updated (e.g., due to bug fixes, security vulnerabilities, or feature upgrades), the `FlapTaxTokenV3` contract itself would require an upgrade. This introduces rigidity and increases the operational complexity and risk associated with updating these components.

**Recommendation:** Implement `onlyOwner` setter functions for `taxProcessor` and `dividendContract` to allow the owner to update these addresses. To mitigate risks associated with immediate changes, consider adding a timelock mechanism to these setter functions, providing a delay before changes take effect and allowing for community review or emergency intervention.


### `M-02` — Centralized Control over State Transitions  *(Severity: Medium · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control critical state changes of the token's lifecycle (e.g., transitioning from `BondingCurve` to `Migrating` and then to `TaxEnforcedAntiFarmer`), are protected by the `onlyOwner` modifier. This grants a single address absolute control over these significant protocol changes. A compromise of the owner's private key could lead to unauthorized or malicious state transitions, potentially disrupting the token's intended economic behavior and user trust.

**Recommendation:** Consider implementing a multi-signature wallet for the contract owner to distribute control among multiple trusted parties. For highly sensitive operations, integrate a timelock mechanism that introduces a delay before state changes take effect, allowing for community oversight and potential emergency cancellation if a malicious or erroneous action is initiated.


### `L-01` — Gas Inefficiency and External Dependency in `_liquidateTax`  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function is called on every `_transfer` operation where the recipient (`to`) is the `mainPool`. This function performs several state checks, potentially updates the `poolState` storage, and makes an external call to `_processTax` on the `taxProcessor` contract. Calling this logic, including an external call, on every such transfer can lead to increased gas costs for users interacting with the `mainPool` and introduces a direct dependency on the `taxProcessor`'s availability and execution cost for basic token transfers.

**Recommendation:** Evaluate the necessity of triggering `_liquidateTax` on every transfer to the `mainPool`. Consider alternative mechanisms such as: 1) a periodic liquidation function that can be called by anyone (with incentives) or a trusted keeper, 2) a threshold-based liquidation that only triggers when the collected tax amount reaches a certain level, or 3) batching tax processing to reduce the frequency of external calls.


### `I-01` — Potential for Storage Collisions in `PackedPoolState` (Upgradeability Concern)  *(Severity: Informational · Status: Unresolved)*

The `PackedPoolState` struct uses tightly packed variables (`uint8`, `uint16`, `uint96`, `uint64`, `uint48`) to optimize gas usage. While efficient, modifying the order, size, or adding/removing variables within this struct in a future upgrade can lead to storage collisions if not handled with extreme care and strict adherence to UUPS storage layout rules. Such collisions could corrupt the contract's state, leading to unexpected behavior or loss of funds.

**Recommendation:** When planning future upgrades, strictly follow the UUPS storage layout guidelines. Any new state variables should always be appended to the end of the contract's storage. Avoid modifying existing structs, especially packed ones, in place. If changes to `PackedPoolState` are absolutely necessary, consider migrating to a new struct or using a proxy-specific storage slot for new data, ensuring no existing data is overwritten.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xede0...7777`](https://bscscan.com/address/0xede00776439f9c49c592e43eee34777a51847777) |
| **Network** | BNB Chain |
| **Price** | $0.003841 |
| **24h Volume** | $289.5K |
| **Liquidity** | $32.9K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 0h |
| **Top-10 Holders** | 17.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1388 buys / 1214 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xcd27d0f6c4d64c1d8ea6b5ce98a532dfbf720ef5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/utility-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
