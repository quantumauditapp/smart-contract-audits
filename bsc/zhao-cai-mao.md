---
token: Zhao Cai Mao
ticker: 招财猫
network: bsc
risk_score: 4
status: low
date: 2026-09-25
---

# Zhao Cai Mao (招财猫) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zhao-cai-mao-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and multiple operational states. It leverages OpenZeppelin's upgradeable contracts for a robust foundation. However, a critical portion of the `_liquidateTax` function, central to the token's economic logic, is truncated in the provided source code, preventing a full security assessment. The contract also exhibits centralized control by the owner and relies on external contracts for tax processing and dividends, introducing additional risks.

> **Final Recommendation:** Prioritize providing the complete and verified source code for the `_liquidateTax` function to enable a comprehensive security assessment of the token's core economic logic. Evaluate the security of the external `taxProcessor` and `dividendContract` dependencies through dedicated audits. Consider decentralizing critical administrative functions currently controlled by the owner, potentially through a multi-signature wallet or a time-locked governance mechanism, to mitigate single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes OpenZeppelin's upgradeable standards, including `Initializable`, `ERC20Upgradeable`, `ERC20PermitUpgradeable`, and `OwnableUpgradeable`, demonstrating a solid foundation for… |
| **Governance / Economics** | 7/10 | Low | The token implements a dynamic tax mechanism with various `PoolState`s and time-based transitions, managed by the contract owner. This centralized control allows the owner to initiate migration… |
| **Upgrades** | 9/10 | Low | The contract correctly uses OpenZeppelin's UUPS proxy pattern, inheriting `Initializable` and calling `_disableInitializers` in the constructor, along with the `initializer` modifier for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `OwnableUpgradeable` pattern grants significant control to the contract owner. Functions such as `startMigration` and `finalizeMigration` allow the owner to unilaterally change the contract's `PoolState`, which directly impacts tax rates and transfer restrictions. This introduces a single point of failure and a high trust assumption on the owner, who could potentially manipulate the system or be compromised.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or a time-locked governance mechanism for critical operations to reduce centralization risk and enhance security. For less critical functions, a role-based access control (RBAC) system could be explored.


### `M-02` — External Contract Dependencies (TaxProcessor, DividendContract)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract relies on external `taxProcessor` and `dividendContract` addresses, which are set during initialization. The `_liquidateTax` function (implied by its name and context) likely interacts with these contracts to process collected taxes and distribute dividends. The security and integrity of these external contracts are paramount to the overall system's safety. A vulnerability or malicious behavior in `taxProcessor` or `dividendContract` could compromise funds or disrupt the token's functionality.

**Recommendation:** Conduct thorough security audits of the `taxProcessor` and `dividendContract` implementations. Implement robust input validation and consider re-entrancy guards if external calls are made from `_liquidateTax` to these contracts, especially if they handle significant value.


### `M-03` — Incomplete `_liquidateTax` Function Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_liquidateTax` function is truncated, specifically the critical part that handles the actual liquidation of collected tax and potentially further state transitions based on `liquidationThreshold`. This prevents a full security assessment of the token's core economic mechanism, which could harbor unknown vulnerabilities related to fund handling, state transitions, or external interactions.

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function to enable a comprehensive and accurate security audit of this critical component.


### `L-01` — Potential for Front-Running State Transitions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function modifies the `poolState` based on `block.timestamp` (e.g., `taxExpirationTime`, `antiFarmerExpirationTime`). Since `_liquidateTax` is called on every `_transfer`, users can observe pending state changes in the mempool. An attacker could front-run transactions to execute transfers under a more favorable tax regime (e.g., before taxes are enforced or after they expire) or to avoid restrictions, potentially leading to minor economic imbalances.

**Recommendation:** While inherent to time-based logic on public blockchains, consider if the impact of front-running on state transitions is acceptable. For critical state changes, a more robust, multi-step, or time-locked process might be considered, though this adds complexity and may not be necessary given the current design.


### `I-01` — Immutable Variables in Upgradeable Contract Constructor  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` variables are declared as `immutable` and initialized in the constructor. In an upgradeable contract using the UUPS pattern, constructor logic is executed only once when the proxy contract is deployed, not when the implementation is deployed or upgraded. This means these `immutable` variables are correctly stored in the proxy's storage, ensuring they persist across upgrades.

**Recommendation:** No action required. This is a good practice for defining constants that should not change across upgrades in an upgradeable contract.


### `I-02` — Packed Storage for `PackedPoolState`  *(Severity: Informational · Status: Resolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PackedPoolState` struct uses tightly packed data types (`uint8`, `uint16`, `bool`, `uint96`, `uint64`, `uint48`) to optimize storage usage. This reduces the number of storage slots required, leading to lower gas costs for reading and writing these state variables, which is a good practice for gas efficiency.

**Recommendation:** No action required. This is a good practice for gas optimization and efficient state management.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x975f...7777`](https://bscscan.com/address/0x975faed559b45feb8a5c5ceb940e614302947777) |
| **Network** | BNB Chain |
| **Price** | $0.001885 |
| **24h Volume** | $332.8K |
| **Liquidity** | $135.1K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 17d |
| **Top-10 Holders** | 21.6% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 4099 buys / 2098 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb574b9a4ac85a588e66f4cb8fa4edf30ca066172)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zhao-cai-mao-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
