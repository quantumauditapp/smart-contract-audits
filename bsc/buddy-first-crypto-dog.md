---
token: BUDDY - First Crypto Dog
ticker: BUDDY
network: bsc
risk_score: 40
status: medium
date: 2026-09-12
---

# BUDDY - First Crypto Dog (BUDDY) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/buddy-first-crypto-dog-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an upgradeable ERC20 token incorporating a dynamic tax mechanism and a multi-stage migration process. It leverages OpenZeppelin's upgradeable contracts for core functionalities and access control. The audit identified a potential reentrancy vulnerability in the tax liquidation logic, centralized control by the owner over critical state transitions, and susceptibility to MEV for time-dependent state changes. The contract demonstrates good code quality and adherence to upgradeability patterns, but requires careful review of external interactions and owner privileges.

> **Final Recommendation:** Thoroughly review the complete `_liquidateTax` function, especially any external calls to `ITaxProcessor`, `IDividend`, or `v2Router`, to ensure robust reentrancy protection. Implement a reentrancy guard (e.g., `nonReentrant` or a mutex flag) around any external calls that modify state. Consider decentralizing critical owner functions through a multi-signature wallet or a time-lock contract to mitigate centralized control risks. Evaluate the impact of MEV on time-dependent state changes and explore alternative mechanisms if the risk is deemed too high. Ensure that the upgrade mechanism, particularly `_authorizeUpgrade` for UUPS proxies, is correctly implemented and secured.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes OpenZeppelin's upgradeable ERC20, Ownable, and Permit modules, demonstrating a robust architectural foundation (7.1). Code quality is generally high, with proper use of… |
| **Governance / Economics** | 4/10 | Medium | The economic model revolves around a dynamic tax mechanism that changes based on the `poolState` (7.4). The owner has significant centralized control (7.5) over the contract's lifecycle, including… |
| **Upgrades** | 8/10 | Low | The contract is designed as an upgradeable implementation using OpenZeppelin's `Initializable` and `Upgradeable` patterns (7.7). The constructor correctly calls `_disableInitializers()`, and the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Potential Reentrancy in `_liquidateTax` Function  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function is called on every `_transfer` and is likely to perform external calls (e.g., to `ITaxProcessor`, `IDividend`, or a DEX via `v2Router`) to process collected taxes. The provided snippet shows a check for `currentPoolState.notLiquidating`, but it does not show how this flag is set to `false` at the beginning of the liquidation process and `true` at the end. If external calls are made before state updates or without a proper reentrancy guard, a malicious external contract could re-enter the `_transfer` or `_liquidateTax` function, potentially draining funds or manipulating contract state.

**Recommendation:** Implement a robust reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard` or a custom mutex flag) around the `_liquidateTax` function, specifically covering any external calls. Ensure the `notLiquidating` flag is correctly managed: set to `false` at the very beginning of the liquidation logic and reset to `true` only after all external calls and state updates are complete.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract inherits `OwnableUpgradeable`, granting a single owner address exclusive control over critical functions such as `startMigration` and `finalizeMigration`. These functions significantly alter the token's tax and transfer mechanics, moving it through different `PoolState`s. This centralization introduces a single point of failure, where a compromised owner key or a malicious owner could unilaterally change the token's behavior, potentially leading to economic instability or loss of user trust.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the owner address to distribute control and reduce the risk of a single point of failure. For highly sensitive operations like state migrations, introduce a time-lock mechanism to allow users sufficient time to react to impending changes.


### `M-02` — Time-Dependent State Changes Susceptible to MEV  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function modifies the `poolState` (e.g., from `TaxEnforcedAntiFarmer` to `TaxEnforced` or `TaxFree`) based on `block.timestamp` exceeding `taxExpirationTime` or `antiFarmerExpirationTime`. These time-based state transitions can have significant economic implications for users, as they directly affect tax rates. Malicious miners or sophisticated actors could exploit this by manipulating block timestamps within a small window or front-running transactions to trigger state changes at an opportune moment, potentially gaining an unfair advantage or causing adverse effects for other users.

**Recommendation:** While `block.timestamp` is commonly used, be aware of its manipulability. If precise timing is critical and economic incentives for manipulation are high, consider alternative time sources (e.g., Chainlink Keepers or Oracles for time-based events) or implement a grace period after a state change is triggered to allow users to react, reducing the immediate impact of MEV.


### `L-01` — Lack of Setter Functions for Critical External Contracts  *(Severity: Low · Status: Unresolved)*

Several critical external contract addresses, including `taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, `mainPool`, and the `pools` mapping, are set only during the `initialize` function. While this ensures immutability after deployment, it also means that if any of these external dependencies need to be updated (e.g., due to a bug, a migration, or a strategic change), the entire `FlapTaxTokenV3` contract would require an upgrade. This reduces operational flexibility and increases the overhead for necessary updates.

**Recommendation:** For external contract addresses that may require updates over the contract's lifetime, consider implementing owner-only setter functions. These setters should include appropriate access control, zero-address checks, and potentially a time-lock mechanism to provide transparency and a grace period before changes take effect.


### `I-01` — Missing `_authorizeUpgrade` for UUPS Proxy Pattern  *(Severity: Informational · Status: Unresolved)*

The contract is an implementation behind a proxy and utilizes OpenZeppelin's `Upgradeable` contracts. If the proxy follows the UUPS (Universal Upgradeable Proxy Standard) pattern, the implementation contract is responsible for authorizing upgrades via an `_authorizeUpgrade` function. This function is not present in the provided snippet. Without it, the upgradeability mechanism might either be insecure (if the proxy allows anyone to upgrade) or not fully compliant with the UUPS standard, potentially leading to unexpected upgrade behavior or security risks.

**Recommendation:** Verify the exact proxy pattern used. If it is UUPS, ensure that the full implementation contract includes a properly secured `_authorizeUpgrade` function, typically restricting upgrade calls to the contract owner or a designated governance mechanism. If a different proxy pattern (e.g., Transparent Proxy) is used, confirm that the proxy admin's upgrade authority is adequately secured.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4e00...7777`](https://bscscan.com/address/0x4e0026b2a27f60cd7ed8bb71f9489501b1f87777) |
| **Network** | BNB Chain |
| **Price** | $0.0003088 |
| **24h Volume** | $381.4K |
| **Liquidity** | $57.0K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 9h |
| **Top-10 Holders** | 31.4% of supply |
| **Buy / Sell Tax** | 1.0% / 2.0% |
| **24h Transactions** | 2964 buys / 2527 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf0ca0a1dcd9fc30ad5570e1882a483f8e4cafbb6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/buddy-first-crypto-dog-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
