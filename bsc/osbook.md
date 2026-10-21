---
token: osbook
ticker: OSBOOK
network: bsc
risk_score: 4
status: low
date: 2026-09-22
---

# osbook (OSBOOK) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/osbook-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an upgradeable ERC20 token implementation featuring a dynamic tax mechanism and a multi-state pool system. It leverages OpenZeppelin's upgradeable contracts for robustness. The audit identified a high centralization risk due to extensive owner control over critical economic parameters and state transitions. Medium risks include potential denial of service from external contract interactions within the transfer path and reliance on truncated external contract logic. Low risks involve `block.timestamp` reliance and potential gas issues during initialization with large arrays. The contract's upgradeability is well-implemented but also owner-controlled.

> **Final Recommendation:** Prioritize decentralizing critical control mechanisms, such as ownership of the contract and the ability to change core economic parameters. Consider implementing a multi-signature wallet or a DAO for these sensitive operations to enhance security and community trust. Thoroughly audit all external dependencies, especially `ITaxProcessor` and `IDividend`, to ensure their security and prevent potential reentrancy or denial-of-service vulnerabilities that could impact token transfers. Implement robust error handling and reentrancy guards where necessary.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 standard, providing a solid foundation for token functionality and upgradeability (7.1 Architecture, 7.2 Code Security). It implements a… |
| **Governance / Economics** | 8/10 | Low | The contract employs an `OwnableUpgradeable` pattern, granting the owner significant control over critical economic parameters and state transitions (7.3 Access Control, 7.5 Governance). The owner… |
| **Upgrades** | 10/10 | Low | The contract is designed as an upgradeable proxy implementation using OpenZeppelin's `Initializable` and `Upgradeable` patterns, which is a robust approach for future enhancements (7.7 Upgrades). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Critical Token Parameters and State Transitions  *(Severity: High · Status: Unresolved)*

The `OwnableUpgradeable` contract grants the owner significant control over the token's core functionality. The owner can initiate `startMigration()` and `finalizeMigration()`, which directly change the `poolState` (e.g., from `BondingCurve` to `Migrating` to `TaxEnforcedAntiFarmer`). These state changes dictate whether transfers are taxed, at what rates, and if they are restricted. For example, the owner can enable or disable taxes, and change tax rates by transitioning states. This level of control allows the owner to unilaterally alter the token's economic model and transfer behavior without community consensus.

**Recommendation:** Implement a multi-signature wallet for ownership or transition to a decentralized governance model (e.g., DAO) for critical parameter changes and state transitions. If a multi-sig is not feasible, ensure robust operational security for the owner key.


### `M-01` — Reliance on External Contracts with Truncated Logic  *(Severity: Medium · Status: Unresolved)*

The contract relies on external contracts `ITaxProcessor` and `IDividend` for critical functions like `processTax` and `distributeDividends` within `_liquidateTax`. The full implementation of `_liquidateTax` and the interfaces for these external contracts are truncated in the provided source. If these external contracts contain vulnerabilities (e.g., reentrancy, denial of service, or incorrect logic), they could directly impact the security and functionality of `FlapTaxTokenV3`, potentially leading to frozen funds or unexpected behavior during tax liquidation.

**Recommendation:** Conduct a thorough audit of the `ITaxProcessor` and `IDividend` contracts, including their full source code, to ensure they are secure and function as intended. Implement robust error handling and reentrancy guards in `ITaxProcessor` and `IDividend` if they perform external calls.


### `M-02` — Potential for Denial of Service in `_liquidateTax`  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function is called on every `_transfer`. This function performs state transitions and potentially calls external contracts (`ITaxProcessor.processTax` and `IDividend.distributeDividends` based on the truncated code). If any of these external calls or internal logic within `_liquidateTax` (e.g., due to an unexpected state or insufficient funds for a required operation) were to revert, it would cause the entire `_transfer` operation to revert, effectively halting all token transfers. This creates a denial-of-service vector for token holders.

**Recommendation:** Isolate complex or external interactions from the core `_transfer` path. Consider implementing a separate, owner-triggered function for tax liquidation and dividend distribution, or ensure that `_liquidateTax` handles all potential failure scenarios gracefully without reverting the `_transfer` function.


### `L-01` — `block.timestamp` Reliance for Critical State Transitions  *(Severity: Low · Status: Unresolved)*

The `_liquidateTax` function uses `block.timestamp` to determine state transitions, specifically for `taxExpirationTime` and `antiFarmerExpirationTime`. While `block.timestamp` is generally suitable for time-based logic, it is susceptible to miner manipulation within a small window (typically a few seconds). A malicious miner could slightly adjust the timestamp to trigger a state change (e.g., from `TaxEnforcedAntiFarmer` to `TaxEnforced` or `TaxFree`) earlier or later, potentially benefiting from changes in tax rates or transfer restrictions.

**Recommendation:** For critical time-sensitive operations where miner manipulation could have significant financial implications, consider using `block.number` and calculating time based on average block times, or use a decentralized oracle for time if higher precision and tamper-resistance are required. For this specific use case, the risk is low given the typical duration of tax periods.


### `L-02` — Gas Limit Risk in `initialize` for `pools` Array  *(Severity: Low · Status: Unresolved)*

The `initialize` function iterates through the `params.pools` array to set `pools[address] = true`. If `params.pools.length` is excessively large, this loop could potentially consume a significant amount of gas, potentially exceeding the block gas limit during deployment. While `initialize` is called only once, a very large array could lead to deployment failure.

**Recommendation:** While unlikely to be an issue for typical deployments, consider imposing a reasonable maximum length for the `pools` array in `initialize` to prevent potential gas limit issues. For example, `require(params.pools.length <= MAX_POOLS_COUNT, "Too many pools");`.


### `I-01` — Unused `initialLiquidationThreshold` Variable  *(Severity: Informational · Status: Unresolved)*

The `initialLiquidationThreshold` state variable is set in the `initialize` function to `START_LIQ_THRESHOLD`. However, in the provided code snippet, this variable is not subsequently read or used anywhere else. This suggests it might be redundant or part of an incomplete feature.

**Recommendation:** Review the purpose of `initialLiquidationThreshold`. If it's not intended for future use, consider removing it to reduce contract complexity and storage costs. If it is intended for future use, ensure its purpose is clearly documented and that it is integrated into the contract's logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x355c...7777`](https://bscscan.com/address/0x355c11826d33ac0cce61f4c1f71eef9363707777) |
| **Network** | BNB Chain |
| **Price** | $0.0007491 |
| **24h Volume** | $851.7K |
| **Liquidity** | $96.6K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 26.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3279 buys / 2884 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7a129d9882c00fb01ab006402fd0ed141dc012ef)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/osbook-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
