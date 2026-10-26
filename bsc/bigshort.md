---
token: BigShort
ticker: SHORT
network: bsc
risk_score: 20
status: low
date: 2026-09-25
---

# BigShort (SHORT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bigshort-bsc)

---

## Audit Summary

The BigShortTokenV1 contract, serving as an upgradeable ERC20 token implementation, integrates a complex tax mechanism and relies heavily on an external protocol registry for configuration. While it employs OpenZeppelin's upgradeable patterns and includes specific reentrancy guards, a significant portion of the core transfer and tax processing logic within the `_update` function was truncated, preventing a full security assessment. This audit identifies several medium-level risks related to external dependencies, upgradeability, and the incomplete view of critical functionality.

> **Final Recommendation:** A comprehensive security review of the complete `_update` function and the `BigShortTaxProcessorV1` contract is essential to fully assess the tax mechanism and potential reentrancy vectors. Strengthen the security posture of the `IProtocolRegistry` and its data integrity, as it is a critical dependency for the token's correct operation. Implement robust operational security procedures for the `controller` address, potentially utilizing a well-secured multisig. For future upgrades, conduct thorough testing and formal verification of storage layout compatibility to mitigate risks associated with upgradeable contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The `BigShortTokenV1` contract demonstrates good technical practices, including the use of OpenZeppelin's upgradeable contracts and custom error handling. A specific reentrancy guard is implemented… |
| **Governance / Economics** | 4/10 | Medium | The economic model incorporates a flexible tax mechanism with configurable buy/sell taxes and a burn mode, validated extensively during initialization (7.4 Economic). The `controller` role is central… |
| **Upgrades** | 2/10 | High | The contract is designed as an upgradeable implementation for a BeaconProxy, leveraging OpenZeppelin's `Initializable` pattern for secure deployment (7.7 Upgrades). The `initialize` function includes… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.7% (≈ permanent lock) |
| **LP Locked** | 99.7% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Reliance on External Protocol Registry for Critical Configuration  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function and overall contract operation heavily depend on the `IProtocolRegistry` for fetching critical configuration data such as `TokenRecord`, `MarketGroup`, `EconomicConfiguration`, and `EngineReservation`. If the `IProtocolRegistry` is compromised, misconfigured, or returns malicious data, it could lead to incorrect token initialization, invalid tax parameters, or an overall broken token state. This introduces a central point of trust and a significant external dependency risk (7.6 External, 7.1 Architecture).

**Recommendation:** Implement robust security measures for the `IProtocolRegistry`, including strong access control, immutable configuration where possible, and thorough validation of data before it's consumed by dependent contracts. Consider adding additional on-chain validation checks within `BigShortTokenV1` for critical parameters fetched from the registry, if feasible, to provide a defense-in-depth approach.


### `M-02` — Incomplete Tax Processing Logic (Truncated Code)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `_update` function, which is central to token transfers and tax application, is truncated. This prevents a full security assessment of the tax mechanism, including potential reentrancy vectors beyond the explicitly mentioned guard, slippage attacks during swaps (if applicable), or incorrect tax calculations. Without the complete implementation of this critical function and the `BigShortTaxProcessorV1` contract, an unknown level of risk remains regarding the core economic and security logic (7.2 Code Security, 7.4 Economic).

**Recommendation:** Provide the complete source code for the `_update` function and the `BigShortTaxProcessorV1` contract for a comprehensive security audit. A full review is necessary to identify and mitigate any vulnerabilities related to tax calculation, external calls, and reentrancy within the entire transfer process.


### `M-03` — Upgradeability Risks (General)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). As an upgradeable contract (BeaconProxy implementation), future upgrades must meticulously manage storage layout to prevent collisions or data corruption. While the current contract uses OpenZeppelin's `ERC20Upgradeable` and `Initializable` patterns, the inherent complexity of upgradeable systems introduces a persistent risk if new state variables are added or existing ones are reordered incorrectly in subsequent versions. This could lead to critical data loss or unexpected contract behavior upon upgrade (7.7 Upgrades).

**Recommendation:** Adhere strictly to OpenZeppelin's upgradeability guidelines for storage layout. When performing upgrades, conduct thorough testing in a staging environment, including migration simulations. Consider using tools like 'hardhat-upgrades' or 'openzeppelin-upgrades' to assist in detecting storage layout incompatibilities during development and deployment. Formal verification of storage compatibility for each upgrade is highly recommended.


### `L-01` — Centralization Risk via `controller` Role  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `controller` address holds significant power within the contract, including the ability to bind the main trading pair (`bindMainPair`) and enable external trading (`enableExternalTrading`). While this is a common design pattern for operational control, it introduces a centralization risk. A compromise of the `controller`'s private key or its controlling mechanism (e.g., a multisig with too few signers) could lead to critical operational disruptions or malicious actions affecting the token's trading capabilities (7.3 Access Control, 7.8 Operations).

**Recommendation:** Ensure the `controller` address is secured with the highest possible operational security standards, such as a robust multisignature wallet with a sufficient number of signers and strict key management practices. Consider implementing time-locks for critical administrative actions to provide a window for intervention in case of a compromise.


### `I-01` — Specific Reentrancy Guard in `_update` for Tax Processing  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_update` function includes a reentrancy guard (`_processingExternalTax`) specifically designed to prevent re-entry during tax processing initiated by the `taxProcessor`. This is a good practice for the identified scenario, ensuring that internal state changes related to tax collection are not interrupted or manipulated by re-entrant calls from the `taxProcessor` (7.2 Code Security).

**Recommendation:** While this specific guard is well-placed, ensure that the `BigShortTaxProcessorV1` contract itself is also thoroughly audited for reentrancy vulnerabilities, especially if it makes external calls that could re-enter the token contract in different contexts (e.g., via `transfer` or `transferFrom` to an attacker-controlled contract). A holistic view of reentrancy across all interacting contracts is crucial.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7c46...bbbb`](https://bscscan.com/address/0x7c46508f0937a0c8fb4c34fa20fef70ec9a6bbbb) |
| **Network** | BNB Chain |
| **Price** | $0.0002909 |
| **24h Volume** | $451.6K |
| **Liquidity** | $175.6K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 69.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1556 buys / 3376 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x949bcb28d249e7a2aee90ca1eb1d44806e2139a1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bigshort-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
