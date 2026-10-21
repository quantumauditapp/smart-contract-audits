---
token: Circle Wrapped Bitcoin
ticker: CIRBTC
network: ethereum
risk_score: 86
status: critical
date: 2026-09-20
---

# Circle Wrapped Bitcoin (CIRBTC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 86/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/circle-wrapped-bitcoin-eth)

---

## Audit Summary

This audit covers the FiatTokenV2_2 contract, which serves as the implementation logic for a proxy-based ERC-20 stablecoin. The contract introduces EIP-712 permit and authorization features, and a refined blacklisting mechanism that packs balance and blacklist status into a single storage slot. While the EIP-712 implementation appears robust and the bitwise operations for state packing are carefully handled, a significant risk lies in potential storage collisions during upgrades due to the altered storage layout. Centralized control is inherent to the stablecoin's design, and the contract's self-blacklisting behavior, while potentially intentional, warrants careful consideration.

> **Final Recommendation:** Prioritize a thorough storage layout analysis to confirm compatibility between FiatTokenV2_2 and previous implementations, especially concerning the `balanceAndBlacklistStates` mapping, to mitigate critical upgrade risks. Clearly document the implications of the contract's self-blacklisting behavior for all integrators and ensure it aligns with operational requirements. While centralized control is expected for stablecoins, consider implementing multi-signature wallets or time-locks for critical administrative functions to enhance security and reduce single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract demonstrates robust implementation of EIP-712 permit and authorization functions, leveraging secure libraries like ECRecover and SignatureChecker (7.2 Code Security). The bitwise packing… |
| **Governance / Economics** | 1/10 | High | As a stablecoin, the protocol exhibits a high degree of centralized control, with roles such as owner, pauser, and blacklister possessing significant authority over token operations, including… |
| **Upgrades** | 1/10 | High | The contract is designed as an upgradeable implementation for a proxy (7.1 Architecture). The `initializeV2_2` function includes a version check (`_initializedVersion == 2`) to prevent… |

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
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Storage Collision Risk in Upgrade  *(Severity: High · Status: Unresolved)*

The `FiatTokenV2_2` contract introduces a new storage pattern where `balanceAndBlacklistStates` combines both the token balance and the blacklisted status into a single `uint256` using bitwise operations. If prior versions of the contract (e.g., `FiatTokenV2_1`, `FiatTokenV2`, `FiatTokenV1`) stored these two pieces of information in separate storage slots (e.g., `balances` mapping and `blacklisted` mapping), this change in storage layout could lead to a storage collision during an upgrade. A collision would result in data corruption, where existing balances or blacklist statuses are overwritten or misinterpreted, potentially leading to loss of funds or incorrect blacklisting.

**Recommendation:** Conduct a comprehensive storage layout analysis across all contract versions in the upgrade path to ensure that the introduction of `balanceAndBlacklistStates` does not conflict with previously used storage slots. If a conflict is identified, a migration strategy or a different storage layout for the new version must be implemented to preserve existing data integrity. This is critical for upgrade safety (7.7 Upgrades).


### `M-01` — Self-Blacklisting of Contract Address  *(Severity: Medium · Status: Unresolved)*

The `initializeV2_2` function explicitly blacklists the contract's own address (`_blacklist(address(this))`). While this might be an intentional design choice to prevent the token contract itself from holding tokens, it is an unusual pattern for an ERC-20 token. This could lead to unexpected behavior or operational limitations if future functionalities or integrations require the contract to temporarily hold or receive its own tokens. It also means the contract cannot be a recipient in any transfer, which might not be immediately obvious to external systems (7.8 Operations).

**Recommendation:** Clearly document the rationale and implications of blacklisting the contract's own address. Ensure that all current and future operational requirements and integrations are compatible with this restriction. If the intent is solely to prevent the contract from holding tokens, consider alternative mechanisms that are less restrictive or more explicit in their purpose.


### `L-01` — Centralized Control Over Critical Functions  *(Severity: Low · Status: Unresolved)*

The contract, as part of a stablecoin system, relies on centralized control for critical functions such as pausing transfers, blacklisting accounts, and managing upgrades. Roles like `owner`, `pauser`, and `blacklister` (inherited from base contracts) possess significant power, including the ability to freeze user funds or prevent all token operations (7.3 Access Control, 7.5 Governance). While this is a common and often necessary design for stablecoins to ensure stability and compliance, it introduces a single point of failure and a high degree of trust in the controlling entities.

**Recommendation:** While centralization is inherent to this type of asset, consider implementing additional security measures for critical administrative roles, such as multi-signature wallets for ownership and key operational roles, and potentially time-locks for sensitive parameter changes or upgrade approvals. This enhances security by distributing control and providing a delay for review (7.5 Governance).


### `I-01` — Complex Bitwise Operations for State Packing  *(Severity: Informational · Status: Unresolved)*

The contract utilizes bitwise operations to pack two distinct pieces of state (token balance and blacklisted status) into a single `uint256` variable (`balanceAndBlacklistStates`). Specifically, the highest bit (2^255) is used to indicate blacklisting, while the lower 255 bits store the balance. While this is an efficient storage optimization, it significantly increases the complexity of the code and the potential for subtle errors if not handled with extreme care (7.2 Code Security).

**Recommendation:** Ensure comprehensive unit and integration tests specifically cover all edge cases related to the bitwise operations, including maximum balance values, blacklisting/unblacklisting transitions, and concurrent operations. Maintain clear and detailed documentation explaining this storage mechanism to reduce the risk of future misinterpretations or errors during maintenance or upgrades.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x72df...075e`](https://etherscan.io/address/0x72dfb2e44f59c5ad2bafe84314e5b99a7cd5075e) |
| **Network** | Ethereum |
| **Price** | $80,300.3200 |
| **24h Volume** | $4.52M |
| **Liquidity** | $21.90M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4d |
| **Top-10 Holders** | 100.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 238 buys / 179 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xcceef8a17d01e0097bd1ab51687754c86456363b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/circle-wrapped-bitcoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
