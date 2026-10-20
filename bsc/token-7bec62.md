---
token: 人生好物
ticker: 人生好物
network: bsc
risk_score: 50
status: medium
date: 2026-09-24
---

# 人生好物 (人生好物) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-7bec62-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a complex state-based tax mechanism. A critical portion of the contract's core economic logic, the `_liquidateTax` function, was truncated in the provided source code. This prevents a full security assessment of the tax collection, liquidation, and state transition processes, introducing significant unquantifiable risk. Other findings include potential reentrancy, centralization risks, and minor precision loss in tax calculations.

> **Final Recommendation:** It is imperative to obtain and review the complete source code for the `_liquidateTax` function to conduct a thorough security assessment of the contract's core economic logic. Address the potential reentrancy vulnerability in `_liquidateTax` by implementing checks-effects-interactions patterns or reentrancy guards if external calls are made. Consider implementing a multi-signature wallet or a time-locked contract for critical owner-controlled functions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements an upgradeable ERC20 token with a complex state-based tax mechanism (7.1 Architecture). It leverages OpenZeppelin's upgradeable contracts and `SafeERC20` for secure external… |
| **Governance / Economics** | 2/10 | High | The contract's economic model revolves around dynamic tax rates and state transitions (7.4 Economic). Taxes are collected into the contract itself, awaiting liquidation, but the full logic for this… |
| **Upgrades** | 8/10 | Low | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` pattern, indicating a UUPS proxy implementation (7.7 Upgrades). The constructor correctly calls… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Critical Logic Unauditable Due to Truncation  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated. This function is critical for the contract's economic model, handling tax collection, liquidation, and state transitions. Without the full code, a comprehensive security assessment of this core functionality is impossible, leaving a significant unknown risk (7.2 Code Security, 7.4 Economic).

**Recommendation:** Provide the complete and untruncated source code for the `_liquidateTax` function to enable a full security audit. Until the complete code is available, the contract's core economic security cannot be fully guaranteed.


### `H-01` — Potential Reentrancy in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function is called on every transfer to `mainPool`. If the full, truncated implementation of `_liquidateTax` makes external calls (e.g., to `taxProcessor` or `dividendContract`) before updating internal state or handling collected taxes, it could be vulnerable to reentrancy attacks. An attacker could re-enter the contract during an external call, potentially manipulating balances or state before the initial transaction completes (7.2 Code Security, 7.6 External).

**Recommendation:** Implement the 'checks-effects-interactions' pattern within the `_liquidateTax` function. Ensure all state changes related to tax collection and liquidation are completed before any external calls are made. Consider using OpenZeppelin's `ReentrancyGuard` if complex external interactions are unavoidable.


### `M-01` — Centralization Risk with Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `OwnableUpgradeable` contract grants significant control to the owner, including the ability to `startMigration` and `finalizeMigration`, which directly changes the `PoolState`. This centralization of control means a compromised owner key or a malicious owner could unilaterally alter the contract's operational state, potentially impacting tokenomics and user funds (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Consider implementing a multi-signature wallet for ownership or critical administrative functions. Alternatively, introduce a time-lock mechanism for sensitive state-changing operations to provide a window for community review or intervention.


### `L-01` — Precision Loss in Tax Calculation  *(Severity: Low · Status: Unresolved)*

The tax calculation `(amount * rate) / 10000` uses integer division. For small `amount` values or low `rate` values, this can lead to a loss of precision, resulting in a slightly lower tax collected than a mathematically precise calculation would yield. While common in Solidity, it means the protocol might not collect the exact intended tax amount in all scenarios (7.2 Code Security, 7.4 Economic).

**Recommendation:** Acknowledge this behavior as an inherent characteristic of integer arithmetic in Solidity. For most practical purposes, the impact is negligible. If higher precision is critical for very small transactions, consider adjusting the tax rate basis (e.g., `100_000` instead of `10_000`) or implementing a more complex fixed-point arithmetic library, though this adds complexity and gas cost.


### `I-01` — Reliance on `block.timestamp` for Expiration  *(Severity: Informational · Status: Unresolved)*

The contract uses `block.timestamp` to determine `taxExpirationTime` and `antiFarmerExpirationTime`. While `block.timestamp` is commonly used, miners have a limited ability to manipulate its value (typically within a few seconds of the actual time). This could potentially allow for minor front-running or delayed execution of time-sensitive state transitions (7.4 Economic).

**Recommendation:** Be aware of the inherent limitations of `block.timestamp` for highly time-sensitive operations. For most use cases, the minor manipulation risk is acceptable. If precise, unmanipulable timing is critical, consider alternative oracle-based time sources, though this introduces external dependencies and additional complexity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1e3e...7777`](https://bscscan.com/address/0x1e3ed808b60688c3bbf235c67159376d1ad77777) |
| **Network** | BNB Chain |
| **Price** | $0.0002564 |
| **24h Volume** | $205.4K |
| **Liquidity** | $46.2K |
| **Volume / Liquidity** | 4.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | 20.4% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1646 buys / 1064 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcffea1f7dddb0c35f3518854c4560504519600e2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-7bec62-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-24*
