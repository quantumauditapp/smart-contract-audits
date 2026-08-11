---
token: Monkey
ticker: MONKEY
network: bsc
risk_score: 89
status: critical
date: 2026-08-11
---

# Monkey (MONKEY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 89/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monkey-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and pool state management. The audit identified critical upgradeability flaws due to the incorrect use of immutable variables in an upgradeable context, and a significant portion of the core tax processing logic (`_processTax`) was truncated, preventing a full security assessment. Additionally, high-severity centralization risks and potential denial-of-service vectors were found. The contract demonstrates good practices in some areas, such as efficient struct packing and the use of OpenZeppelin upgradeable standards, but these are overshadowed by the critical issues.

> **Final Recommendation:** Address the critical upgradeability issue by removing `immutable` keywords from state variables in the upgradeable contract and managing their values through storage slots and initializer functions. Provide the complete implementation of the `_processTax` function to allow for a thorough security review of its external interactions and reentrancy safeguards. Consider implementing a more decentralized governance mechanism for critical state transitions to mitigate centralization risks. Ensure robust error handling and gas considerations for all external calls to prevent denial-of-service scenarios.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 2/10 | High | The technical architecture leverages OpenZeppelin's upgradeable ERC20 and access control patterns (7.1 Architecture). However, a critical flaw exists with immutable variables in the upgradeable… |
| **Governance / Economics** | 2/10 | High | The contract's economic model includes dynamic buy/sell taxes and an anti-farmer mechanism, managed through various pool states (7.4 Economic). Critical state transitions, such as `startMigration`… |
| **Upgrades** | 3/10 | High | The contract is designed to be upgradeable using OpenZeppelin's UUPS proxy pattern, indicated by `Initializable` and `_disableInitializers()` (7.7 Upgrades). However, the use of `immutable` variables… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Immutable Variables in Upgradeable Contract  *(Severity: Critical · Status: Unresolved)*

The `FlapTaxTokenV3` contract declares `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` as `immutable` variables. In an upgradeable contract using a proxy pattern (like UUPS), the constructor of the implementation contract is only called once upon its initial deployment, not when the proxy is initialized or upgraded. Consequently, these `immutable` variables will always read as their default value (zero) when accessed through the proxy, leading to incorrect contract behavior and a fundamental design flaw for the token's core logic.

**Recommendation:** Remove the `immutable` keyword from `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD`. Instead, declare them as regular state variables and initialize their values within the `initialize` function. This ensures they are correctly set in the proxy's storage during deployment and accessible as intended.


### `C-02` — Incomplete `_processTax` Logic and External Call Risks  *(Severity: Critical · Status: Unresolved)*

The `_processTax` function, which is invoked within `_liquidateTax` to handle collected taxes, is truncated in the provided source code. This function is critical as it likely involves external calls to `taxProcessor` and `dividendContract`. Without its full implementation, it is impossible to assess potential reentrancy vulnerabilities, gas limit issues, or other external call risks that could lead to loss of funds, incorrect tax distribution, or denial of service. The reentrancy guard (`notLiquidating`) around the call is noted, but the external call's internal logic remains unknown.

**Recommendation:** Provide the complete and verified source code for the `_processTax` function and any related external contracts (`ITaxProcessor`, `IDividend`). A thorough review of this critical component is essential to ensure proper security, reentrancy protection, and correct handling of funds.


### `H-01` — Centralized Control over Pool State Transitions  *(Severity: High · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control critical transitions between pool states (e.g., from `BondingCurve` to `Migrating`, and `Migrating` to `TaxEnforcedAntiFarmer`), are restricted to `onlyOwner`. This grants the contract owner sole authority over these significant operational changes. A compromised or malicious owner could unilaterally alter the token's behavior, potentially enabling or disabling taxes, or changing transfer restrictions, without community consensus.

**Recommendation:** Consider implementing a more decentralized governance mechanism for critical state transitions. This could involve a multi-signature wallet, a time-locked governance contract, or a community-driven voting system. If centralized control is intended, ensure robust operational security for the owner's private key.


### `H-02` — Denial of Service via `_processTax` Revert  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function is called at the beginning of every `_transfer` operation where the `to` address is the `mainPool`. If the external call within the (truncated) `_processTax` function reverts for any reason (e.g., insufficient gas, external contract error, or malicious reentrancy attempt that causes a revert), the entire `_transfer` transaction will revert. This could lead to a denial of service, preventing users from transferring tokens to the `mainPool` and potentially disrupting liquidity provision or other core functionalities.

**Recommendation:** Implement robust error handling for the `_processTax` function. Consider using a `try-catch` block for external calls to gracefully handle reverts without blocking the main `_transfer` functionality. Alternatively, design `_processTax` to be pull-based or to use a separate, non-blocking mechanism for tax distribution, ensuring that `_transfer` remains resilient.


### `M-01` — Unused State Variables  *(Severity: Medium · Status: Unresolved)*

The state variables `liqExpectedOutputAmount`, `initialLiquidationThreshold`, and `MIN_LIQ_THRESHOLD` are declared and initialized but are not referenced or utilized anywhere in the provided contract logic. While `MIN_LIQ_THRESHOLD` is also affected by the immutable variable issue (C-01), its general lack of use suggests either incomplete development, dead code, or a potential misunderstanding of the contract's intended functionality. This can lead to confusion, increased complexity, and wasted storage.

**Recommendation:** Review the contract's design to determine if these variables are truly necessary. If they are intended for future functionality, add comments explaining their purpose. If they are not needed, remove them to reduce contract size, complexity, and gas costs associated with storage. Ensure all critical parameters are actively used in the contract's logic.


### `L-01` — Reliance on `block.timestamp` for Critical Expiration  *(Severity: Low · Status: Unresolved)*

The contract relies on `block.timestamp` for checking `taxExpirationTime` and `antiFarmerExpirationTime`. While `block.timestamp` is commonly used for time-based logic, miners have a limited ability to manipulate its value (up to 900 seconds on Ethereum, typically less on other EVM chains like BSC). For critical, short-duration events, this manipulation could potentially be exploited by miners to front-run or delay state transitions, although the impact on long-term expiration times is generally minimal.

**Recommendation:** For time-sensitive operations where miner manipulation could have a significant impact, consider using alternative time sources or mechanisms that are less susceptible to manipulation, such as a decentralized oracle for time. For expiration times spanning days or longer, `block.timestamp` is generally acceptable, but developers should be aware of its limitations.


### `I-01` — Efficient Struct Packing  *(Severity: Informational · Status: Resolved)*

The `PackedPoolState` struct is designed efficiently by carefully ordering and sizing its member variables (`uint8`, `uint16`, `uint16`, `bool`, `uint96`, `uint64`, `uint48`). The total bit size (256 bits) allows the entire struct to fit within a single storage slot. This optimization reduces gas costs associated with reading and writing the struct to storage, demonstrating good Solidity development practices.

**Recommendation:** Maintain this practice for future struct definitions to ensure optimal gas efficiency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4ac8...7777`](https://bscscan.com/address/0x4ac85f2a2d22956a15a95ebe142d442da35e7777) |
| **Network** | BNB Chain |
| **Price** | $0.0001251 |
| **24h Volume** | $90.9K |
| **Liquidity** | $32.7K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 2d |
| **Top-10 Holders** | 75.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1154 buys / 772 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x0c54d8a065be1442b238bae5422c577b53e5890a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monkey-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
