---
token: 牛梦
ticker: 牛梦
network: bsc
risk_score: 54
status: medium
date: 2026-09-13
---

# 牛梦 (牛梦) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-5696d7-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and anti-farmer features. While it utilizes OpenZeppelin's battle-tested upgradeable components, a critical vulnerability exists due to truncated code in the `_liquidateTax` function, preventing a full security assessment of core logic. High-severity issues include centralized control over critical state transitions and potential for manipulation/high gas costs within the `_liquidateTax` function. Medium-severity findings relate to inflexible pool management and a long-term integer overflow risk. Addressing the truncated code is paramount for the security of the protocol.

> **Final Recommendation:** Prioritize resolving the critical issue of the truncated `_liquidateTax` function by providing its complete and verified source code for a comprehensive security review. Address the high centralization risks by considering multi-signature wallets or time-locks for critical owner-controlled functions like state transitions. Re-evaluate the design of `_liquidateTax` to mitigate potential manipulation, high gas costs, and ensure its robustness against common vulnerabilities. Enhance transparency by implementing event emissions for all significant parameter changes and consider adding flexibility for pool management.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages OpenZeppelin's upgradeable standards for ERC20, Ownable, and Permit functionalities, contributing to a robust architectural foundation (7.1 Architecture). `SafeERC20` is… |
| **Governance / Economics** | 3/10 | High | The contract's economic model incorporates dynamic tax rates and anti-farmer mechanisms, managed through various `PoolState` transitions. The owner has significant control over these transitions via… |
| **Upgrades** | 8/10 | Low | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's `Initializable` and `_disableInitializers` in the constructor, ensuring proper upgradeability (7.7 Upgrades). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Truncated `_liquidateTax` Function Logic  *(Severity: Critical · Status: Unresolved)*

The provided source code for the `_liquidateTax` function is truncated, specifically the part dealing with the actual liquidation of `taxAmount`. This function is called on every `_transfer` operation. Without the complete logic, it is impossible to assess critical security aspects such as reentrancy risks, external call vulnerabilities, potential for denial-of-service, or incorrect handling of funds. This represents a severe unknown risk (7.2 Code Security, 7.6 External).

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function to allow for a thorough security review.


### `H-01` — Centralized Control over Core Token State Transitions  *(Severity: High · Status: Unresolved)*

The `startMigration` and `finalizeMigration` functions, which control the critical `PoolState` transitions (e.g., from `BondingCurve` to `Migrating` and then to `TaxEnforcedAntiFarmer`), are protected by the `onlyOwner` modifier. This grants the contract owner unilateral power to enable or disable core token functionalities like tax enforcement and anti-farmer mechanisms, significantly impacting the token's economic model and user experience (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for owner functions or introducing a time-lock mechanism for critical state changes to reduce single-point-of-failure risk and provide transparency.


### `H-02` — Potential for Manipulation and High Gas Costs in `_liquidateTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function is invoked on every `_transfer` call. This function performs time-based state transitions (`taxExpirationTime`, `antiFarmerExpirationTime`) and checks `balanceOf(address(this))` to trigger liquidation. Miners can slightly influence `block.timestamp`, potentially front-running or delaying state transitions. Additionally, if the contract's balance can be manipulated by external transfers, it could affect the `taxAmount > 0` condition, potentially preventing or forcing liquidations. Calling this function on every transfer, especially if the truncated liquidation logic involves complex calculations or external calls, could lead to unexpectedly high gas costs for use…

**Recommendation:** Re-evaluate the necessity of calling `_liquidateTax` on every transfer. Consider a dedicated, permissioned function for liquidation or a more gas-efficient trigger. Ensure the full liquidation logic is robust against reentrancy and external call failures. Implement safeguards against balance manipulation affecting liquidation triggers.


### `M-01` — Inflexible Pool Management  *(Severity: Medium · Status: Unresolved)*

The `pools` mapping and `mainPool` address are initialized only once during the `initialize` function. There are no owner-controlled or governance-controlled functions to add, remove, or modify these pool addresses after deployment. This inflexibility means that if a pool address changes, a new pool needs to be added, or the `mainPool` needs to be updated, a contract upgrade would be required (7.1 Architecture, 7.8 Operations).

**Recommendation:** Implement owner-controlled functions (e.g., `addPool(address _pool)`, `removePool(address _pool)`, `setMainPool(address _mainPool)`) to allow for flexible management of pool addresses. Consider adding a time-lock for such changes.


### `M-02` — `antiFarmerExpirationTime` `uint48` Overflow Risk  *(Severity: Medium · Status: Unresolved)*

The `antiFarmerExpirationTime` variable is declared as `uint48`. While `block.timestamp` is currently well within `uint48` limits, in approximately 17,000 years, `block.timestamp` will exceed the maximum value of `uint48`. At that point, `block.timestamp + antiFarmerDuration` could cause an overflow when cast to `uint48`, leading to incorrect expiration calculations and unexpected contract behavior (7.2 Code Security).

**Recommendation:** Consider using `uint64` for `antiFarmerExpirationTime`, similar to `taxExpirationTime`, to provide a significantly longer operational lifespan and prevent future overflow issues.


### `L-01` — Lack of Event Emission for Tax Rate Changes  *(Severity: Low · Status: Unresolved)*

While `PoolStateChanged` is emitted when the overall pool state changes, there are no explicit events emitted when `buyTaxRate` or `sellTaxRate` are modified within the `_liquidateTax` function (e.g., when the state transitions to `TaxFree` and rates are set to 0). This lack of granular event emission makes it harder for off-chain monitoring systems and users to track precise tax rate changes (7.2 Code Security, 7.8 Operations).

**Recommendation:** Emit specific events (e.g., `TaxRatesChanged(uint16 newBuyTax, uint16 newSellTax)`) whenever `buyTaxRate` or `sellTaxRate` are modified to enhance transparency and off-chain monitoring capabilities.


### `I-01` — Initial Token Distribution Centralization  *(Severity: Informational · Status: Unresolved)*

The `initialize` function mints the entire `maxSupply` (1 billion tokens) to `msg.sender` (the deployer/initializer address). This centralizes the initial token supply entirely with one address, which then bears the responsibility for subsequent distribution. While a common pattern, it concentrates significant power and responsibility (7.4 Economic).

**Recommendation:** Ensure that the address receiving the initial `maxSupply` is a secure, multi-signature wallet or a well-audited distribution contract to mitigate risks associated with a single point of control.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xee22...7777`](https://bscscan.com/address/0xee22fce582dc4120f07e13e42b55ee75246e7777) |
| **Network** | BNB Chain |
| **Price** | $0.0007729 |
| **24h Volume** | $687.0K |
| **Liquidity** | $90.1K |
| **Volume / Liquidity** | 7.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | 17.0% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 6549 buys / 5191 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x33d2e1eeb4d399591c11ac9ad64863fa11678304)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-5696d7-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
