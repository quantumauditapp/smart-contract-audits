---
token: Bankr Kat
ticker: BANKAT
network: base
risk_score: 57
status: medium
date: 2026-09-28
---

# Bankr Kat (BANKAT) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bankr-kat-base)

---

## Audit Summary

The DopplerERC20V1 contract serves as an upgradeable ERC20 token with integrated vesting functionalities and a temporary balance limit mechanism. The audit identified a High-severity issue related to centralized control, two Medium-severity issues concerning token distribution concentration and potential gas inefficiencies, one Low-severity issue regarding event logging, and one Informational finding about initialization complexity. The contract generally demonstrates good code quality, leveraging battle-tested Solady libraries, but critical roles and initial token distribution parameters warrant careful review and potential mitigation strategies.

> **Final Recommendation:** It is strongly recommended to implement robust security measures for the `owner` and `controller` roles, such as multi-signature wallets and potentially time-locks for critical operations, to mitigate the risks associated with centralized control. The project should also re-evaluate the `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` constants to ensure they align with the desired token distribution strategy and avoid excessive concentration. For future upgrades, a detailed storage layout analysis should be performed to prevent potential issues with complex data structures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes Solady libraries (ERC20, Ownable, ERC20Votes, Initializable), which generally contribute to robust code security and gas efficiency. The vesting logic appears sound, calculating… |
| **Governance / Economics** | 2/10 | High | The contract's economic model allows for a highly concentrated initial token distribution. The `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` constants are set to 80% of the initial… |
| **Upgrades** | 7/10 | Low | The contract is designed as an upgradeable implementation, correctly using Solady's `Initializable` and calling `_disableInitializers()` in its constructor. This adheres to the standard proxy pattern… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.0% |
| **Top-3 Unlocked** | ⚠️ 92.1% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control and Single Points of Failure  *(Severity: High · Status: Unresolved)*

The `owner` and `controller` roles in the DopplerERC20V1 contract possess significant power, creating single points of failure. The `owner` can `lockPool`, `unlockPool`, and `updateTokenURI`, which directly impacts token distribution and the balance limit mechanism. The `controller` can `disableBalanceLimit` entirely. If these accounts are compromised, an attacker could manipulate token distribution, bypass balance limits, or alter token metadata, leading to severe financial and reputational damage to the protocol. This directly impacts 7.3 Access Control and 7.5 Governance.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for both the `owner` and `controller` roles to require multiple approvals for critical operations. Consider introducing a time-lock mechanism for highly sensitive functions (e.g., `disableBalanceLimit`, `lockPool`) to provide a window for community review or emergency intervention before changes take effect.


### `M-01` — High Pre-Mint Limits Leading to Concentration Risk  *(Severity: Medium · Status: Unresolved)*

The constants `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` are both set to `0.8 ether`. When used in the `initialize` function's calculations (e.g., `initialSupply * MAX_PRE_MINT_PER_ADDRESS_WAD / WAD`), this effectively allows a single beneficiary to receive up to 80% of the total initial supply as pre-minted tokens, and the total pre-minted amount can also be up to 80% of the initial supply. This high percentage could lead to a highly concentrated token distribution among a few addresses, potentially impacting decentralization, market liquidity, and susceptibility to manipulation. This impacts 7.4 Economic.

**Recommendation:** Review these pre-mint limits to ensure they align with the project's desired token distribution model. If a more decentralized distribution is intended, consider significantly reducing these percentages. Clearly document the rationale if this high concentration is an intentional design choice.


### `M-02` — Potential Gas Inefficiency in `_releaseAllFor` and `getScheduleIdsOf`  *(Severity: Medium · Status: Unresolved)*

The `_scheduleIdsOf` mapping stores an array of `scheduleId`s for each beneficiary. The `_releaseAllFor` function iterates through this array to compute and release tokens for all associated vesting schedules. If a beneficiary accumulates a very large number of individual vesting schedules, this iteration could become gas-intensive, potentially leading to transaction failures or high gas costs for the beneficiary when attempting to claim all their vested tokens. Similarly, the `getScheduleIdsOf` view function could also be expensive to call off-chain if the array is large. This impacts 7.2 Code Security and 7.8 Operations.

**Recommendation:** Consider imposing a reasonable maximum limit on the number of vesting schedules that can be assigned to a single beneficiary. Alternatively, for `_releaseAllFor`, provide an option for beneficiaries to release tokens for specific schedule IDs rather than requiring an iteration over all schedules. For `getScheduleIdsOf`, if it's primarily for off-chain display, ensure front-end applications handle potential gas costs or implement pagination if feasible.


### `L-01` — Incomplete Event Logging for Balance Limit Disablement  *(Severity: Low · Status: Unresolved)*

The `BalanceLimitDisabled` event, emitted when the balance limit is deactivated by the `controller`, only includes a boolean value (`false`) indicating that it's disabled. It does not log the `maxBalanceLimit` or `balanceLimitEnd` values that were active prior to disablement. This omission makes it more challenging for off-chain monitoring and historical analysis to track the exact parameters of the balance limit when it was active and subsequently disabled. This impacts 7.8 Operations.

**Recommendation:** Enhance the `BalanceLimitDisabled` event to include the `maxBalanceLimit` and `balanceLimitEnd` values that were in effect when the balance limit was disabled. This provides a more complete audit trail for the state changes.


### `I-01` — Complex Initialization Function  *(Severity: Informational · Status: Unresolved)*

The `initialize` function takes a large number of parameters, including multiple arrays for vesting schedules and beneficiaries. While necessary for comprehensive initial setup, this complexity increases the risk of human error during deployment, where incorrect parameter ordering or values could lead to unintended configurations. This impacts 7.8 Operations.

**Recommendation:** Ensure thorough testing and multiple independent reviews of the deployment script and all initialization parameters. Consider creating a dedicated deployment script that clearly labels and validates each parameter to minimize the chance of errors. If feasible, for future versions, explore breaking down the initialization into smaller, more focused functions, though this might not be practical for a single `initializer` call.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3351...8ba3`](https://basescan.org/address/0x33515e703c81f054ce6cfd78a3f51f5a94848ba3) |
| **Network** | Base |
| **Price** | $0.00000081 |
| **24h Volume** | $402.3K |
| **Liquidity** | $50.1K |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 18h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2657 buys / 4331 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xfef5a75666cf0bedd84972c4afe1aa2ee06cf0b27fdb680059043db09cc11502)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bankr-kat-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
