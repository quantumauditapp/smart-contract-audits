---
token: apyUSD
ticker: APYUSD
network: ethereum
risk_score: 83
status: high
date: 2026-09-15
---

# apyUSD (APYUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 83/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apyusd-eth)

---

## Audit Summary

The ApyUSD contract functions as an upgradeable ERC-20 token with ERC-4626 vault capabilities, leveraging OpenZeppelin's upgradeable standards. It incorporates a deny-list, pausing functionality, and a custom storage pattern. While the use of established libraries and reentrancy guards enhances security, the contract exhibits significant centralization risks, critical dependencies on external contracts, and specific design choices in its withdrawal mechanism that warrant attention. The custom storage implementation also requires careful management during upgrades.

> **Final Recommendation:** It is recommended to thoroughly review and document the roles and responsibilities of the `AccessManager` to ensure appropriate governance and multi-signature controls are in place for critical operations. Conduct comprehensive audits of all external contracts (`IVesting`, `IUnlockReceipt`, `IAddressList`) that `ApyUSD` depends on, as their security directly impacts this contract. Implement explicit checks for `MAX_FEE` in the `setUnlockingFee` function to prevent malicious fee settings. Finally, ensure a robust upgrade strategy is in place, particularly concerning custom storage slots, to prevent state corruption during future contract updates.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract utilizes robust OpenZeppelin upgradeable components for ERC-20, ERC-4626, pausing, and access control, providing a strong foundation (7.2 Code Security). Reentrancy is mitigated using… |
| **Governance / Economics** | 1/10 | High | The contract's `AccessManagedUpgradeable` pattern centralizes significant control under an `Authority` (7.3 Access Control). This entity can pause transfers, manage the deny-list, set critical… |
| **Upgrades** | 1/10 | High | The contract employs the UUPS proxy pattern, with `_authorizeUpgrade` restricted to the `AccessManager`, which is a secure approach for upgrade authorization (7.7 Upgrades). However, the use of a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control and Privileged Roles  *(Severity: High · Status: Unresolved)*

The `AccessManagedUpgradeable` pattern grants significant power to the designated `Authority` (or `AccessManager`). This entity has the ability to pause the contract, manage the deny-list, set critical external contract addresses (e.g., `unlockToken`, `vesting`, `unlockReceipt`), set the `ccipAdmin`, and authorize upgrades. This high degree of centralization introduces a single point of failure or compromise, where a malicious or compromised `AccessManager` could severely impact the protocol's integrity and user funds.

**Recommendation:** Implement robust governance mechanisms, such as a multi-signature wallet or a decentralized autonomous organization (DAO), to control the `AccessManager` role. Ensure that critical actions require multiple approvals or community consensus. Clearly document the powers of the `AccessManager` and the procedures for its management.


### `H-02` — Critical External Contract Dependencies  *(Severity: High · Status: Unresolved)*

The `ApyUSD` contract relies heavily on external contracts such as `IUnlockToken`, `IVesting`, `IUnlockReceipt`, and `IAddressList`. Specifically, the `_withdraw` function calls `$.vesting.pullVestedYield()` and `$.unlockReceipt.mint()`, and the `totalAssets()` calculation depends on `$.vesting.vestedAmount()`. Vulnerabilities, malicious behavior, or unexpected state in any of these external contracts could directly lead to security breaches, economic exploits, or operational failures within the `ApyUSD` contract.

**Recommendation:** Conduct thorough security audits of all dependent external contracts. Implement robust input validation and sanity checks on return values from external calls where possible. Consider implementing circuit breakers or emergency mechanisms to temporarily disable interactions with compromised external contracts. Ensure that the addresses of these external contracts are set by a secure, multi-signature controlled process.


### `M-01` — Strict `receiver` check in `_withdraw`  *(Severity: Medium · Status: Unresolved)*

The `_withdraw` function includes a strict check `if (receiver != owner) revert InvalidCaller();`. This design choice mandates that the `receiver` of the withdrawn assets must be the same as the `owner` (the address initiating the withdrawal). This deviates from the typical ERC-4626 `withdraw` behavior, which usually allows `receiver` to be a different address than `owner`. While this might be an intentional design for specific use cases (e.g., direct receipt minting to the owner), it could limit flexibility for users and lead to unexpected integration issues for systems expecting standard ERC-4626 functionality.

**Recommendation:** Clarify and document the rationale behind this strict `receiver` check. If the intention is to allow withdrawals to different addresses, consider removing or modifying this check, ensuring that any such change does not introduce new vulnerabilities. If the current behavior is intentional, ensure it is clearly communicated to integrators and users.


### `M-02` — Custom Storage Slot Management  *(Severity: Medium · Status: Unresolved)*

The contract uses a custom storage slot (`APYUSD_STORAGE_LOC`) for `ApyUSDStorage` via inline assembly. While this pattern is a valid approach for managing custom state in upgradeable contracts, it requires meticulous care. If the chosen slot collides with OpenZeppelin's internal storage slots or any future state variables introduced in subsequent upgrades, it could lead to critical state corruption, loss of funds, or unexpected contract behavior.

**Recommendation:** Ensure that the chosen custom storage slot is sufficiently far from known OpenZeppelin storage slots and any other potential future state variables. Maintain a clear and detailed storage layout map for all contract versions. Implement robust testing, including upgrade simulations, to verify storage compatibility before deploying new implementations.


### `L-01` — Missing Fee Cap Enforcement in `setUnlockingFee` (Assumed)  *(Severity: Low · Status: Unresolved)*

The contract defines a `MAX_FEE` constant of `0.01e18` (1%). However, the `setUnlockingFee` function (which is truncated in the provided code but assumed to exist and be `restricted`) is not explicitly shown to enforce this `MAX_FEE` limit. Without this check, a privileged role could potentially set an arbitrarily high unlocking fee, leading to economic exploitation or making withdrawals prohibitively expensive.

**Recommendation:** Ensure that the `setUnlockingFee` function includes a check to prevent setting the `unlockingFee` above `MAX_FEE`. For example: `require(newFee <= MAX_FEE, "Fee exceeds max");`.


### `I-01` — Use of `TransientSlot` for `tokenId`  *(Severity: Informational · Status: Unresolved)*

The contract utilizes `TransientSlot` (`LAST_TOKEN_ID_TSLOT`) to temporarily store the `tokenId` generated during `_withdraw` and retrieve it in `withdrawForReceipt` and `redeemForReceipt`. This pattern is designed to pass values across internal/external calls within a single transaction without permanent storage. While generally safe for its intended purpose, it's a less common pattern that requires careful understanding to ensure correct usage and prevent unexpected behavior if transaction flow is altered or re-entered in an unforeseen way.

**Recommendation:** Document the specific use case and assumptions for `TransientSlot` usage within the contract. Ensure that all developers and integrators understand its ephemeral nature and the implications for transaction design. Verify through testing that the `tokenId` is correctly stored and retrieved under various transaction scenarios.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x38ee...8a6a`](https://etherscan.io/address/0x38eeb52f0771140d10c4e9a9a72349a329fe8a6a) |
| **Network** | Ethereum |
| **Price** | $1.3600 |
| **24h Volume** | $2.20M |
| **Liquidity** | $16.36M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 83.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 98 buys / 61 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xe41be7b340f7c2eda4da1e99b42ee1b228b526b7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apyusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
