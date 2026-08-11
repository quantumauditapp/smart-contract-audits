---
token: Staked USDe
ticker: SUSDE
network: ethereum
risk_score: 58
status: high
date: 2026-08-11
---

# Staked USDe (SUSDE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/staked-usde-eth)

---

## Audit Summary

The StakedUSDeV2 contract implements a staking mechanism with a cooldown period, building upon the StakedUSDe contract which provides ERC4626 vault functionality, reward distribution, and a robust access control system. The contract utilizes OpenZeppelin libraries for security primitives like `ReentrancyGuard` and `AccessControl`. Key findings include the significant power of the `DEFAULT_ADMIN_ROLE`, a dependency on an external `USDeSilo` contract, and minor limitations regarding data types and precision.

> **Final Recommendation:** It is crucial to ensure that the `DEFAULT_ADMIN_ROLE` is secured by a robust multi-signature wallet with a timelock, as indicated by the provided deployment information. A comprehensive audit of the `USDeSilo` contract is highly recommended to ensure the security of funds held during the cooldown period. Additionally, clear documentation of administrative capabilities and operational procedures will enhance the overall security posture of the protocol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical architecture (7.1 Architecture) is well-structured, leveraging inheritance and OpenZeppelin standards. Code security (7.2 Code Security) is enhanced by `ReentrancyGuard` in critical… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4 Economic) includes a cooldown mechanism for unstaking, a vesting period for rewards, and a blacklisting feature. Access control (7.3 Access Control) is robust, with a… |
| **Upgrades** | 5/10 | Medium | The contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no specific upgrade-related risks associated with proxy patterns. Any future changes to the contract logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 73.9% |
| **Top-3 Unlocked** | ⚠️ 97.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control by DEFAULT_ADMIN_ROLE  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` in `SingleAdminAccessControl` and `StakedUSDe` possesses extensive control over critical contract parameters and operations. This includes the ability to set `cooldownDuration` (effectively disabling cooldowns), add/remove users from blacklists, rescue arbitrary ERC20 tokens (excluding the asset token), and redistribute locked amounts from full-restricted stakers. While a 2-step transfer mechanism is implemented for the admin role, a compromise of this single role could lead to significant financial loss or protocol manipulation. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Ensure the `DEFAULT_ADMIN_ROLE` is controlled by a robust multi-signature wallet with a timelock, as indicated by the prefill data. Implement strict operational procedures and multi-party approvals for any sensitive actions taken by this role. Consider further decentralizing control over time if feasible.


### `M-01` — Dependency on USDeSilo Contract Security  *(Severity: Medium · Status: Unresolved)*

The `StakedUSDeV2` contract relies on the `USDeSilo` contract to temporarily hold user funds during the cooldown period. The `USDeSilo` contract is deployed by `StakedUSDeV2`'s constructor, making its address immutable. The security and correctness of `USDeSilo` are paramount, as any vulnerability in `USDeSilo` (e.g., reentrancy, unauthorized withdrawals, or incorrect accounting) could directly impact the safety of funds in `StakedUSDeV2`. The code for `USDeSilo` was not provided for this audit. (7.6 External, 7.1 Architecture)

**Recommendation:** Conduct a thorough and independent security audit of the `USDeSilo` contract to ensure it is secure, correctly handles asset transfers, and does not introduce any unexpected behaviors or vulnerabilities. Verify that its withdrawal logic is robust and cannot be exploited.


### `L-01` — `UserCooldown` `underlyingAmount` Type Limitation  *(Severity: Low · Status: Unresolved)*

The `underlyingAmount` in the `UserCooldown` struct is defined as `uint152`. While `uint152` can hold a very large value (~1.6 * 10^45), it is smaller than `uint256`, which is the standard type for ERC20 token balances. If a single user attempts to put an amount of assets into cooldown that exceeds `type(uint152).max`, the explicit cast `uint152(assets)` in `cooldownAssets` or `cooldownShares` would revert. This acts as a safety measure, but it represents a hard limit on the maximum amount a single user can put into cooldown. (7.2 Code Security)

**Recommendation:** Document this limitation clearly for users and administrators. If there is a theoretical possibility of users needing to cooldown amounts larger than `uint152` can hold, consider using `uint256` for `underlyingAmount` to remove this constraint, acknowledging the slight increase in storage costs.


### `I-01` — Precision Loss in Vesting Calculation  *(Severity: Informational · Status: Unresolved)*

The `getUnvestedAmount()` function calculates the currently unvested portion of rewards using integer division: `(deltaT * vestingAmount) / VESTING_PERIOD`. This calculation can suffer from precision loss, especially if `vestingAmount` is small relative to `VESTING_PERIOD`. This might lead to a slight underestimation of the unvested amount over time, potentially leaving a tiny residual amount unvested. (7.4 Economic)

**Recommendation:** Acknowledge this inherent characteristic of integer arithmetic. For most practical purposes, the impact is negligible. If higher precision is deemed critical for the vesting mechanism, consider using a fixed-point math library, though this would add complexity and increase gas costs.


### `I-02` — Cooldown Bypass via Admin Control  *(Severity: Informational · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has the ability to set `cooldownDuration` to 0 via the `setCooldownDuration` function. When `cooldownDuration` is 0, the `ensureCooldownOff` modifier allows direct `withdraw` and `redeem` calls, effectively bypassing the cooldown mechanism. Additionally, the `unstake` function also allows immediate withdrawal if `cooldownDuration == 0`. This is an intended design choice, granting the admin the ability to disable cooldowns. (7.3 Access Control, 7.4 Economic)

**Recommendation:** Ensure this functionality is well-understood and clearly documented as a powerful administrative control. Any changes to `cooldownDuration` should follow strict governance procedures and be communicated transparently to users.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9d39...3497`](https://etherscan.io/address/0x9d39a5de30e57443bff2a8307a4256c8797a3497) |
| **Network** | Ethereum |
| **Price** | $1.2400 |
| **24h Volume** | $3.57M |
| **Liquidity** | $12.29M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 81.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 97 buys / 105 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xb20351bcf606dcc3525d2ed36760a86a5dec7423b77d41125bd4a416ba93448b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/staked-usde-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
