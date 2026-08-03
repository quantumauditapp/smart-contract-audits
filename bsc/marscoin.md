---
token: MarsCoin
ticker: MARSCOIN
network: bsc
risk_score: 37
status: medium
date: 2026-08-03
---

# MarsCoin (MARSCOIN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/marscoin-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an ERC20 token with advanced tax mechanisms, including asymmetric buy/sell taxes, anti-farmer tax, and a dynamic liquidation threshold. It leverages OpenZeppelin's upgradeable contracts for secure upgradeability. The audit identified a high-severity risk related to potential integer overflow in a packed struct field if token supply limits are significantly altered, alongside medium-severity centralization and external dependency risks. The contract demonstrates good architectural practices for upgradeability and gas optimization.

> **Final Recommendation:** It is recommended to carefully review the `uint96` type for `liquidationThreshold` and implement robust checks or alternative data types if the token's `maxSupply` is ever considered for an increase beyond current limits. Additionally, consider implementing a multi-signature wallet for critical owner-controlled functions to mitigate centralization risks and enhance security. Thoroughly vet all external contract addresses before deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes OpenZeppelin's upgradeable standards and implements a gas-optimized `PackedPoolState` struct (7.1 Architecture). A notable technical risk is the `uint96` type for… |
| **Governance / Economics** | 5/10 | Medium | The contract exhibits a medium level of centralization due to the `onlyOwner` role having extensive control over critical parameters such as tax rates, external contract addresses (`taxProcessor`… |
| **Upgrades** | 3/10 | High | The contract is designed for upgradeability using OpenZeppelin's `Initializable` and `Upgradeable` patterns, indicating a UUPS proxy implementation (7.7 Upgrades). Immutable variables… |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `H-01` — Potential `uint96` Overflow in `PackedPoolState.liquidationThreshold`  *(Severity: High · Status: Unresolved)*

The `liquidationThreshold` field within the `PackedPoolState` struct is defined as `uint96`. While the current `maxSupply` of 1 billion tokens (1e9 ether) fits within this type, the contract's `custom:security-note` explicitly warns that if the total supply limit is changed to more than 1 billion ether, this field type must be revisited. Failure to do so could lead to an integer overflow if the `liquidationThreshold` value exceeds `uint96`'s maximum capacity (~79 billion tokens with 18 decimals), causing incorrect calculations or unexpected protocol behavior. This is a critical design consideration for future scalability.

**Recommendation:** Implement a robust monitoring system for the token's `maxSupply` and `liquidationThreshold` values. If there is any intention to increase `maxSupply` significantly in the future, proactively adjust the `liquidationThreshold` data type (e.g., to `uint128` or `uint256`) in a new implementation to prevent potential overflows. Consider adding runtime checks to ensure `liquidationThreshold` never exceeds `type(uint96).max` during updates.


### `M-01` — High Centralization Risk via Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `OwnableUpgradeable` pattern grants significant control to a single `owner` address. Functions like `startMigration` are protected by `onlyOwner`. Furthermore, the `initialize` function allows the owner to set critical parameters such as `taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, `antiFarmerDuration`, `buyTax`, `sellTax`, `taxDuration`, `liqExpectedOutputAmount`, and the initial `pools`. This extensive control over core protocol addresses and economic parameters introduces a high degree of centralization, making the protocol vulnerable to a single point of compromise or malicious action by the owner.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `owner` role to require multiple approvals for critical operations. For highly sensitive parameters or actions, explore time-locked governance mechanisms or decentralized autonomous organization (DAO) control to distribute power and increase transparency.


### `M-02` — Reliance on External Contracts Introduces Dependency Risk  *(Severity: Medium · Status: Unresolved)*

The `FlapTaxTokenV3` contract relies heavily on several external contracts, including `v2Router`, `taxProcessor`, `dividendContract`, `quoteToken`, and the addresses within the `pools` mapping. These external dependencies are set during initialization and can be critical for the token's functionality (e.g., tax processing, liquidity management, dividend distribution). A compromise, malfunction, or malicious upgrade in any of these external contracts could directly impact the security and functionality of `FlapTaxTokenV3`, potentially leading to loss of funds or service disruption.

**Recommendation:** Thoroughly audit and vet all external contracts before integrating them. Implement robust input validation for external addresses. Consider adding mechanisms to pause critical interactions with external contracts in emergencies or to allow the owner to update compromised external addresses. Clearly document the trust assumptions made regarding each external dependency.


### `L-01` — Potential Gas Limit Exceeded in `initialize` for Large Pool Arrays  *(Severity: Low · Status: Unresolved)*

The `initialize` function includes a `for` loop that iterates through the `params.pools` array to set `pools[params.pools[i]] = true`. If the `params.pools` array contains an extremely large number of addresses, this loop could consume a significant amount of gas. In extreme cases, it might cause the transaction to exceed the block gas limit, preventing the contract from being initialized successfully.

**Recommendation:** While unlikely for typical deployments, consider imposing a reasonable maximum limit on the size of the `params.pools` array during initialization. Alternatively, if a very large number of pools is anticipated, implement a paginated or batched approach for adding pools post-initialization via an owner-controlled function, rather than during a single deployment transaction.


### `I-01` — Reliance on `block.timestamp` for Time-Dependent Mechanisms  *(Severity: Informational · Status: Unresolved)*

The contract utilizes `taxExpirationTime` and `antiFarmerExpirationTime`, which are derived from `block.timestamp`. While `block.timestamp` is a standard EVM primitive, it is susceptible to minor manipulation by miners (within a small window, typically a few seconds). For highly time-sensitive operations, this could introduce a slight degree of unpredictability or allow for minor front-running opportunities related to tax expirations.

**Recommendation:** Acknowledge the inherent limitations of `block.timestamp` in EVM. For most applications, this level of precision is acceptable. If extreme precision or resistance to miner manipulation is critical for future features, consider alternative time-keeping mechanisms (e.g., relying on oracle-provided timestamps, though this introduces new trust assumptions).


### `I-02` — Effective Use of Immutable Variables for Threshold Limits  *(Severity: Informational · Status: Unresolved)*

The contract correctly utilizes `immutable` keywords for `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` in its constructor. This ensures that these critical threshold limits are set once at deployment and cannot be altered thereafter, providing a strong guarantee of their values across all clones and future upgrades of this implementation. This is a good practice for fixed protocol parameters.

**Recommendation:** Continue to identify and apply the `immutable` keyword to any other parameters that are intended to be unchangeable throughout the contract's lifecycle, enhancing security and predictability.


### `I-03` — Well-Implemented Upgradeability Pattern  *(Severity: Informational · Status: Unresolved)*

The contract correctly implements the UUPS (Universal Upgradeable Proxy Standard) pattern by inheriting from OpenZeppelin's `Initializable`, `ERC20Upgradeable`, `ERC20PermitUpgradeable`, and `OwnableUpgradeable` contracts. The constructor calls `_disableInitializers()` to prevent re-initialization of the implementation contract, and the `initialize` function uses the `initializer` modifier. This setup provides a secure and standard way to manage contract upgrades.

**Recommendation:** Maintain strict control over the proxy's admin address, as this address has the power to upgrade the contract. Ensure that upgrade proposals are thoroughly tested and reviewed before deployment to production.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfe18...7777`](https://bscscan.com/address/0xfe189e97832da1573e4e4ff034f4ffc3a15c7777) |
| **Network** | BNB Chain |
| **Price** | $0.03253 |
| **24h Volume** | $3.04M |
| **Liquidity** | $653.2K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 6d |
| **Top-10 Holders** | 21.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5078 buys / 4557 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x94f3ed36706c746ad59fadcaf271b7431ab1d8f1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/marscoin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-03*
