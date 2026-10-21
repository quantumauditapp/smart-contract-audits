---
token: 孙小圣
ticker: 孙小圣
network: bsc
risk_score: 37
status: medium
date: 2026-09-06
---

# 孙小圣 (孙小圣) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-21a384-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and a state-based lifecycle. It leverages OpenZeppelin's upgradeable patterns for robust architecture. However, a critical portion of the `_liquidateTax` function was truncated in the provided source, preventing a full security assessment of the core tax processing and fund management. This, combined with high centralization, contributes to a Medium overall risk level.

> **Final Recommendation:** Prioritize providing the complete and verified source code for all contract functions, especially `_liquidateTax`, to enable a comprehensive security audit. Address the high centralization by considering a multi-signature wallet for the owner role or exploring a transition to a decentralized governance model for critical administrative functions. Ensure all declared variables and imported interfaces are actively utilized within the contract logic, or remove any unused components to enhance clarity and reduce the attack surface.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements an upgradeable ERC20 token with a complex state machine for tax enforcement and migration. It leverages OpenZeppelin's battle-tested upgradeable contracts, ensuring a solid… |
| **Governance / Economics** | 5/10 | Medium | The economic model incorporates dynamic buy/sell taxes and an anti-farmer mechanism, managed through distinct pool states. The tax rates are applied using a standard basis point calculation… |
| **Upgrades** | 8/10 | Low | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` pattern, correctly disabling initializers in the constructor and using the `initializer` modifier (7.7 Upgrades).… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `C-01` — Incomplete Code Provided for Audit  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated, specifically the condition `taxAmount >= currentPoolState.liqu...`. This function is critical as it handles state transitions, tax processing, and potentially external calls (e.g., to `taxProcessor` or `dividendContract`). Without the complete code, it is impossible to fully assess the security and economic implications of the tax liquidation mechanism, including potential reentrancy, denial-of-service, or incorrect handling of accumulated funds. (7.2 Code Security, 7.4 Economic)

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function and any other truncated sections to allow for a comprehensive security review.


### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The contract relies heavily on `OwnableUpgradeable` for critical operations. The owner has exclusive control over initiating and finalizing migration states (`startMigration`, `finalizeMigration`), which directly impacts the token's tax mechanisms and transfer rules. The owner also minted the entire `maxSupply` during initialization. This high degree of centralization introduces a single point of failure and trust, as a compromised owner key could lead to significant economic manipulation or a rug pull scenario. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet for ownership or transitioning to a decentralized governance model (e.g., DAO) for critical functions to reduce the risk associated with a single point of control.


### `M-01` — Unused or Truncated External Dependencies and Variables  *(Severity: Medium · Status: Unresolved)*

Several imported interfaces (`ITaxProcessor`, `IDividend`) and state variables (`liqExpectedOutputAmount`, `initialLiquidationThreshold`, `metaURI`, `dividendContract`, `taxProcessor`) are initialized but not used within the provided code snippet. While some usage might be in the truncated `_liquidateTax` function, their absence in the visible logic suggests either dead code, incomplete implementation, or critical functionality being hidden. This makes it difficult to understand the full system's behavior and potential external interaction risks. (7.1 Architecture, 7.6 External)

**Recommendation:** Ensure all declared variables and imported interfaces are actively used and their interactions are fully implemented and visible. If they are intended for future use, document their purpose clearly. If they are dead code, remove them to improve clarity and reduce attack surface.


### `L-01` — Potential Truncation Risk for `antiFarmerExpirationTime`  *(Severity: Low · Status: Unresolved)*

The `antiFarmerExpirationTime` variable is declared as `uint48`. While `uint48` provides a large enough range for typical `block.timestamp` values and `antiFarmerDuration` (up to approximately 2.78 million years), there is a theoretical risk of truncation if `block.timestamp + antiFarmerDuration` were to exceed `2^48 - 1`. Although highly improbable in practical scenarios, using a larger type like `uint64` for time-related variables is generally safer and more robust against extreme or long-term values. (7.2 Code Security)

**Recommendation:** Consider using `uint64` for `antiFarmerExpirationTime` to align with `taxExpirationTime` and eliminate any theoretical truncation risk, even if practically negligible.


### `L-02` — Ambiguity in Pool Tax Application Logic  *(Severity: Low · Status: Unresolved)*

The `_getTaxWithPoolState` function applies tax logic differently based on the `PoolState`. In `PoolState.TaxEnforcedAntiFarmer`, it checks `pools[from]` or `pools[to]`, applying tax if either address is a configured pool. In `PoolState.TaxEnforced`, it specifically checks `from == mainPool` or `to == mainPool`. This distinction, while potentially intentional, could lead to confusion or unintended tax application if the `mainPool` is not the only address intended to be taxed in the `TaxEnforced` state, or if the `pools` mapping is not managed carefully. (7.1 Architecture, 7.4 Economic)

**Recommendation:** Clearly document the intended behavior and rationale behind the differing tax application logic for `PoolState.TaxEnforcedAntiFarmer` and `PoolState.TaxEnforced`. Ensure that the `pools` mapping and `mainPool` variable are managed consistently with these rules.


### `I-01` — Packed Storage for `PackedPoolState`  *(Severity: Informational · Status: Unresolved)*

The `PackedPoolState` struct uses packed storage (`uint8`, `uint16`, `uint16`, `bool`, `uint96`, `uint64`, `uint48`) to optimize gas costs by fitting multiple variables into a single storage slot. While efficient, this design requires careful consideration for future upgrades. Any change in the order or size of these variables in a subsequent implementation could lead to storage collisions and data corruption if not handled meticulously, potentially breaking the contract's state. (7.7 Upgrades)

**Recommendation:** When upgrading the contract, ensure that the `PackedPoolState` struct's layout remains identical or that any changes are managed with extreme care to prevent storage collisions. Thorough testing of upgrade scenarios is crucial.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbb87...7777`](https://bscscan.com/address/0xbb87378b58894338f0937b9691a5a6dc3a5a7777) |
| **Network** | BNB Chain |
| **Price** | $0.000217 |
| **24h Volume** | $151.0K |
| **Liquidity** | $47.8K |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 53.6% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 1603 buys / 2621 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x38fd5142c556b5016e48edba9eee48dbc7c3fb72)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-21a384-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
