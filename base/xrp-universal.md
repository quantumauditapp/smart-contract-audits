---
token: XRP (Universal)
ticker: UXRP
network: base
risk_score: 55
status: medium
date: 2026-09-15
---

# XRP (Universal) (UXRP) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xrp-universal-base)

---

## Audit Summary

The audit of the WrappedAssetV2 contract, deployed as an upgradeable BeaconProxy, reveals a robust technical foundation built on OpenZeppelin standards. However, the contract design incorporates significant centralization risks, particularly concerning token supply management (mint/burn) and user blacklisting. The custom storage slot implementation, while a valid pattern, introduces a high technical risk for future upgrades if not meticulously managed. These factors contribute to an overall High risk level.

> **Final Recommendation:** Prioritize a comprehensive review of the centralized control mechanisms, specifically the blacklisting and mint/burn functionalities, to ensure they align with the project's risk tolerance and decentralization goals. Implement robust off-chain monitoring for all critical administrative actions, especially blacklisting. For future upgrades, meticulously plan and test any changes to storage layout, particularly concerning the custom storage slot, to prevent potential collisions and state corruption.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20, ERC20Permit, and AccessControlDefaultAdminRules, ensuring a strong foundation for code security (7.2). The `MERCHANT_CONTROLLER` is correctly… |
| **Governance / Economics** | 4/10 | Medium | The contract implements `AccessControlDefaultAdminRules` with an `ADMIN_TRANSFER_DELAY`, enhancing the security of role management, and the initial admin is a multisig (7.3, 7.5). However, the… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern and OpenZeppelin's `Initializable` module, with proper initializer calls for inherited contracts (7.7). The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 1 Informational_

### `M-01` — Centralized Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `RESPONDER_ROLE` has the authority to blacklist any user via the `setUserBlacklist` function. Blacklisted users are prevented from sending or receiving tokens, as enforced by the `_update` override. This grants a single role the power to censor transactions and effectively freeze user funds, posing a critical risk to user autonomy and fund accessibility (7.3 Access Control, 7.4 Economic).

**Recommendation:** Evaluate the necessity and scope of the blacklisting feature. If essential, consider implementing a multi-signature approval process for blacklisting actions or a time-locked mechanism to allow users to react. Ensure clear policies and transparency around blacklisting criteria and procedures. Consider emitting an event when a user is blacklisted or unblacklisted.


### `M-02` — Centralized Control over Token Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` and `burn` functions are restricted to the `MERCHANT_CONTROLLER` address. This grants the `MERCHANT_CONTROLLER` complete control over the token's total supply, allowing arbitrary inflation or deflation. While this may be an intended design, it introduces a significant centralization risk where the integrity of the token's value is entirely dependent on the security and trustworthiness of the `MERCHANT_CONTROLLER` (7.4 Economic, 7.3 Access Control).

**Recommendation:** If centralized supply control is intended, ensure the `MERCHANT_CONTROLLER` is secured by a robust multi-signature wallet with strict operational policies. Consider implementing rate limits or time locks on minting/burning operations, or requiring governance approval for large supply changes, to mitigate risks associated with a compromised key.


### `M-03` — Custom Storage Slot Management for Upgrades  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses a custom storage slot (`WrappedAssetV2StorageLocation`) for its `WrappedAssetV2Storage` struct, accessed via inline assembly in `_getWrappedAssetV2Storage()`. While this pattern can be used for 'eternal storage,' it introduces a high risk of storage collisions if not meticulously managed. Any future upgrade that introduces new state variables or changes the storage layout without accounting for this fixed slot could lead to data corruption or unexpected behavior (7.1 Architecture, 7.7 Upgrades).

**Recommendation:** Ensure that all future upgrades are thoroughly audited for storage layout compatibility, specifically verifying that no new state variables are introduced that would occupy or overlap with the `WrappedAssetV2StorageLocation`. Maintain clear documentation of the custom storage slot and its purpose. Consider using a more standard upgradeable storage pattern (e.g., `_gap` for OpenZeppelin contracts) if the custom slot is not strictly necessary for a specific architectural pattern.


### `I-01` — Lack of Event Emission for Critical Actions  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setUserBlacklist` function, which performs a critical access control action by blacklisting or unblacklisting a user, does not emit an event. This makes it difficult for off-chain systems, such as block explorers, monitoring tools, or user interfaces, to track changes to the blacklist status of addresses (7.8 Operations).

**Recommendation:** Emit an event (e.g., `BlacklistStatusChanged(address indexed user, bool blacklisted, address indexed by)`) whenever `setUserBlacklist` is called. This improves transparency, auditability, and allows for easier off-chain monitoring and integration.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2615...93ae`](https://basescan.org/address/0x2615a94df961278dcbc41fb0a54fec5f10a693ae) |
| **Network** | Base |
| **Price** | $1.3900 |
| **24h Volume** | $107.5K |
| **Liquidity** | $1.03M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 62.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 203 buys / 399 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc8da14d7467814a91384796db3ca2c273b30b361)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xrp-universal-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
