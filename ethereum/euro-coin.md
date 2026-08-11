---
token: Euro Coin
ticker: EURC
network: ethereum
risk_score: 44
status: medium
date: 2026-08-11
---

# Euro Coin (EURC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/euro-coin-eth)

---

## Audit Summary

This audit covers the FiatTokenV2_2 implementation contract, which serves as the logic for a proxy-based ERC-20 stablecoin. The contract introduces a new storage mechanism for balances and blacklist status, combining them into a single mapping. While the new bit-packing logic is technically sound, the upgrade path from previous versions (e.g., FiatTokenV1) that used separate storage mappings for balances and blacklisted accounts appears to be critically flawed. The `initializeV2_2` function only migrates blacklisted accounts, not existing token balances, leading to a high risk of data loss for all user balances upon upgrade. Other aspects, such as EIP-712 signature handling and access controls, are implemented robustly, but the upgrade safety issue overshadows these strengths.

> **Final Recommendation:** Prioritize a thorough review of the upgrade path, specifically focusing on storage layout compatibility and data migration strategies. If this contract was deployed as an upgrade from a version using separate `_balances` and `_blacklisted` mappings without a comprehensive balance migration, immediate action is required to address the potential data loss. Ensure all future upgrades include explicit, audited migration logic for any changes in storage layout affecting user data. Additionally, consider documenting the EIP-712 domain versioning strategy to clarify its relationship with contract versions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract demonstrates strong technical implementation for its core functionalities, including robust EIP-712 signature handling for delegated operations and an efficient bit-packing mechanism for… |
| **Governance / Economics** | 4/10 | Medium | The contract incorporates standard stablecoin governance features such as pausing and blacklisting, which are essential for emergency response and regulatory compliance (7.5 Governance). EIP-712… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable proxy implementation, featuring a versioned initializer (`initializeV2_2`) to manage upgrade logic (7.7 Upgrades). This initializer includes specific… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 21.6% |
| **Top-3 Unlocked** | 55.9% |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Critical Upgrade Storage Collision and Data Loss  *(Severity: Critical · Status: Unresolved)*

The `FiatTokenV2_2` contract introduces a new storage mechanism by overriding `_balanceOf`, `_isBlacklisted`, `_setBalance`, and `_setBlacklistState` to use a single `balanceAndBlacklistStates` mapping. Previous versions, such as `FiatTokenV1`, utilized separate `_balances` and `_blacklisted` mappings. The `initializeV2_2` function, intended for upgrade logic, only migrates accounts from `_deprecatedBlacklisted` to the new `balanceAndBlacklistStates` format. Crucially, it lacks any migration logic for existing token balances stored in the `_balances` mapping from prior versions. This design flaw means that upon upgrading to `FiatTokenV2_2` from a version using separate balance storage, all…

**Recommendation:** If this contract was deployed as an upgrade from a version with separate `_balances` and `_blacklisted` mappings, an immediate and comprehensive audit of the upgrade process is required. A robust migration strategy must be implemented to transfer all existing token balances from the old `_balances` mapping to the new `balanceAndBlacklistStates` mapping during the upgrade. This typically involves a dedicated migration function or a more sophisticated proxy upgrade mechanism that handles storage…


### `I-01` — Centralized Control by Privileged Roles  *(Severity: Informational · Status: Unresolved)*

The contract inherits functionalities such as pausing and blacklisting, which grant significant control to privileged roles (e.g., owner, pauser, blacklister). These roles can pause all transfers, blacklist specific accounts (preventing them from sending/receiving tokens), and potentially mint/burn tokens (inherited from parent contracts). While common for stablecoins to ensure regulatory compliance and emergency response, this centralization introduces a single point of failure and trust, as a compromise of these roles could have severe consequences.

**Recommendation:** Ensure that the private keys controlling these privileged roles are secured with the highest industry standards (e.g., multi-signature wallets, hardware security modules, robust access control policies). Consider implementing a time-lock mechanism for critical administrative actions to provide a window for community review or emergency intervention.


### `I-02` — Hardcoded EIP-712 Domain Version String  *(Severity: Informational · Status: Unresolved)*

The `_domainSeparator()` function uses `EIP712.makeDomainSeparator` with a hardcoded version string of `"2"`. While this is a common practice for EIP-712 domains, if future contract upgrades introduce significant changes to the EIP-712 message structures or authorization logic, maintaining a static domain version might lead to confusion or require careful external communication to users about which domain version corresponds to which contract version. It might also imply that all `FiatTokenV2.x` versions share the same EIP-712 domain, which should be explicitly documented.

**Recommendation:** Document the rationale behind the hardcoded EIP-712 domain version `"2"` and clarify its relationship to the contract's semantic versioning (e.g., `V2_2`). If future changes to EIP-712 message structures are anticipated, consider making the EIP-712 version string configurable or derive it from the contract's semantic version to avoid potential ambiguities.


### `I-03` — Blacklisting of Implementation Contract Address  *(Severity: Informational · Status: Unresolved)*

The `initializeV2_2` function explicitly calls `_blacklist(address(this))`, which blacklists the implementation contract itself. While implementation contracts are generally not intended to hold tokens, if tokens were accidentally sent to this address, they would become permanently locked and unrecoverable due to the blacklisting status. This is an edge case but represents a potential loss of funds if such an accidental transfer occurs.

**Recommendation:** Confirm that there are no scenarios where the implementation contract is expected to hold tokens. If there are, re-evaluate the necessity of blacklisting `address(this)`. Otherwise, ensure clear documentation and operational procedures are in place to prevent accidental token transfers to the implementation contract address.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1aba...c33c`](https://etherscan.io/address/0x1abaea1f7c830bd89acc67ec4af516284b1bc33c) |
| **Network** | Ethereum |
| **Price** | $1.1500 |
| **24h Volume** | $1.20M |
| **Liquidity** | $5.06M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4y |
| **Top-10 Holders** | 37.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 40 buys / 99 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x95dbb3c7546f22bce375900abfdd64a4e5bd73d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/euro-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
