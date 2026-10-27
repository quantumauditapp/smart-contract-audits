---
token: VCAT
ticker: VCAT
network: base
risk_score: 18
status: low
date: 2026-09-20
---

# VCAT (VCAT) — Smart Contract Security Analysis | Base

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vcat-base)

---

## Audit Summary

The FlapTaxTokenV3 contract, an upgradeable ERC20 token, implements a complex tax and state machine mechanism. The audit identified two critical vulnerabilities: immutable variables initialized in the constructor will be zero in the proxy context, leading to incorrect logic, and a potential integer underflow in tax calculations if tax rates exceed 100%. High and medium risks include immutable critical external dependencies, publicly triggerable state transitions, and significant centralization of power with the owner. The contract generally follows OpenZeppelin upgradeable patterns but requires immediate attention to the identified critical issues.

> **Final Recommendation:** It is critical to address the identified issues, particularly the incorrect use of immutable variables in an upgradeable context and the potential for integer underflow in tax calculations. These issues can lead to severe operational failures and economic instability. Implement robust access control for critical external dependencies and consider decentralizing owner control to mitigate centralization risks. Thoroughly review the economic implications of publicly triggerable state transitions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good code quality by utilizing OpenZeppelin upgradeable standards and packed structs for gas efficiency. However, critical vulnerabilities exist, including a potential… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model incorporates a flexible tax mechanism and state transitions, managed by the owner. A significant risk is the immutability of critical external dependencies like… |
| **Upgrades** | 9/10 | Low | The contract correctly uses OpenZeppelin's upgradeable patterns, including `Initializable` and `_disableInitializers`. However, a critical upgrade safety issue exists where `immutable` variables… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 5 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Publicly Triggerable State Transitions and Tax Liquidation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, which contains logic for changing the `PoolState` (e.g., from `TaxEnforcedAntiFarmer` to `TaxEnforced` or `TaxFree`) and potentially initiating tax processing, is called internally by `_transfer` when tokens are sent to the `mainPool`. If `mainPool` is a publicly accessible AMM pool, any user can trigger this function by simply transferring tokens to it. This creates a potential for front-running or malicious actors to force state transitions at economically unfavorable times, or to repeatedly trigger the liquidation logic, potentially impacting system stability or gas costs. (Coverage: 7.

**Recommendation:** Re-evaluate the trigger mechanism for `_liquidateTax`. Consider restricting its execution to `onlyOwner` or a designated `taxProcessor` role, or implementing a cooldown period or minimum amount threshold to prevent abuse. If public triggering is intended, ensure that the economic implications of such actions are thoroughly modeled and mitigated.


### `M-02` — Centralization of Power with Owner/Deployer  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract grants significant control to the `owner` role, allowing them to initiate and finalize migration states (`startMigration`, `finalizeMigration`). Furthermore, the entire `maxSupply` of tokens is minted to `msg.sender` (the deployer/initializer) during the `initialize` function. This concentration of power in a single entity (the owner/deployer) introduces a single point of failure. If the owner's private key is compromised, an attacker could manipulate the token's state, potentially leading to economic damage or loss of funds. (Coverage: 7.3 Access Control, 7.4 Economic, 7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` role to distribute control and enhance security. For token distribution, explore more decentralized or time-locked vesting mechanisms rather than minting the entire supply to a single address.


### `M-03` — Immutable Variables in Upgradeable Contract Constructor Remain Zero in Proxy Context  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` variables are declared as `immutable` and initialized in the constructor of the `FlapTaxTokenV3` implementation contract. In an upgradeable proxy pattern, the constructor of the implementation contract is never called when users interact with the proxy. Consequently, these `immutable` variables will retain their default zero values (0) in the context of the proxy, leading to incorrect or unintended behavior in any logic that relies on them. For example, `initialLiquidationThreshold` is set to `START_LIQ_THRESHOLD` in `initialize`, but if `START_LIQ_THRESHOLD` is 0, this

**Recommendation:** `immutable` variables should not be used in upgradeable contracts. Instead, these values should be stored as regular state variables and initialized via the `initialize` function, or set via an `onlyOwner` function after initialization.


### `M-04` — Potential Integer Underflow in Tax Calculation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_getTaxWithPoolState` function calculates `tax = (amount * currentPoolState.buyTaxRate) / 10000` or `(amount * currentPoolState.sellTaxRate) / 10000`. The `buyTaxRate` and `sellTaxRate` are `uint16`. If these rates are set to a value greater than `10000` (e.g., 15000 for 150% tax), the calculated `tax` could exceed the `amount` being transferred. Subsequently, in `_taxedTransfer`, the operation `amount - tax` would result in an integer underflow. While Solidity 0.8+ reverts on underflow, this would effectively block all transfers if such a tax rate is configured, rendering the token unusable. (Coverage: 7.2 Code S

**Recommendation:** Implement a check to ensure that `buyTaxRate` and `sellTaxRate` do not exceed `10000` (100%) during their setting or initialization. Alternatively, ensure that `tax` never exceeds `amount` before performing the subtraction, e.g., `uint256 remainingAmount = amount > tax ? amount - tax : 0;`. However, preventing rates > 100% is generally a better design.


### `M-05` — Critical External Dependencies Are Immutable After Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The addresses for `taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, and `mainPool` are set exclusively during the `initialize` function and cannot be modified thereafter. These are critical external dependencies for the token's core functionality (tax processing, dividends, liquidity). If any of these external contracts become compromised, deprecated, or require an update (e.g., a new router version, a bug fix in the tax processor), the system would be unable to adapt without a full contract upgrade, potentially leading to a permanent loss of functionality or funds. (Coverage: 7.1 Architecture, 7.6 External

**Recommendation:** Implement `onlyOwner` functions to allow the authorized owner to update these critical external dependency addresses. This provides necessary flexibility and resilience against external changes or issues.


### `L-01` — Lack of Explicit Upgrade Authorization in Implementation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the contract is designed as an upgradeable implementation, the provided code snippet does not include an explicit `_authorizeUpgrade` function, which is a standard component of UUPS proxy patterns to define who can initiate an upgrade. Although the proxy contract itself typically handles upgrade authorization, its absence in the implementation means the implementation contract itself doesn't enforce any specific upgrade policy, relying entirely on the proxy's configuration. This isn't a direct vulnerability in the implementation but highlights a dependency on the proxy's security configuration. (Coverage: 7.7 Upg

**Recommendation:** Ensure the proxy contract (0xfdcc845c048ad96b5c80b6a55d65c20a98d37777) has robust and secure upgrade authorization mechanisms, preferably using a multi-signature wallet or a well-tested governance module.


### `I-01` — Reliance on `block.timestamp` for Critical Timings  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `block.timestamp` to manage `taxExpirationTime` and `antiFarmerExpirationTime` for state transitions within the `_liquidateTax` function. While `block.timestamp` is commonly used, miners have a limited ability to manipulate it (typically within a 900-second window on Ethereum, less on faster chains like Base). For critical, high-value, or time-sensitive operations, this manipulation could potentially be exploited by sophisticated attackers to front-run or delay state changes for economic gain. (Coverage: 7.2 Code Security, 7.4 Economic)

**Recommendation:** For highly time-sensitive or economically critical operations, consider using a time oracle (e.g., Chainlink Keepers or a custom decentralized oracle) rather than `block.timestamp` directly. For state transitions that are not extremely time-critical, `block.timestamp` is generally acceptable, but the potential for minor manipulation should be acknowledged.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfdcc...7777`](https://basescan.org/address/0xfdcc845c048ad96b5c80b6a55d65c20a98d37777) |
| **Network** | Base |
| **Price** | $0.005759 |
| **24h Volume** | $1.45M |
| **Liquidity** | $232.4K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 36.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1977 buys / 1130 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8b9ae9726173f933972cdfd6b0b9b573826cd243)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vcat-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
