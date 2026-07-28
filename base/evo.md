---
token: evo
ticker: EVO
network: base
risk_score: 59
status: high
date: 2026-07-28
---

# evo (EVO) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/evo-base)

---

## Audit Summary

The DERC20 token contract implements standard ERC20 functionalities along with custom features for vesting, inflation, and a pool locking mechanism. The contract leverages OpenZeppelin libraries for robust base implementations. However, the audit identified two high-severity issues: an inverted logic for pool locking with a misleading error message, and the complete absence of a function to release vested tokens, rendering a core feature non-functional. Minor issues include precision loss in inflation calculations and a restrictive constructor check. The contract also exhibits a high degree of centralization under the owner's control.

> **Final Recommendation:** It is critical to address the high-severity issues identified, particularly the inverted pool locking logic and the missing vesting release function, to ensure the contract functions as intended and provides expected utility to users. Implement the `releaseVestedTokens` function to enable beneficiaries to claim their vested tokens. Correct the `_beforeTokenTransfer` logic and its associated error message to accurately reflect the intended pool transfer restrictions. Consider the implications of integer division for inflation calculations and evaluate if a more precise approach is necessary for the project's economic model. Review the constructor's vesting limit to ensure it aligns with the project's token distribution strategy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC20, ERC20Votes, ERC20Permit, and Ownable, providing a strong foundation (7.2 Code Security). Custom error messages enhance clarity.… |
| **Governance / Economics** | 2/10 | High | The contract's economic model includes a capped yearly inflation rate, preventing excessive token dilution (7.4 Economic). The owner has control over critical parameters like `yearlyMintRate` and can… |
| **Upgrades** | 7/10 | Low | The DERC20 contract is implemented as a standalone, non-upgradeable contract. Therefore, it does not introduce any specific upgrade-related risks (7.7 Upgrades). Any future changes would require a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟢 2 Low · ⚪ 2 Informational_

### `H-01` — Inverted Logic and Misleading Error Message for Pool Locking  *(Severity: High · Status: Unresolved)*

The `_beforeTokenTransfer` hook contains logic `if (from == pool && !isPoolUnlocked) { revert PoolLocked(); }`. This prevents tokens from being transferred *from* the `pool` address when the pool is locked. However, the associated error message `PoolLocked()` states: 'Thrown when trying to transfer tokens into the pool while it is locked'. This discrepancy indicates either an inverted logic (if the intent was to prevent transfers *into* the pool) or a misleading error message (if the intent was to prevent transfers *from* the pool). If the former, the intended protection against transfers *into* the pool is completely bypassed.

**Recommendation:** Clarify the intended behavior for pool locking. If the goal is to prevent transfers *into* the pool, modify the condition to `if (to == pool && !isPoolUnlocked)`. If the goal is to prevent transfers *from* the pool, update the `PoolLocked()` error message to accurately reflect this, e.g., 'Thrown when trying to transfer tokens from the pool while it is locked'.


### `H-02` — Missing Vesting Token Release Functionality  *(Severity: High · Status: Unresolved)*

The contract defines a comprehensive vesting mechanism, including `vestingStart`, `vestingDuration`, `vestedTotalAmount`, and a `getVestingDataOf` mapping to track individual vesting data. However, the crucial `releaseVestedTokens` function (or any equivalent public/external function allowing beneficiaries to claim their vested tokens) is entirely absent from the provided source code. This renders the entire vesting system non-functional, preventing beneficiaries from accessing their vested tokens after the vesting period.

**Recommendation:** Implement a `releaseVestedTokens` function that allows users to claim their vested tokens based on the `vestingStart`, `vestingDuration`, and `getVestingDataOf` records. This function should calculate the releaseable amount, transfer tokens from the contract's balance to the claimant, and update the `releasedAmount` in `getVestingDataOf`.


### `L-01` — Precision Loss in Inflation Calculation  *(Severity: Low · Status: Unresolved)*

The `mintInflation` function calculates `yearMint` and `partialYearMint` using integer division: `(supply * yearlyMintRate_ * timeLeftInCurrentYear) / (1 ether * 365 days)`. Integer division truncates any fractional token amounts, leading to a slight under-minting of tokens compared to a precise floating-point calculation. While common in Solidity, this precision loss can accumulate over time and result in a minor deviation from the intended inflation schedule.

**Recommendation:** Consider using a fixed-point math library or adjusting the calculation methodology to minimize precision loss if exact inflation amounts are critical. Alternatively, acknowledge this behavior as an acceptable trade-off for gas efficiency and simplicity in the project's documentation.


### `L-02` — Constructor Vesting Limit Logic  *(Severity: Low · Status: Unresolved)*

The constructor includes a check `require(vestedTokens < initialSupply, MaxTotalVestedExceeded(vestedTokens, initialSupply));`. This condition prevents the entire `initialSupply` from being allocated to vested tokens, requiring at least one wei to be sent to the `recipient` via `_mint(recipient, initialSupply - vestedTokens)`. If the intention was to allow full initial supply vesting, this check imposes an unnecessary restriction. Additionally, the error message 'MaxTotalVestedExceeded' implies `vestedTokens > initialSupply` rather than `>= initialSupply`, which could be confusing.

**Recommendation:** Review the project's token distribution strategy to confirm if `vestedTokens` should be allowed to equal `initialSupply`. If so, change the condition to `vestedTokens <= initialSupply`. Also, consider refining the error message for clarity if the current behavior is intended.


### `I-01` — Centralized Control by Owner  *(Severity: Informational · Status: Unresolved)*

The contract's `Ownable` pattern grants the deployer (owner) significant control over critical functions. The owner can `lockPool`, `unlockPool`, `burn` tokens, and `updateMintRate`. While `mintInflation` is public, it mints all inflation tokens directly to the owner. This centralization introduces a single point of failure and relies heavily on the owner's trustworthiness and operational security.

**Recommendation:** For enhanced decentralization and security, consider implementing a multi-signature wallet for ownership or transitioning to a decentralized autonomous organization (DAO) governance model for critical functions. If centralization is intended, ensure robust operational security measures are in place for the owner's private key.


### `I-02` — BUSL-1.1 License Usage  *(Severity: Informational · Status: Unresolved)*

The contract is licensed under the Business Source License 1.1 (BUSL-1.1). This is a non-open-source license with specific usage restrictions, typically allowing free use for non-production purposes but requiring a commercial license for production use after a certain time period. While not a security vulnerability, this has significant implications for project adoption, integration, and legal compliance for users and developers.

**Recommendation:** Ensure all users and integrators of the DERC20 contract are fully aware of the BUSL-1.1 licensing terms and their implications. Clearly communicate the licensing model in project documentation and any public-facing materials.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x721b...bba3`](https://basescan.org/address/0x721b072dbb616f29eea73ac004e03fd4e884bba3) |
| **Network** | Base |
| **Price** | $0.00000261 |
| **24h Volume** | $174.5K |
| **Liquidity** | $202.6K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 48.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 413 buys / 260 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xd8ee119a65d3a902ced4ef7693b98e62a7fbb1d7808a693dbb6961d7f544fb80)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/evo-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-28*
