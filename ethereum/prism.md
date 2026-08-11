---
token: Prism
ticker: PRISM
network: ethereum
risk_score: 46
status: high
date: 2026-08-11
---

# Prism (PRISM) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 46/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prism-eth)

---

## Audit Summary

The PrismHookV2 contract serves as a Uniswap V4 hook, an ERC20 token, and manages NFT-like shares for fee distribution. It integrates Solady libraries for efficiency and ReentrancyGuard for security. The contract features a custom NFT-like ownership system and significant owner control over critical operations and fee collection. While robust in its core Uniswap V4 integration and use of established libraries, the custom share management and centralized administrative powers introduce areas of elevated risk.

> **Final Recommendation:** It is recommended to enhance the security posture by decentralizing critical administrative functions, such as fee forfeiture, through a multi-signature wallet or a governance mechanism. A thorough, independent audit of the custom NFT-like share management system is crucial to ensure its correctness and resilience against edge cases. Additionally, comprehensive documentation detailing the intended use and implications of all owner-controlled functions, especially those impacting user funds, should be provided.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates a strong technical foundation, leveraging Solady libraries for gas efficiency and `ReentrancyGuard` for common attack vectors (7.2 Code Security). Its integration with… |
| **Governance / Economics** | 4/10 | Medium | The contract employs an `Ownable` pattern, granting the deployer significant administrative control over critical functions (7.3 Access Control, 7.5 Governance). The owner can `seed` the pool… |
| **Upgrades** | 8/10 | Low | The `PrismHookV2` contract is not implemented as an upgradeable proxy, which simplifies its deployment and reduces the attack surface associated with proxy patterns (7.7 Upgrades). The presence of a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 48.5% |
| **Top-3 Unlocked** | ⚠️ 99.6% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants significant power to a single address. Functions such as `seed`, `migrate`, `setForfeitNextCollection`, and `setMirror` are restricted to the owner. Specifically, the `forfeitNextCollection` flag allows the owner to unilaterally prevent the collection of accrued fees, directly impacting user rewards. This centralization introduces a single point of failure and potential for malicious action or compromise of the owner's key.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the contract owner to reduce the risk associated with a single point of compromise. For highly sensitive functions like `setForfeitNextCollection`, explore integrating a time-lock mechanism or a community governance vote to introduce a delay and transparency before execution.


### `M-01` — Custom NFT-like Implementation Complexity  *(Severity: Medium · Status: Unresolved)*

The contract implements a custom system for managing 'NFTs' (shares) using intricate bitwise operations and mapping structures (`_oo`, `_ownedSlots`, `_addressData`). This custom logic, particularly in `_ownedGet`, `_ownedSet`, `_ownedLength`, and `_setOwnedLength`, deviates from standard ERC721 implementations. Such bespoke solutions are prone to subtle bugs, off-by-one errors, or unexpected behavior in edge cases, potentially leading to incorrect ownership tracking or state corruption.

**Recommendation:** Conduct a dedicated, in-depth audit of the custom NFT-like ownership and storage logic, focusing on all bitwise operations, index calculations, and mapping interactions. Consider writing extensive unit tests specifically for these functions to cover all possible edge cases. If the custom logic is not strictly necessary for unique protocol requirements, consider refactoring to use a well-vetted ERC721 library.


### `M-02` — Potential for Fee Forfeiture Abuse  *(Severity: Medium · Status: Unresolved)*

The `forfeitNextCollection` flag, which can be set by the owner via `setForfeitNextCollection`, allows the owner to unilaterally prevent the collection of fees in the subsequent `pokeFees` call. While this might be intended for emergency situations or specific operational adjustments, it gives the owner the power to directly impact the economic incentives of users by denying them their accrued fees without explicit user consent or a transparent process.

**Recommendation:** Clearly document the intended use cases and operational procedures for the `forfeitNextCollection` flag. Implement safeguards such as a time-lock for setting this flag, or require a multi-signature confirmation. Consider a mechanism to compensate users for forfeited fees if the forfeiture is not due to a critical security event, or ensure that such an action is subject to governance approval.


### `L-01` — Potential Gas Limits in Iterative Functions  *(Severity: Low · Status: Unresolved)*

The constant `MAX_REALIGN` suggests the presence of a function (likely `realign`, though not fully provided) that iterates over a collection of NFTs or similar data. If such a function processes a large number of items in a single transaction, it could become gas-expensive or even revert due to exceeding block gas limits, especially as the number of NFTs or users grows. This could lead to denial of service for certain operations.

**Recommendation:** Ensure that any iterative functions, particularly those that process user-specific data or a growing list of items, are designed to be gas-efficient. Implement pagination, checkpointing, or a pull-based system where users can process their own data in smaller, manageable chunks to avoid hitting block gas limits.


### `I-01` — Dual ERC20 and NFT-like Functionality  *(Severity: Informational · Status: Unresolved)*

The contract functions as both an ERC20 token ('Prism') and manages a system of 'NFTs' (shares) that represent ownership of fee entitlements. While this dual functionality is a core design choice, it can lead to confusion for users and external integrators who might expect a contract to adhere strictly to one token standard. The internal 'NFTs' are not standard ERC721 tokens, which could complicate integration with existing NFT marketplaces or wallets.

**Recommendation:** Provide comprehensive documentation that clearly distinguishes between the ERC20 token and the internal 'NFT' share system. Explain their respective purposes, how they interact, and any deviations from standard ERC721 behavior. Ensure that events and function names clearly indicate which asset type is being manipulated.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcf4d...e040`](https://etherscan.io/address/0xcf4d29f14cc585ddd1167f956092852af844e040) |
| **Network** | Ethereum |
| **Price** | $533.0390 |
| **24h Volume** | $228.3K |
| **Liquidity** | $254.6K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 11d |
| **Top-10 Holders** | 42.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 154 buys / 111 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x30850e19afc43b95e41b1fe35185762b4b631e63d07e91b0300c6e0c8cbf7146)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prism-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
