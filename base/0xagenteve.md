---
token: 0xAgentEVE
ticker: EVE
network: base
risk_score: 62
status: medium
date: 2026-08-31
---

# 0xAgentEVE (EVE) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/0xagenteve-base)

---

## Audit Summary

The DERC20 token contract implements an ERC20 token with voting, permit, and vesting functionalities, alongside an inflation mechanism. The contract leverages OpenZeppelin libraries for standard components, enhancing code quality. However, the audit identified a critical vulnerability related to potential division by zero in vesting calculations, high centralization risks due to extensive owner privileges over economic parameters, and a medium-severity issue where vesting release could be blocked under specific conditions. Minor issues include an approximation in yearly duration calculations and clarity in constant naming.

> **Final Recommendation:** Address the critical vulnerability by adding a constructor check to ensure `vestingDuration` is a non-zero value. Evaluate the extent of centralized control by the owner; consider implementing a multi-signature wallet or a time-locked governance mechanism for sensitive functions like `updateMintRate` and `unlockPool` to mitigate governance and economic risks. Review the `_update` logic to ensure vesting releases are not inadvertently blocked by the pool locking mechanism, potentially by exempting `address(this)` as the 'from' address in the pool lock check.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract demonstrates a solid architectural foundation by inheriting from OpenZeppelin's ERC20, ERC20Votes, ERC20Permit, and Ownable. This promotes robust code security (7.2) for core token… |
| **Governance / Economics** | 3/10 | High | The contract's economic model (7.4) includes a controlled inflation mechanism and a vesting schedule. The owner has significant centralized control (H-01) over critical economic parameters, including… |
| **Upgrades** | 6/10 | Medium | The DERC20 contract is not designed as an upgradeable proxy (7.7). Therefore, there are no upgrade-specific risks associated with this contract. Any future changes would require a new deployment and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Division by Zero in Vesting Calculation  *(Severity: Critical · Status: Unresolved)*

The `computeAvailableVestedAmount` function calculates vested tokens using `getVestingDataOf[account].totalAmount * (block.timestamp - vestingStart) / vestingDuration`. If `vestingDuration` is initialized to `0` in the constructor, this division will result in a runtime error, preventing any user from releasing their vested tokens. The constructor currently does not include a check to ensure `vestingDuration_` is greater than zero.

**Recommendation:** Add a `require(vestingDuration_ > 0, "Vesting duration must be greater than zero")` check in the constructor to prevent `vestingDuration` from being set to zero.


### `H-01` — Centralized Control over Economic Parameters  *(Severity: High · Status: Unresolved)*

The `owner` role, protected by OpenZeppelin's Ownable, possesses extensive control over critical economic parameters and token supply. The owner can `updateMintRate`, which directly influences the token's inflation, and all tokens minted via `mintInflation()` are sent directly to the owner. Additionally, the owner can `lockPool` and `unlockPool`, controlling transfers to a designated pool address, and `burn` tokens from their own balance. This high degree of centralization introduces significant governance and economic risks, as the protocol's stability and token value are heavily reliant on the owner's actions and security.

**Recommendation:** Consider decentralizing control over sensitive functions. Implement a multi-signature wallet for the owner address or integrate a time-locked governance mechanism (e.g., a DAO) for critical operations like `updateMintRate` and `unlockPool`. This would introduce a delay or require multiple approvals, reducing the risk of a single point of failure or malicious action.


### `M-01` — Vesting Release Denial of Service via Pool Lock  *(Severity: Medium · Status: Unresolved)*

The `release()` function transfers vested tokens from the contract (`address(this)`) to `msg.sender`. The `_update` internal function, which is called during this transfer, includes a check: `if (to == pool && isPoolUnlocked == false) revert PoolLocked();`. If the owner sets a vested recipient's address as the `pool` address using `lockPool()` and then locks the pool, that specific recipient will be unable to call `release()` and receive their vested tokens, leading to a denial of service for their vesting schedule.

**Recommendation:** Modify the `_update` function's `PoolLocked` check to exempt transfers originating from `address(this)` when the `to` address is the `pool`. Alternatively, ensure that the `pool` address cannot be set to an address that has active vesting schedules, or implement a mechanism to allow vested token releases even if the recipient's address is the designated pool and it is locked.


### `L-01` — Inaccurate Yearly Duration Calculation  *(Severity: Low · Status: Unresolved)*

The `mintInflation` function uses a fixed `365 days` (equivalent to `31536000` seconds) to represent a year in its inflation calculations. This approximation does not account for leap years, which occur every four years and add an extra day. Over long periods, this consistent discrepancy will lead to minor inaccuracies in the calculated yearly minting amounts and the overall inflation schedule.

**Recommendation:** While `365 days` is a common approximation in smart contracts, for precise long-term economic models, consider acknowledging this limitation in documentation or exploring more dynamic ways to account for leap years if extreme precision is required. For most DeFi applications, this level of approximation is acceptable but should be noted.


### `I-01` — Clarity of Percentage Constants Using 'ether' Unit  *(Severity: Informational · Status: Unresolved)*

Constants like `MAX_PRE_MINT_PER_ADDRESS_WAD` and `MAX_TOTAL_PRE_MINT_WAD` are defined as `0.1 ether`. While mathematically correct for representing 10% when divided by `1 ether` (e.g., `amount * 0.1 ether / 1 ether`), the use of the `ether` unit can be slightly misleading as these values represent fractions/percentages rather than actual Ether amounts. This might cause confusion for developers unfamiliar with this specific Solidity idiom.

**Recommendation:** For improved clarity, consider defining these constants using explicit `uint256` values that represent the desired percentage with 18 decimals, e.g., `uint256 constant MAX_PRE_MINT_PER_ADDRESS_PERCENT = 1e17;` (for 10%) or `uint256 constant MAX_PRE_MINT_PER_ADDRESS_BPS = 1000;` (for 10% if using basis points out of 10000). This makes the intent immediately clear without relying on the `ether` unit as a scaling factor.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe7d1...1ba3`](https://basescan.org/address/0xe7d192e52fa418236d6eecf7d5eb38da9dd11ba3) |
| **Network** | Base |
| **Price** | $0.00000158 |
| **24h Volume** | $23.7K |
| **Liquidity** | $99.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 63.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1529 buys / 1214 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x935697dd4a8170092be90b538d3bfb34d0af3429b93f4b1c589abe921a09c22e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/0xagenteve-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
