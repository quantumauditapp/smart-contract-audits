---
token: Field Atlas
ticker: ATLAS
network: base
risk_score: 38
status: medium
date: 2026-09-27
---

# Field Atlas (ATLAS) — Smart Contract Security Analysis | Base

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/field-atlas-base)

---

## Audit Summary

The DopplerERC20V1 contract implements an ERC20 token with vesting functionalities and a balance limit mechanism. The audit identified a Medium overall risk level, primarily due to hardcoded tokenomic parameters, centralized control over the balance limit, and potential upgrade safety concerns related to storage slot management. The contract leverages Solady libraries, demonstrating good code quality and adherence to upgradeability patterns, but specific design choices introduce inflexibility and single points of control.

> **Final Recommendation:** It is recommended to review the immutability of key tokenomic parameters and consider implementing mechanisms for their adjustment through a robust governance process. Strengthen the security of the `controller` role, ideally by assigning it to a multisig or a time-locked contract. For future upgrades, carefully manage storage slots, especially when using libraries that rely on fixed slots for persistent data, to prevent potential collisions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices, utilizing battle-tested Solady libraries for ERC20, Ownable, and Initializable functionalities, which enhances code security (7.2 Code Security).… |
| **Governance / Economics** | 4/10 | Medium | The protocol implements a vesting mechanism with configurable schedules, ensuring controlled token distribution (7.4 Economic). Access control for critical functions like pool locking and token URI… |
| **Upgrades** | 7/10 | Low | The contract is designed as an upgradeable proxy implementation, correctly using Solady's `Initializable` and disabling its constructor (7.7 Upgrades). This pattern allows for future enhancements and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 22.9% |
| **Top-3 Unlocked** | 55.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control by Controller Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `controller` address possesses the sole authority to call `disableBalanceLimit()`, which completely deactivates the balance limit mechanism. If this `controller` address is compromised or acts maliciously, it can bypass a core security feature designed to restrict token holdings, potentially leading to unintended token distribution or market manipulation (7.3 Access Control, 7.5 Governance). While the `owner` is a multisig, the `controller`'s ownership is not specified as such.

**Recommendation:** Enhance the security of the `controller` role. It is strongly recommended to assign this role to a multi-signature wallet or a time-locked contract to introduce a delay or require multiple approvals for critical actions, thereby mitigating the risk of a single point of failure.


### `M-02` — Potential Storage Collision with LibTransient for Persistent State  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `LibTransient` library is used to track persistent state (`_hasTransientSchedule`) via a fixed storage slot (`HAS_SCHEDULE_TRANSIENT_SLOT`). While `LibTransient` is typically intended for transient (single-transaction) data, its application here for persistent tracking of beneficiary schedules introduces a risk. In an upgradeable proxy environment, if a future contract upgrade introduces a new state variable that happens to occupy the same storage slot as `HAS_SCHEDULE_TRANSIENT_SLOT`, it could lead to a storage collision, corrupting data or causing unexpected contract behavior (7.7 Upgrades).

**Recommendation:** Re-evaluate the use of `LibTransient` for persistent state. For persistent data, it is safer to use standard Solidity state variables or a dedicated storage pattern that guarantees unique storage slots. If `LibTransient` must be used, ensure that the chosen slot is explicitly reserved and documented, and that all future upgrades are meticulously checked for potential storage collisions with this slot.


### `M-03` — Inflexible Hardcoded Constants for Tokenomics  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract utilizes several hardcoded constants for critical tokenomic parameters, including `MAX_PRE_MINT_PER_ADDRESS_WAD`, `MAX_TOTAL_PRE_MINT_WAD`, and `MIN_VESTING_DURATION`. Additionally, `maxBalanceLimit` is set during initialization and cannot be subsequently modified. This design choice significantly limits the protocol's flexibility to adapt to evolving market conditions, adjust token distribution strategies, or modify vesting terms without requiring a full contract upgrade (7.4 Economic).

**Recommendation:** Consider making critical tokenomic parameters configurable by the owner or a governance mechanism. This could involve adding setter functions for `maxBalanceLimit` (with appropriate access control and potentially a timelock) and allowing for the creation of new vesting schedules with different `MIN_VESTING_DURATION` or other parameters. For pre-mint caps, if flexibility is desired, they could be made adjustable or removed if no longer necessary.


### `L-01` — Complex Initialization Function  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function accepts a large number of parameters, including multiple arrays for vesting schedules, beneficiaries, and amounts. This complexity increases the likelihood of human error during deployment, potentially leading to incorrect initial configurations, misconfigured vesting schedules, or missed exclusions from the balance limit (7.1 Architecture, 7.8 Operations).

**Recommendation:** Consider breaking down the initialization into smaller, more manageable functions if feasible, or provide comprehensive deployment scripts and clear documentation. Implement robust pre-deployment checks and simulations to verify the correctness of all parameters before actual deployment.


### `I-01` — Unused `pool` Variable After Locking  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `pool` address is set and `isPoolLocked` is activated in `lockPool()`, and the `pool` address is explicitly excluded from the balance limit. However, the `pool` variable itself is not directly referenced or utilized in any further internal logic within the provided contract code. While its exclusion from the balance limit is a functional effect, the variable's lack of direct interaction elsewhere might indicate incomplete functionality or a design choice where its purpose is purely external to this contract's internal logic (7.1 Architecture).

**Recommendation:** Clarify the intended purpose and interaction of the `pool` variable. If it's solely for external reference and balance limit exclusion, this can be documented. If it's meant to be used internally, ensure all intended functionalities are implemented.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb462...7ba3`](https://basescan.org/address/0xb462a5039a540883508ee37b5cf3999647557ba3) |
| **Network** | Base |
| **Price** | $0.00000167 |
| **24h Volume** | $660.3K |
| **Liquidity** | $82.7K |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 10h |
| **Top-10 Holders** | 62.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3874 buys / 6172 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x73184f3f24a9993aeb4ae040e36997dfe2e927a6742bbb1f24706c421f527330)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/field-atlas-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*
