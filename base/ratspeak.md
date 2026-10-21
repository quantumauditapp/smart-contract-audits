---
token: Ratspeak
ticker: RATSPEAK
network: base
risk_score: 80
status: high
date: 2026-08-30
---

# Ratspeak (RATSPEAK) — Smart Contract Security Analysis | Base

> **Risk Score: 80/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ratspeak-base)

---

## Audit Summary

The DERC20 token contract implements standard ERC20 functionality with extensions for voting, permit, and ownership. It includes custom features for token vesting, an inflation mechanism, and a configurable pool lock. The audit identified a critical vulnerability related to potential division by zero in the vesting calculation, which could render vested tokens unclaimable. High-severity issues include significant owner control over token supply inflation and the ability to arbitrarily lock/unlock transfers to a designated pool address. Several medium and low-severity findings highlight design considerations and minor inefficiencies.

> **Final Recommendation:** Address the critical division-by-zero vulnerability by adding a `require` check for `vestingDuration_ > 0` in the constructor. Consider decentralizing control over inflation and pool locking mechanisms, potentially through a multi-signature wallet or a time-locked governance contract, to reduce single points of failure and enhance trust. Clearly document the purpose of the `tokenURI` field for an ERC20 token to avoid confusion. Ensure users are fully aware of the implications of granting infinite allowance to `PERMIT_2`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages OpenZeppelin libraries for core ERC20 functionality, contributing to a robust foundation (7.2 Code Security). The custom vesting and inflation mechanisms are generally… |
| **Governance / Economics** | 2/10 | High | The contract design grants significant centralized control to the owner (7.5 Governance). The owner can control the `yearlyMintRate` (within a cap) and is the sole recipient of all minted inflation… |
| **Upgrades** | 6/10 | Medium | The DERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). Its core logic and state variables are immutable once deployed, which eliminates upgrade-related risks such as storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 84.4% |
| **Top-3 Unlocked** | ⚠️ 99.4% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 2 Low_

### `C-01` — Division by Zero in Vesting Calculation  *(Severity: Critical · Status: Unresolved)*

The `computeAvailableVestedAmount` function performs a division by `vestingDuration`. If `vestingDuration` is initialized to `0` in the constructor, any call to `computeAvailableVestedAmount` (and consequently `release()`) will result in a division-by-zero error, making all vested tokens permanently unclaimable. The constructor currently lacks a check to ensure `vestingDuration_` is greater than zero.

**Recommendation:** Add a `require(vestingDuration_ > 0, "Vesting duration must be positive")` check in the constructor to prevent `vestingDuration` from being set to zero.


### `H-01` — Centralized Control Over Token Inflation  *(Severity: High · Status: Unresolved)*

The `mintInflation()` function, which controls the token's supply expansion, mints all new tokens exclusively to the `owner()`. Additionally, the `updateMintRate()` function, which sets the `yearlyMintRate`, is restricted to `onlyOwner`. This grants the contract owner significant centralized control over the token's economic policy and the accumulation of newly minted supply, potentially leading to manipulation or disproportionate ownership.

**Recommendation:** Consider implementing a more decentralized approach for inflation management. Options include: (1) directing minted tokens to a community treasury or a staking pool, (2) requiring a governance vote for `updateMintRate` changes, or (3) transferring ownership to a robust multi-signature wallet or a DAO.


### `H-02` — Arbitrary Pool Lock/Unlock by Owner  *(Severity: High · Status: Unresolved)*

The `lockPool()` and `unlockPool()` functions, which control whether transfers to the designated `pool` address are allowed, are restricted to `onlyOwner`. This means the contract owner can arbitrarily prevent or allow transfers to a critical external protocol (the `pool`), potentially disrupting its functionality or creating a single point of failure for users interacting with that pool.

**Recommendation:** Evaluate the necessity of this level of centralized control. If a pool lock mechanism is required, consider implementing a time-lock for `lockPool()`/`unlockPool()` operations or requiring a multi-signature approval to provide a delay and transparency for such critical actions.


### `M-01` — PERMIT_2 Infinite Allowance Implications  *(Severity: Medium · Status: Unresolved)*

The `allowance` function is overridden to return `type(uint256).max` (infinite allowance) if the `spender` is `PERMIT_2` (0x000000000022D473030F116dDEE9F6B43aC78BA3). While this is a feature of the Permit2 standard, it means that any user who interacts with Permit2 and approves this token effectively grants Permit2 the ability to move an unlimited amount of their tokens. This is a significant security implication that users should be fully aware of.

**Recommendation:** Ensure clear communication to users about the implications of interacting with Permit2 and the infinite allowance granted to it. Provide educational resources or warnings within the dApp interface if applicable.


### `M-02` — Unclear Purpose of `tokenURI` for ERC20  *(Severity: Medium · Status: Unresolved)*

The contract includes a `tokenURI` state variable and an `updateTokenURI` function, typically associated with ERC721 or ERC1155 tokens for metadata. For an ERC20 token, this field is non-standard and its intended purpose is unclear from the code alone. This could lead to confusion or indicate an incomplete design if it was meant to integrate with NFT-like features.

**Recommendation:** Clarify the intended use case for the `tokenURI` field in the contract documentation. If it's not serving a specific purpose, consider removing it to reduce contract complexity and potential for misinterpretation. If it's for off-chain metadata, ensure its purpose is well-defined.


### `L-01` — Limited Burn Functionality  *(Severity: Low · Status: Unresolved)*

The `burn()` function is restricted to `onlyOwner` and only allows burning tokens from the `owner()`'s balance. This provides a very limited burn mechanism, as general users cannot burn their own tokens, nor can the owner burn tokens from other addresses. If a broader token burning utility was intended, the current implementation is insufficient.

**Recommendation:** If a general burn mechanism for all token holders is desired, consider implementing a public `burn(uint256 amount)` function that allows `msg.sender` to burn their own tokens. If the current limited functionality is intentional, document this design choice clearly.


### `L-02` — Redundant Vesting Start Check  *(Severity: Low · Status: Unresolved)*

The `hasVestingStarted` modifier includes `require(vestingStart > 0, VestingNotStartedYet())`. However, `vestingStart` is initialized to `block.timestamp` in the constructor, which will always be a positive value. Therefore, this check is redundant and will always pass.

**Recommendation:** Remove the `require(vestingStart > 0, VestingNotStartedYet())` check from the `hasVestingStarted` modifier as it is redundant.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf1e9...bba3`](https://basescan.org/address/0xf1e9baa65d418a9025e1851dd2d37f1ad208bba3) |
| **Network** | Base |
| **Price** | $0.00001456 |
| **24h Volume** | $296.7K |
| **Liquidity** | $354.7K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 38.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 389 buys / 640 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x5e9782079683037fc8bb57625683359d9efaef80f2b829c4bb5b1896c6bb40b6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ratspeak-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
