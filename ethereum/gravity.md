---
token: Gravity
ticker: G
network: ethereum
risk_score: 61
status: medium
date: 2026-09-19
---

# Gravity (G) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gravity-eth)

---

## Audit Summary

The Gravity Token (G) contract implements an ERC20 token with standard OpenZeppelin functionalities (burnable, pausable, permit) and a custom LimitedMinterManager for controlled token minting. The contract utilizes Ownable2Step for ownership management, with the owner being a 3/6 multisig. While the architecture leverages well-audited libraries, a critical integer overflow vulnerability exists in the custom minting limit calculation, which could severely disrupt the token's economic model. Additionally, the owner retains the ability to mint an unlimited supply of tokens, posing a significant centralization risk.

> **Final Recommendation:** It is strongly recommended to address the critical integer overflow vulnerability in the `_getCurrentLimit` function immediately to ensure the integrity of the limited minting mechanism. Consider implementing SafeMath or similar overflow protection for all arithmetic operations involving potentially large numbers. Review the `ownerMint` function's necessity; if unlimited owner minting is not strictly required, it should be removed or restricted. For future deployments, evaluate the benefits of an upgradeable contract architecture to allow for bug fixes and feature enhancements without requiring a token migration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The technical architecture (7.1 Architecture) benefits from extensive use of battle-tested OpenZeppelin libraries for ERC20, burning, pausing, and ownership, which enhances code security. However… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) is significantly impacted by the `ownerMint` function, which allows the owner to mint an unlimited supply of tokens, creating a single point of failure and potential… |
| **Upgrades** | 3/10 | High | The contract is deployed as a standard implementation and does not incorporate any upgradeability mechanisms (7.7 Upgrades). This means that any discovered bugs or desired feature enhancements would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Integer Overflow in `_getCurrentLimit` Calculation  *(Severity: Critical · Status: Unresolved)*

The `_getCurrentLimit` function in `LimitedMinterManager.sol` calculates the replenished minting limit using the formula `_calculatedLimit = _limit + ((_timePassed * _maxLimit) / _duration);`. The multiplication `_timePassed * _maxLimit` can lead to an integer overflow if both `_timePassed` (which can be very large, representing time elapsed since `_timestamp`) and `_maxLimit` (which can be up to `type(uint256).max / 2`) are sufficiently large. An overflow would cause `_calculatedLimit` to wrap around to a much smaller value, effectively denying minters their expected minting capacity and breaking the core economic logic of the limited minter system.

**Recommendation:** Implement robust overflow protection for the multiplication `_timePassed * _maxLimit`. Consider using OpenZeppelin's `SafeMath` library (if not already implicitly handled by Solidity 0.8.x checked arithmetic for additions/subtractions, which it is, but not for intermediate products in a division) or explicitly check for overflow before multiplication. For example, check `if (_timePassed != 0 && _maxLimit > type(uint256).max / _timePassed)` before performing the multiplication.


### `H-01` — Unlimited Owner Minting Capability  *(Severity: High · Status: Unresolved)*

The `ownerMint(address to, uint256 amount)` function in `GravityTokenG.sol` allows the contract owner to mint an arbitrary `amount` of tokens to any `to` address without any limits or restrictions. This capability bypasses the `LimitedMinterManager`'s controlled minting mechanism entirely. While protected by `onlyOwner`, this grants the owner absolute control over the token's total supply, posing a significant centralization risk and potential for arbitrary inflation, which could severely devalue the token.

**Recommendation:** Evaluate the necessity of unlimited owner minting. If not strictly required, remove the `ownerMint` function. If it is deemed necessary for specific operational reasons (e.g., emergency recovery), consider implementing a time-locked or multi-signature approval mechanism for such mints, or cap the maximum amount that can be minted by the owner within a certain period. Ensure robust operational security for the owner's keys.


### `L-01` — Inefficient Minter Removal with Index Hint  *(Severity: Low · Status: Unresolved)*

The `_removeMinterByIndexHint` function in `LimitedMinterManager.sol` requires an `_indexHint` parameter to locate the minter in the `_minters` array. If the array's state changes (e.g., another minter is added or removed) between the time an off-chain system fetches the index and the transaction is submitted, the provided `_indexHint` might become invalid. This would cause the transaction to revert with `ILimitedMinterManager_InvalidIndexHint()`, requiring the owner to re-fetch the correct index and resubmit.

**Recommendation:** While not a security vulnerability, this can lead to a poor user experience for the owner. Consider iterating through the `_minters` array to find the minter's index if the array is expected to remain small. For larger arrays, ensure off-chain tooling is robust in handling potential index mismatches and retries, or provide a mechanism to update the index hint if the transaction reverts.


### `I-01` — High Degree of Centralized Control  *(Severity: Informational · Status: Unresolved)*

The `GravityTokenG` contract design grants significant control to a single owner address (currently a 3/6 multisig). This owner has the power to pause/unpause transfers, change the token name, set minting limits for all minters, remove minters, and crucially, mint an unlimited supply of tokens via `ownerMint`. While a multisig mitigates some risks associated with a single point of failure, the protocol's operation remains highly dependent on the integrity and security of this central entity.

**Recommendation:** Acknowledge and accept the inherent risks of centralized control. Ensure the multisig signers are diverse, trusted, and follow strict operational security procedures. For future iterations, consider gradually decentralizing control over critical functions, perhaps through a more robust on-chain governance mechanism or by introducing time-locks for sensitive operations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9c7b...0649`](https://etherscan.io/address/0x9c7beba8f6ef6643abd725e45a4e8387ef260649) |
| **Network** | Ethereum |
| **Price** | $0.008818 |
| **24h Volume** | $1.57M |
| **Liquidity** | $1.58M |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 90.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 921 buys / 781 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc4dbe30fecc148a8755c970f3b8b0c9af0db81f5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gravity-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-19*
