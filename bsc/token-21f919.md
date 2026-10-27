---
token: 妖蝶
ticker: 妖蝶
network: bsc
risk_score: 0
status: low
date: 2026-09-24
---

# 妖蝶 (妖蝶) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-21f919-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with custom tax mechanics, anti-farmer logic, and a multi-state pool system. The contract utilizes OpenZeppelin's upgradeable standards, ensuring a robust foundation for upgradeability and ERC20 compliance. Key strengths include the use of packed storage for gas efficiency and clear state management. However, potential reentrancy and denial-of-service risks exist within the `_liquidateTax` function due to likely external calls to `ITaxProcessor` and `IDividend` (based on imported interfaces and stored addresses), which could lead to critical vulnerabilities if not properly guarded. Additionally, the immutability of critical external contract addresses and significant owner privileges introduce medium-level operational and centralization risks.

> **Final Recommendation:** It is highly recommended to thoroughly review the complete `_liquidateTax` function, specifically focusing on external calls to `ITaxProcessor` and `IDividend`. Implement robust reentrancy guards and ensure the Checks-Effects-Interactions pattern is strictly followed to mitigate potential reentrancy and denial-of-service risks. Consider adding owner-controlled functions to update critical external contract addresses like `taxProcessor` and `dividendContract` to enhance operational flexibility without requiring a full contract upgrade. Evaluate the impact of owner privileges and consider implementing a multi-signature wallet or time-locked governance for critical state changes to reduce centralization risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's battle-tested upgradeable contracts for ERC20, access control, and initialization, which is a strong foundation (7.1 Architecture, 7.2 Code Security). The… |
| **Governance / Economics** | 8/10 | Low | The `OwnableUpgradeable` pattern provides clear access control for critical functions like `startMigration` and `finalizeMigration` (7.3 Access Control, 7.5 Governance). The tokenomics involve… |
| **Upgrades** | 10/10 | Low | The contract correctly implements the OpenZeppelin upgradeable pattern, including `Initializable` and calling `_disableInitializers()` in the constructor (7.7 Upgrades). This ensures proper… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Immutability of Critical External Contract Addresses  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `taxProcessor` and `dividendContract` addresses are set during the `initialize` function and cannot be changed thereafter. This design choice means that if these external contracts need to be updated, replaced due to bugs, vulnerabilities, or changes in business logic, a full contract upgrade of `FlapTaxTokenV3` would be required. This reduces operational flexibility and increases the complexity and risk associated with necessary updates.

**Recommendation:** Consider adding owner-controlled functions (e.g., `setTaxProcessor(address newProcessor)`) to allow the owner to update these critical external contract addresses. Implement a timelock or multi-signature wallet for such changes to provide an additional layer of security and transparency.


### `M-02` — Centralization Risk with Owner Privileges  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `onlyOwner` role has significant control over critical contract state transitions, specifically `startMigration` and `finalizeMigration`. These functions can alter the token's tax behavior and operational state. While common in initial project phases, this level of control by a single entity introduces a centralization risk, as a compromised owner key or a malicious owner could unilaterally change core tokenomics.

**Recommendation:** Evaluate the long-term governance model. For production environments, consider transitioning ownership to a multi-signature wallet (e.g., Gnosis Safe) or a decentralized autonomous organization (DAO) to distribute control and enhance security. Implement a timelock for critical owner actions to provide a window for community review and reaction.


### `M-03` — Potential Reentrancy and Denial of Service in `_liquidateTax`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called on every `_transfer` and is responsible for collecting and potentially distributing tax. While the provided code snippet is truncated, the presence of `taxProcessor` and `dividendContract` addresses, along with imported interfaces `ITaxProcessor` and `IDividend`, strongly suggests that external calls to these contracts occur within the full `_liquidateTax` function. If these external calls are made without proper reentrancy guards (e.g., Checks-Effects-Interactions pattern) or before critical state updates, a malicious external contract could re-enter `FlapTaxTokenV3` and exploit

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function or ensure that all external calls adhere strictly to the Checks-Effects-Interactions pattern. Specifically, all state changes should occur before any external calls. Additionally, consider implementing robust error handling or fallback mechanisms for external calls to prevent denial of service.


### `L-01` — Lack of Event Emission for Critical Parameter Changes  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While `PoolStateChanged` is emitted for state transitions, other critical parameters like `antiFarmerDuration`, `liqExpectedOutputAmount`, `mainPool`, or changes to the `pools` mapping (if such modification functions were implemented) do not emit events. The absence of events for such changes makes it challenging for off-chain monitoring tools, block explorers, and users to track and verify modifications to the contract's operational parameters.

**Recommendation:** Emit events for all significant parameter changes that affect the contract's behavior or tokenomics. This improves transparency, auditability, and allows for easier integration with external monitoring systems.


### `L-02` — Potential for MEV/Front-running on `_liquidateTax` Thresholds  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function's behavior, including state transitions (e.g., `TaxEnforcedAntiFarmer` to `TaxEnforced` or `TaxFree`) and tax collection, is dependent on `block.timestamp` and `balanceOf(address(this))` relative to `liquidationThreshold`. Sophisticated actors (MEV bots) could potentially time their transactions to trigger or avoid certain tax/liquidation events, or even manipulate the `balanceOf(address(this))` by sending tokens just before a liquidation check, to gain an economic advantage.

**Recommendation:** While difficult to fully eliminate, consider if the precise timing of `_liquidateTax` triggers can be made less predictable or if the impact of small manipulations can be minimized. For example, using a time-weighted average for `block.timestamp` or adding a small random delay (if feasible) could reduce predictability. However, this is often a trade-off with design simplicity.


### `I-01` — Hardcoded `maxSupply`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxSupply` is declared as a `constant` with a value of `1e9 ether`. This means the total supply of the token is fixed at deployment and cannot be changed without a contract upgrade. While this is a common and often desired characteristic for ERC20 tokens, it limits future flexibility if the project's tokenomics require adjustments to the total supply.

**Recommendation:** No direct action is required if this is an intentional design choice. However, ensure that the project's long-term tokenomics plan accounts for this immutability. If future flexibility is desired, consider making `maxSupply` a state variable controlled by governance.


### `I-02` — `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` Immutability  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` values are set as `immutable` in the constructor. This design choice means these base liquidation thresholds cannot be modified in future upgrades. While `initialLiquidationThreshold` is set from `START_LIQ_THRESHOLD` and might be mutable, the core immutable values could restrict future flexibility if the underlying economic model needs to adapt to unforeseen market conditions or protocol changes.

**Recommendation:** No direct action is required if this immutability is an intentional design constraint. Ensure that the project's long-term economic model is robust enough to not require changes to these fundamental thresholds. If flexibility is paramount, consider making these configurable state variables, albeit with increased complexity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf609...7777`](https://bscscan.com/address/0xf609e7c374ee82001c3c9834c63d8c8cc6ed7777) |
| **Network** | BNB Chain |
| **Price** | $0.001413 |
| **24h Volume** | $207.9K |
| **Liquidity** | $123.2K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 13d |
| **Top-10 Holders** | 53.8% of supply |
| **Buy / Sell Tax** | 3.0% / 4.6% |
| **24h Transactions** | 2286 buys / 536 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4759a374237b0e0c4da7d627f0ceb06c9bbeedfb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-21f919-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-24*
