---
token: PIZZA
ticker: PIZZA
network: bsc
risk_score: 20
status: low
date: 2026-08-20
---

# PIZZA (PIZZA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pizza-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and multiple pool states. It leverages OpenZeppelin's upgradeable contracts for security and maintainability. The audit identified a critical logic error in tax expiration time calculation, significant owner centralization, and potential truncation issues in packed storage. While reentrancy guards are present for tax processing, the reliance on external contracts and the immutability of critical parameters pose operational risks. Recommendations focus on correcting the logic, enhancing decentralization, and improving transparency.

> **Final Recommendation:** Address the critical logic error in `taxExpirationTime` calculation to ensure correct tax durations. Implement direct setter functions for critical external contract addresses and parameters, guarded by `onlyOwner` or a multi-signature wallet, to enhance operational flexibility and reduce the need for full contract upgrades in case of dependency changes or compromises. Carefully review the sizing of `liquidationThreshold` within `PackedPoolState` to prevent potential truncation issues with large `uint256` values.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | 7.1 Architecture: The contract utilizes a well-structured upgradeable ERC20 pattern from OpenZeppelin, which is a strong foundation. The `PackedPoolState` struct is an efficient design choice for… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic: The token implements a flexible tax system with different pool states and anti-farmer durations. The `maxSupply` is minted to the initializer, establishing initial distribution.… |
| **Upgrades** | 9/10 | Low | 7.7 Upgrades: The contract correctly uses OpenZeppelin's `Initializable` pattern, enabling secure upgrades. This allows for future enhancements and bug fixes without redeploying the entire system.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 34.7% |
| **Top-3 Unlocked** | 69.5% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Incorrect `taxExpirationTime` Initialization Logic  *(Severity: High · Status: Unresolved)*

The `taxExpirationTime` field in `PackedPoolState` is initialized with `uint64(params.taxDuration)` in the `initialize` function. Subsequently, in `finalizeMigration`, it is updated by adding `block.timestamp` to its current value (`currentPoolState.taxExpirationTime + block.timestamp`). This implies `params.taxDuration` is treated as an absolute timestamp during initialization and then as a duration during migration finalization. This inconsistent logic will result in an incorrect `taxExpirationTime` that is significantly longer than intended, leading to prolonged tax enforcement.

**Recommendation:** Ensure consistent interpretation of `params.taxDuration`. If `params.taxDuration` is intended as a duration, `taxExpirationTime` should be initialized as `uint64(block.timestamp + params.taxDuration)` in the `initialize` function. The `finalizeMigration` function should then only update the state and `antiFarmerExpirationTime` as needed, or recalculate `taxExpirationTime` based on `block.timestamp` and the intended duration.


### `H-02` — Owner Centralization and Immutability of Critical Parameters  *(Severity: High · Status: Unresolved)*

The owner has significant centralized control over the token's core mechanics through `startMigration` and `finalizeMigration`, which dictate the `PoolState` and tax enforcement. Furthermore, several critical external contract addresses (`taxProcessor`, `v2Router`, `quoteToken`, `mainPool`, `dividendContract`) and parameters (`antiFarmerDuration`, `liqExpectedOutputAmount`) are set only during initialization and lack direct setter functions. This immutability creates a high operational risk, as these dependencies cannot be updated or replaced without a full contract upgrade if they become compromised, deprecated, or require changes.

**Recommendation:** Consider implementing `onlyOwner` (or multi-signature) protected setter functions for critical external contract addresses and configurable parameters. This would allow for greater flexibility and responsiveness to changes in the ecosystem or security incidents without requiring a full contract upgrade. Clearly document the owner's responsibilities and the implications of these centralized controls.


### `M-01` — Potential Truncation in `PackedPoolState` Fields  *(Severity: Medium · Status: Unresolved)*

The `liquidationThreshold` field within the `PackedPoolState` struct is defined as `uint96`, while the initial values `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` are `uint256`. If `START_LIQ_THRESHOLD` (or any value assigned to `liquidationThreshold`) exceeds the maximum value of `uint96` (`2^96 - 1`), it will be truncated. This could lead to a smaller effective liquidation threshold than intended, potentially affecting the tax liquidation mechanism and economic stability.

**Recommendation:** Ensure that `START_LIQ_THRESHOLD` and `MIN_LIQ_THRESHOLD` are within the bounds of `uint96` or explicitly cast them with a `require` check to prevent truncation. Alternatively, consider increasing the size of `liquidationThreshold` to `uint256` if the intended values can exceed `uint96` max, though this would increase storage costs.


### `L-01` — Reliance on External `ITaxProcessor` Contract  *(Severity: Low · Status: Unresolved)*

The `_processTax` function makes an external call to the `taxProcessor` contract to handle collected tax funds. While a reentrancy guard (`notLiquidating`) is in place for this specific call, the overall security and correctness of the `FlapTaxTokenV3` contract are highly dependent on the implementation and trustworthiness of the `ITaxProcessor` contract. A bug, vulnerability, or malicious logic within `ITaxProcessor` could lead to the loss or misuse of collected tax funds.

**Recommendation:** Thoroughly audit the `ITaxProcessor` contract to ensure its security and intended functionality. Implement robust monitoring for the `taxProcessor` address and its behavior. Consider adding mechanisms for the owner to pause tax processing or update the `taxProcessor` address in emergencies (as suggested in H-02).


### `I-01` — Lack of Event Emission for Critical Parameter Initialization  *(Severity: Informational · Status: Unresolved)*

Several critical parameters, including `v2Router`, `quoteToken`, `antiFarmerDuration`, `mainPool`, `liqExpectedOutputAmount`, `taxProcessor`, and `dividendContract`, are set during the `initialize` function but no corresponding events are emitted. While these parameters are immutable after initialization, emitting events for their initial values would significantly improve transparency and allow off-chain monitoring systems to track the contract's configuration from deployment.

**Recommendation:** Emit events for all critical parameters set during the `initialize` function. For example, `event ConfigUpdated(address indexed v2Router, address indexed taxProcessor, uint256 antiFarmerDuration, ...);`.


### `I-02` — Unused State Variables  *(Severity: Informational · Status: Unresolved)*

The state variables `dividendContract`, `v2Router`, `quoteToken`, and `liqExpectedOutputAmount` are declared and initialized in the contract but are not used in any of the provided functions. This might indicate incomplete functionality, placeholder variables for future development, or an oversight.

**Recommendation:** Review the purpose of these unused variables. If they are intended for future functionality, consider adding comments to clarify their role. If they are no longer needed, remove them to reduce contract size and improve clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8554...7777`](https://bscscan.com/address/0x8554d38b95e4f7ca11d391008627df30b2b07777) |
| **Network** | BNB Chain |
| **Price** | $0.0006199 |
| **24h Volume** | $239.2K |
| **Liquidity** | $103.7K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 18d |
| **Top-10 Holders** | 31.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 937 buys / 687 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe5380b1848e71cbfcd1974d92bd4b76659c67534)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pizza-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
