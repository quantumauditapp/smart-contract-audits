---
token: Max Sister
ticker: LILY
network: bsc
risk_score: 33
status: low
date: 2026-09-03
---

# Max Sister (LILY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/max-sister-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and state transitions. The contract leverages OpenZeppelin's upgradeable contracts and includes features like anti-farmer protection and tax liquidation. While the architecture is generally sound and follows good practices for upgradeability, potential reentrancy risks in the tax liquidation logic (due to truncated code), significant owner privileges, and variable gas costs for users interacting with the main pool warrant attention. The overall risk level is assessed as Medium.

> **Final Recommendation:** It is strongly recommended to complete the audit of the full `_liquidateTax` function to ensure no reentrancy vulnerabilities exist, especially concerning external calls to `taxProcessor` and `dividendContract`. Consider implementing a multi-signature wallet or a time-lock for critical owner-controlled functions to mitigate centralization risks. Additionally, thoroughly test the gas implications of the `_liquidateTax` function being called on every transfer to the main pool to ensure a predictable user experience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates a solid technical foundation (7.1 Architecture) by utilizing OpenZeppelin's upgradeable ERC20 and access control modules, ensuring standard compliance and security patterns.… |
| **Governance / Economics** | 8/10 | Low | The contract's economic model (7.4 Economic) is based on dynamic tax rates and liquidation thresholds, which are configurable during initialization. The `owner` (7.3 Access Control) holds significant… |
| **Upgrades** | 5/10 | Medium | The contract is designed as an upgradeable proxy using the UUPS pattern (7.7 Upgrades), leveraging OpenZeppelin's `Initializable` and `ERC20Upgradeable` modules. The constructor correctly calls… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Potential Reentrancy Risk in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function collects tax amounts and likely performs external calls to `ITaxProcessor` and `IDividend` contracts for distribution, as indicated by the contract's imports and the function's purpose. The provided code snippet for `_liquidateTax` is truncated, preventing a full analysis. Without proper implementation of the Checks-Effects-Interactions pattern and robust reentrancy guards (beyond the `notLiquidating` flag, whose full usage is unknown), external calls within this function could be vulnerable to reentrancy attacks, allowing an attacker to drain funds or manipulate contract state.

**Recommendation:** Provide the complete source code for the `_liquidateTax` function for a thorough review. Ensure that all external calls are made after all state changes have been applied (Effects) and that a reentrancy guard (like the `notLiquidating` flag) is correctly implemented to prevent re-entry during external calls. Consider using OpenZeppelin's `ReentrancyGuard` or a similar pattern.


### `M-01` — Centralization Risk with Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `owner` role has significant control over critical contract functions, including `startMigration` and `finalizeMigration`. These functions directly control the `PoolState` transitions, which dictate the token's tax rates and anti-farmer mechanisms. A compromised owner key or a malicious owner could unilaterally alter the token's economic behavior, potentially leading to unexpected taxes or state changes for users.

**Recommendation:** Implement a multi-signature wallet for the `owner` address to require multiple approvals for critical operations. Alternatively, integrate a time-lock mechanism for sensitive functions, introducing a delay between the owner's decision and its execution, allowing the community to react to potentially malicious actions.


### `M-02` — Variable Gas Costs and State Changes on Transfers to `mainPool`  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function is called unconditionally at the beginning of every `_transfer` operation if the recipient (`to`) is the `mainPool`. This means that any transfer to the `mainPool` can trigger complex logic, including state transitions (e.g., from `TaxEnforcedAntiFarmer` to `TaxEnforced` or `TaxFree`) and tax liquidation. This can lead to unpredictable and potentially high gas costs for users, as well as unexpected changes in the token's tax rates during a seemingly simple transfer operation.

**Recommendation:** Evaluate if `_liquidateTax` needs to be called on *every* transfer to `mainPool`. Consider alternative mechanisms, such as a separate `liquidateTax` function that can be called by anyone (or specific roles) when conditions are met, or a more gas-efficient check within `_transfer` to only trigger `_liquidateTax` under specific, less frequent circumstances. Clearly document the gas implications and potential state changes for users interacting with the `mainPool`.


### `L-01` — `uint48` for `antiFarmerExpirationTime`  *(Severity: Low · Status: Unresolved)*

The `antiFarmerExpirationTime` variable is stored as a `uint48`. While `uint48` is sufficient for typical anti-farmer durations (up to approximately 8925 years from the Unix epoch), it imposes a hard limit on the maximum possible duration. In contrast, `taxExpirationTime` uses `uint64`. Using a smaller type than necessary for timestamps can lead to issues if the protocol's lifespan or desired durations exceed these limits in the distant future, or if there's a desire for consistency.

**Recommendation:** Consider using `uint64` for `antiFarmerExpirationTime` for consistency with `taxExpirationTime` and to provide a larger timestamp range, mitigating any potential future issues with extremely long durations. This change would have minimal gas impact.


### `I-01` — Ambiguous Initialization of `taxExpirationTime`  *(Severity: Informational · Status: Unresolved)*

In the `initialize` function, `taxExpirationTime` is set to `uint64(params.taxDuration)`, which represents a duration. However, in `finalizeMigration`, this value is updated by adding `block.timestamp` (`currentPoolState.taxExpirationTime + block.timestamp`), effectively converting it into an absolute timestamp. This dual interpretation (duration vs. timestamp) can be confusing and might lead to misinterpretation of the variable's purpose at different stages of the contract's lifecycle.

**Recommendation:** To improve clarity, consider renaming `params.taxDuration` to `params.taxPeriod` or `params.taxDurationSeconds` to explicitly indicate it's a duration. Additionally, add comments in both `initialize` and `finalizeMigration` to clarify that `taxExpirationTime` initially stores a duration and is later converted to an absolute timestamp upon migration finalization.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7dbc...7777`](https://bscscan.com/address/0x7dbc3c4e6f681d92634f647f09bda66c289f7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001306 |
| **24h Volume** | $131.2K |
| **Liquidity** | $39.2K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 28d |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 3.0% / 3.6% |
| **24h Transactions** | 1594 buys / 1180 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x5ee90fc5f55f4bd62a152bee267159e56bf49cc2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/max-sister-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
