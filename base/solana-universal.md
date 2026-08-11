---
token: Solana (Universal)
ticker: USOL
network: base
risk_score: 45
status: medium
date: 2026-08-11
---

# Solana (Universal) (USOL) — Smart Contract Security Analysis | Base

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solana-universal-base)

---

## Audit Summary

The audit of the WrappedAssetV2 contract, serving as the implementation for a BeaconProxy, revealed a robust ERC20 token implementation utilizing OpenZeppelin's upgradeable contracts and access control. Key features include centralized minting/burning and a user blacklist. A critical vulnerability was identified in the custom storage pattern, which poses a significant risk during future upgrades. High centralization of control for token operations and an immutable merchant controller also present notable risks.

> **Final Recommendation:** It is strongly recommended to address the critical storage collision vulnerability by refactoring the custom storage pattern to align with standard upgradeable storage practices, such as using explicit storage gaps or OpenZeppelin's `ERC1967Upgrade` storage layout. Additionally, consider implementing a mechanism to update the `MERCHANT_CONTROLLER` address through a controlled, multi-signature process to enhance operational flexibility and reduce single points of failure. Ensure robust operational procedures and multi-signature controls are in place for all privileged roles, especially the `MERCHANT_CONTROLLER` and `RESPONDER_ROLE`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract leverages battle-tested OpenZeppelin libraries for ERC20 and access control, enhancing code security (7.2). The custom blacklist logic within `_update` is correctly implemented to… |
| **Governance / Economics** | 4/10 | Medium | The contract implements strong access control (7.3) using `AccessControlDefaultAdminRulesUpgradeable` with a 1-day delay for admin role transfers, which is a good security practice. However, the… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a BeaconProxy, correctly using `Initializable` and calling `_disableInitializers()` in its constructor. This setup generally supports… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 27.1% |
| **Top-3 Unlocked** | 45.2% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 3 Informational_

### `C-01` — Critical: Custom Storage Pattern Poses Upgrade Risk  *(Severity: Critical · Status: Unresolved)*

The `WrappedAssetV2` contract uses a custom storage pattern where `WrappedAssetV2Storage` is explicitly mapped to a fixed `bytes32` slot (`WrappedAssetV2StorageLocation`) using inline assembly. This approach deviates from standard upgradeable contract storage management (e.g., using OpenZeppelin's `ERC1967Upgrade` or explicit storage gaps). If a future upgrade introduces new state variables or if OpenZeppelin's internal storage layout changes in a way that conflicts with this hardcoded slot, it could lead to storage collisions, data corruption, or loss of funds for users. This is a severe upgrade safety issue (7.1, 7.7).

**Recommendation:** Refactor the storage to use OpenZeppelin's recommended upgradeable storage patterns. This typically involves inheriting from `UUPSUpgradeable` or `TransparentUpgradeableProxy` and defining storage variables directly in the contract, allowing the compiler to manage storage slots. If custom storage is absolutely necessary, ensure it is placed within an explicit storage gap to prevent future collisions.


### `H-01` — High: Centralized Control Over Token Supply and User Funds  *(Severity: High · Status: Unresolved)*

The `mint` and `burn` functions are restricted to the `MERCHANT_CONTROLLER`, granting this single address complete control over the token's supply. Additionally, the `setUserBlacklist` function, restricted to the `RESPONDER_ROLE`, allows blacklisting any user, effectively freezing their funds or preventing them from receiving tokens. This high degree of centralization (7.3, 7.4) introduces significant economic risk, as a compromise or malicious action by these privileged roles could lead to arbitrary minting, burning, or censorship of user funds.

**Recommendation:** Ensure that the `MERCHANT_CONTROLLER` and `RESPONDER_ROLE` are controlled by robust, multi-signature wallets with high thresholds and strict operational procedures. Clearly document the scope, responsibilities, and limitations of these roles. Consider implementing time locks or additional governance checks for critical actions like large mints or widespread blacklisting.


### `M-01` — Medium: Immutable MERCHANT_CONTROLLER Address  *(Severity: Medium · Status: Unresolved)*

The `MERCHANT_CONTROLLER` address is set as `immutable` in the constructor. This means that if the `MERCHANT_CONTROLLER` address needs to be changed in the future (e.g., due to compromise, operational changes, or an upgrade of the controller itself), it cannot be updated without deploying an entirely new implementation contract and performing an upgrade. This limits operational flexibility and introduces a single point of failure (7.3, 7.8).

**Recommendation:** Consider making the `MERCHANT_CONTROLLER` address configurable via an access-controlled function, allowing it to be updated by the contract's admin role (e.g., the multisig). This would provide greater operational flexibility and resilience without requiring a full contract upgrade for a simple address change.


### `I-01` — Informational: Blacklist Logic Clarity  *(Severity: Informational · Status: Unresolved)*

The `_update` function checks `$.userBlacklist[msg.sender] \|\| $.userBlacklist[from] \|\| $.userBlacklist[to]`. While functionally correct, the check for `msg.sender` is often redundant when `msg.sender` is also `from` (as in a direct `transfer`). This does not introduce a vulnerability but could be slightly optimized for clarity or gas if desired (7.2).

**Recommendation:** No change is strictly required as the logic is correct. For minor optimization, one could consider if `msg.sender` is always `from` in the context of `_update` calls from `transfer` and `transferFrom`, and potentially simplify the condition. However, the current implementation is safe.


### `I-02` — Informational: Use of AccessControlDefaultAdminRulesUpgradeable with Delay  *(Severity: Informational · Status: Unresolved)*

The contract correctly utilizes `AccessControlDefaultAdminRulesUpgradeable` with a `ADMIN_TRANSFER_DELAY` of 1 day. This is a good security practice (7.3, 7.5) as it introduces a time delay for critical administrative role changes, providing a window for detection and potential mitigation of malicious or erroneous actions.

**Recommendation:** Maintain this security feature. Ensure the `ADMIN_TRANSFER_DELAY` is appropriate for the operational security requirements of the protocol.


### `I-03` — Informational: Correct Initialization Prevention  *(Severity: Informational · Status: Unresolved)*

The `WrappedAssetV2` constructor correctly calls `_disableInitializers()`. This prevents the implementation contract from being initialized directly, which is a crucial security measure for upgradeable contracts deployed behind a proxy (7.7).

**Recommendation:** No action required. This is a best practice and correctly implemented.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9b8d...db55`](https://basescan.org/address/0x9b8df6e244526ab5f6e6400d331db28c8fdddb55) |
| **Network** | Base |
| **Price** | $75.7000 |
| **24h Volume** | $423.3K |
| **Liquidity** | $768.4K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 75.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 387 buys / 308 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x0225ba893d5f8ecd6d2022f9dec59b34f61098a1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solana-universal-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
