---
token: Alberich Token
ticker: ALBRH
network: ethereum
risk_score: 54
status: medium
date: 2026-09-02
---

# Alberich Token (ALBRH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/alberich-token-eth)

---

## Audit Summary

The AlberichToken contract implements an ERC20 token with integrated sale, snapshot, and vesting capabilities, leveraging OpenZeppelin's battle-tested libraries for core functionalities. The contract exhibits a high degree of centralization, with the 'FOUNDATION_ROLE' controlling critical parameters and operations. While standard security patterns like reentrancy guards and pausing are correctly applied, the vesting mechanism's full implementation and management of 'reservedForVesting' are not visible in the provided code, posing a potential risk. The contract is not upgradeable, ensuring immutability but limiting future flexibility.

> **Final Recommendation:** Strengthen the security posture by completing and thoroughly auditing the vesting mechanism, ensuring `reservedForVesting` is accurately managed throughout the token lifecycle. Consider implementing a multi-signature wallet for the `FOUNDATION_ROLE` and `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control. Clearly document the operational procedures and responsibilities for these critical roles.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for ERC20, access control, pausing, and reentrancy protection, enhancing code security (7.2). Standard Solidity 0.8.20 features prevent… |
| **Governance / Economics** | 4/10 | Medium | The contract exhibits a highly centralized governance and economic model, with the `FOUNDATION_ROLE` (and `DEFAULT_ADMIN_ROLE`) possessing extensive control over all critical parameters (7.3, 7.4).… |
| **Upgrades** | 7/10 | Low | The contract is not designed with an upgradeability pattern (7.7), meaning its logic is immutable once deployed. This eliminates risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Extensive Centralization of Control  *(Severity: High · Status: Unresolved)*

The `FOUNDATION_ROLE` (and implicitly `DEFAULT_ADMIN_ROLE`) holds extensive power over critical contract functions, including setting token sale parameters (`setTokenPriceWeiPerToken`, `setPurchaseLimits`, `setSaleActive`), managing the whitelist (`setWhitelist`), withdrawing all accumulated ETH (`withdrawETH`), burning tokens (`ringForgedBurn`), and pausing the contract. This centralizes trust in a single entity or a small group of individuals, introducing a significant single point of failure. A compromise of the foundation's private key or malicious intent could lead to severe consequences, such as draining funds, manipulating token prices, or halting the sale.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `FOUNDATION_ROLE` and `DEFAULT_ADMIN_ROLE` to distribute control and require multiple approvals for critical operations. This significantly reduces the risk associated with a single point of failure. Clearly define and communicate the responsibilities and operational procedures for these roles.


### `M-01` — Incomplete Vesting Logic and `reservedForVesting` Management  *(Severity: Medium · Status: Unresolved)*

The provided contract code includes a `Vesting` struct, a `vestings` mapping, and a `reservedForVesting` state variable, which is crucial for managing token supply during sales by excluding vested tokens from the `unlockedBalance`. However, the functions responsible for creating vestings, claiming vested tokens, and critically, updating `reservedForVesting` are truncated. Without the full implementation of these functions, the integrity of the vesting mechanism and the accuracy of `unlockedBalance` in `_purchase` cannot be fully assessed. This could lead to scenarios where tokens intended for vesting are prematurely sold, or tokens become permanently locked if `reservedForVesting` is not co…

**Recommendation:** Provide the complete implementation of all vesting-related functions, including `createVesting`, `claimVestedTokens`, and any internal logic that updates `reservedForVesting`. Ensure that `reservedForVesting` is accurately incremented when vesting schedules are created and decremented precisely when vested tokens are claimed, preventing discrepancies in the `unlockedBalance` calculation.


### `L-01` — Redundant Access Control Check  *(Severity: Low · Status: Unresolved)*

The `onlyFoundation` modifier checks both `require(msg.sender == foundation, "not foundation")` and `_checkRole(FOUNDATION_ROLE, msg.sender)`. In the constructor, `msg.sender` is granted both `DEFAULT_ADMIN_ROLE` and `FOUNDATION_ROLE`, and `foundation` is set to `msg.sender`. While a foundation transfer mechanism is implied by events, if the `foundation` address is always expected to possess the `FOUNDATION_ROLE`, one of these checks becomes redundant. This does not introduce a vulnerability but adds unnecessary gas cost and complexity.

**Recommendation:** Consider simplifying the `onlyFoundation` modifier. If the `foundation` address is strictly managed to always hold the `FOUNDATION_ROLE`, then `_checkRole(FOUNDATION_ROLE, msg.sender)` should suffice, as `AccessControl` handles role management robustly. Alternatively, if `foundation` can be an address without the role, the current dual check is appropriate but should be clearly documented.


### `I-01` — Irreversible Parameter Freezing  *(Severity: Informational · Status: Unresolved)*

The `freezeParameters()` function, callable by the `foundation`, permanently sets `parametersFrozen` to `true`. Once frozen, critical token sale parameters such as `tokenPriceWeiPerToken`, `shoPurchaseLimit`, `publicPurchaseLimit`, and `minTokensPerPurchase` cannot be changed. While this provides certainty and immutability for sale conditions post-freeze, it removes all flexibility for future adjustments, even in unforeseen circumstances or market changes.

**Recommendation:** This is a design choice. Ensure that the implications of irreversible parameter freezing are fully understood and accepted by the project stakeholders. Clearly communicate this immutability to potential participants. If any flexibility is desired, consider alternative designs that allow for limited, time-gated, or governance-approved parameter adjustments.


### `I-02` — Initial Price Setting Flexibility  *(Severity: Informational · Status: Unresolved)*

The `foundation` has the ability to set the `tokenPriceWeiPerToken` to any non-zero value via `setTokenPriceWeiPerToken()` before `freezeParameters()` is called. This grants significant control over the initial token valuation and sale terms. While this is an intended feature for initial setup, it means the foundation can unilaterally determine the token's price before the sale parameters are locked.

**Recommendation:** Ensure transparency regarding the initial token price setting process. Clearly communicate the mechanism and timing of price finalization to the community. Consider publishing the intended price well in advance or using a pre-determined, auditable pricing formula if greater decentralization or trustlessness is desired.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7adb...b998`](https://etherscan.io/address/0x7adbfd873084db714a57ed648ee69aa4627cb998) |
| **Network** | Ethereum |
| **Price** | $0.0001248 |
| **24h Volume** | $74.6K |
| **Liquidity** | $292.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 21d |
| **Top-10 Holders** | 99.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 197 buys / 167 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd227d3d4602f4037839fff79dc5fd80e9cc45b4e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/alberich-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
