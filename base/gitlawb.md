---
token: gitlawb
ticker: GITLAWB
network: base
risk_score: 46
status: high
date: 2026-07-29
---

# gitlawb (GITLAWB) — Smart Contract Security Analysis | Base

> **Risk Score: 46/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gitlawb-base)

---

## Audit Summary

The DERC20 token contract implements an ERC20 token with voting, permit, and Ownable features. It includes a vesting mechanism for initial token distribution and a time-based inflation mechanism controlled by the owner. While the contract utilizes standard OpenZeppelin libraries and includes custom error handling, a critical vulnerability was identified where vested tokens are minted to the contract but cannot be released to recipients due to a missing function. Additionally, the pool locking mechanism is non-functional, and significant centralized control by the owner poses economic risks.

> **Final Recommendation:** It is critical to implement a public function allowing vested token recipients to claim their allocated amounts. Without this, the vesting mechanism is entirely non-functional. Additionally, the pool locking mechanism should either be removed or fully implemented to enforce transfer restrictions as intended. Consider implementing a multi-signature wallet for the `owner` role to mitigate the risks associated with centralized control over critical functions like inflation minting and rate updates.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The DERC20 contract demonstrates good architectural practices by inheriting from battle-tested OpenZeppelin contracts (ERC20, ERC20Votes, ERC20Permit, Ownable) and utilizing custom error messages for… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralized control, as the `owner` role, inherited from Ownable, possesses significant power (7.3 Access Control, 7.5 Governance). The owner can mint inflation… |
| **Upgrades** | 6/10 | Medium | The provided contract is not implemented as an upgradeable proxy. Therefore, upgradeability risks are not applicable to this specific deployment. Any changes to the contract logic would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `C-01` — Missing Vesting Release Functionality  *(Severity: Critical · Status: Unresolved)*

The constructor mints `vestedTokens` to `address(this)` (the contract itself) for later distribution to recipients based on `getVestingDataOf` and `vestingStart`/`vestingDuration`. However, there is no public function provided in the contract that allows these recipients to claim or release their vested tokens after the vesting period has started or ended. This renders the entire vesting mechanism non-functional, as tokens are locked in the contract indefinitely.

**Recommendation:** Implement a `release` or `claimVestedTokens` function that allows recipients to claim their vested tokens. This function should calculate the amount of tokens eligible for release based on `block.timestamp`, `vestingStart`, `vestingDuration`, `totalAmount`, and `releasedAmount` in `getVestingDataOf`, and then transfer the calculated amount to the recipient. Ensure proper checks to prevent releasing more than `totalAmount` or before `vestingStart`.


### `H-01` — Non-functional Pool Locking Mechanism  *(Severity: High · Status: Unresolved)*

The contract includes `lockPool` and `unlockPool` functions that set the `pool` address and toggle the `isPoolUnlocked` boolean. The stated purpose is to prevent tokens from being transferred into the pool while locked. However, the standard ERC20 `_transfer` function (inherited from OpenZeppelin) does not check the `isPoolUnlocked` state or the `pool` address. Consequently, tokens can still be transferred to the designated `pool` address even when `isPoolUnlocked` is `false`, making the locking mechanism entirely ineffective.

**Recommendation:** To make the pool locking mechanism functional, override the `_transfer` function (or a similar internal transfer function) to include a check. If `isPoolUnlocked` is `false`, prevent transfers where the `to` address is the `pool` address. Alternatively, if this feature is not critical, remove the `pool`, `isPoolUnlocked`, `lockPool`, and `unlockPool` variables and functions to reduce complexity and potential for misunderstanding.


### `H-02` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `owner` of the contract, as defined by the `Ownable` pattern, has extensive control over critical token parameters and supply. The owner can call `mintInflation()` to mint new tokens to themselves, `burn()` tokens from their own address, `lockPool()`/`unlockPool()`, and `updateMintRate()` to change the yearly inflation rate. This high degree of centralization introduces significant governance and economic risks, as a compromised owner key or a malicious owner could manipulate the token supply and value without community consensus.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` role to distribute control and require multiple approvals for critical operations. For `updateMintRate`, consider adding a time-lock mechanism or a governance vote to allow the community to react to proposed changes. For `mintInflation`, consider making it callable by a neutral, audited contract or a DAO, rather than directly by the owner.


### `M-01` — Precision Loss in Inflation Calculation  *(Severity: Medium · Status: Unresolved)*

The `mintInflation` function calculates `yearMint` and `partialYearMint` using integer division: `(supply * yearlyMintRate_ * time) / (1 ether * 365 days)`. While `yearlyMintRate_` is expressed in WAD (1 ether = 10^18), integer division inherently truncates decimal parts. For very small `supply` values, very low `yearlyMintRate_`, or short time periods, this could lead to a minor loss of precision in the minted amount, potentially resulting in slightly less inflation than mathematically precise calculations would yield.

**Recommendation:** While often acceptable for inflation mechanisms, if high precision is paramount, consider using a fixed-point math library or adjusting the calculation order to minimize truncation effects. For example, ensure the numerator is as large as possible before the final division. However, given the yearly nature of the rate, the current approach is likely sufficient for practical purposes, but the minor precision loss should be acknowledged.


### `L-01` — Confusing `MaxTotalVestedExceeded` Requirement  *(Severity: Low · Status: Unresolved)*

In the constructor, the `require(vestedTokens < initialSupply, MaxTotalVestedExceeded(...));` check enforces that the total amount of tokens designated for vesting (`vestedTokens`) must be strictly less than the `initialSupply`. This means it's impossible to vest the entire `initialSupply`, as at least one token must always go to the `recipient` specified in the constructor. The error message `MaxTotalVestedExceeded` implies exceeding a maximum, but the condition prevents `vestedTokens` from even reaching `initialSupply`, which might be an unintended restriction or confusing given the error name.

**Recommendation:** Clarify the design intent. If it is acceptable for `vestedTokens` to equal `initialSupply` (meaning all initial tokens are vested), change the condition to `vestedTokens <= initialSupply`. If the current strict inequality is intentional, consider renaming the error or adding a comment to explain why `vestedTokens` must always be less than `initialSupply`.


### `L-02` — Hardcoded `PERMIT_2` Address  *(Severity: Low · Status: Unresolved)*

The `PERMIT_2` contract address (`0x000000000022D473030F116dDEE9F6B43aC78BA3`) is hardcoded as a constant. While this is a standard and widely used address for Permit2, hardcoding it means that if the canonical Permit2 contract were to change in the future (e.g., due to an upgrade or a critical bug requiring a new deployment), this contract would not be able to interact with the new address without a redeployment.

**Recommendation:** Consider making the `PERMIT_2` address configurable by the owner or through a governance mechanism. This would allow for flexibility in case the canonical Permit2 address needs to be updated in the future. For non-upgradeable contracts, this might be less critical, but it's a good practice for long-lived protocols.


### `I-01` — Lack of Events for Critical Actions  *(Severity: Informational · Status: Unresolved)*

Several critical state-changing functions, such as `mintInflation()`, `burn()`, `lockPool()`, `unlockPool()`, and `updateMintRate()`, do not emit corresponding events. Emitting events is crucial for off-chain monitoring, indexing, and providing transparency into the contract's operations. Without events, it is difficult for users, block explorers, and external systems to track these significant actions.

**Recommendation:** Emit events for all critical state-changing actions. For example, `MintInflation(address indexed minter, uint256 amount)`, `TokensBurned(address indexed burner, uint256 amount)`, `PoolLocked(address indexed poolAddress)`, `PoolUnlocked(address indexed poolAddress)`, and `MintRateUpdated(uint256 oldRate, uint256 newRate)`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5f98...dba3`](https://basescan.org/address/0x5f980dcfc4c0fa3911554cf5ab288ed0eb13dba3) |
| **Network** | Base |
| **Price** | $0.00002067 |
| **24h Volume** | $163.5K |
| **Liquidity** | $1.10M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 35.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 228 buys / 353 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xec33256bf1ded407a57fd3c1965e7556e42ac14db09bc4e6fef57d5e2eb0b0b9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gitlawb-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-29*
