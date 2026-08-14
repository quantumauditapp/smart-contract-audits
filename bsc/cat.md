---
token: CAT
ticker: CAT
network: bsc
risk_score: 82
status: critical
date: 2026-08-14
---

# CAT (CAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cat-bsc)

---

## Audit Summary

The project comprises an ERC-20 token (CATToken), a claim distribution contract (CatClaim), and an ERC-721 NFT collection (PolyJetClub). All contracts are built upon OpenZeppelin standards and utilize Solidity 0.8.28. The primary security concern is the high degree of centralized control across all contracts, where a 3/5 multisig owner holds extensive power over critical operations, including token blacklisting, fund management, claim distributions, and NFT minting. While technically sound, this centralization introduces significant trust assumptions and potential for economic manipulation.

> **Final Recommendation:** The project demonstrates robust technical implementation using established OpenZeppelin standards. The primary area for improvement lies in decentralizing control where feasible. Consider implementing time-locks for critical owner-controlled functions or introducing community governance mechanisms for sensitive operations like blacklisting, fund withdrawals, or NFT metadata changes.

For immutable contracts, ensure thorough testing and auditing before deployment, as any post-deployment changes require costly redeployment. Evaluate the long-term implications of centralized control over core assets and functionalities, and explore strategies to progressively decentralize power as the project matures to enhance trust and resilience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation demonstrates strong adherence to best practices, leveraging battle-tested OpenZeppelin libraries for ERC-20, ERC-721, Ownable, Pausable, and ReentrancyGuard… |
| **Governance / Economics** | 1/10 | High | The governance and economic model exhibits a high degree of centralization, with a 3/5 multisig owner retaining extensive control over all core contract functionalities. This includes the ability to… |
| **Upgrades** | 6/10 | Medium | The contracts are deployed as immutable, non-upgradeable implementations. This design choice eliminates risks associated with proxy patterns, such as storage collisions, logic errors during upgrades… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 72.2% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Across All Contracts  *(Severity: High · Status: Unresolved)*

All three contracts (`CATToken`, `CatClaim`, `PolyJetClub`) are `Ownable` and explicitly prevent ownership renouncement. This design concentrates extensive power in a single 3/5 multisig address, which controls all critical operations including token blacklisting, fund transfers from blacklisted accounts, claim amount management, NFT minting, and pausing. This introduces a significant single point of control and high trust requirement in the owner (7.3, 7.5, 7.8).

**Recommendation:** Consider implementing time-locks for highly sensitive owner-controlled functions to introduce a delay before execution, allowing for community review or emergency intervention. Explore progressive decentralization strategies, such as transitioning to a DAO-based governance model for critical decisions like blacklisting or major fund movements, reducing reliance on a single multisig.


### `M-01` — Owner's Power Over Blacklisted Funds  *(Severity: Medium · Status: Unresolved)*

In `CATToken`, the `transferBlackFunds` function allows the owner to unilaterally transfer all tokens from a blacklisted address to any non-blacklisted recipient. While intended for recovery or enforcement, this grants significant power to the owner over user funds, which could be misused or lead to disputes if not handled transparently (7.3, 7.4).

**Recommendation:** Implement a clear policy and transparent process for the use of `transferBlackFunds`, communicating the conditions under which it will be invoked. Consider requiring a multi-signature approval or a time-lock for such transfers to add an additional layer of security and accountability.


### `M-02` — Owner's Control Over Claimable Amounts and Funds  *(Severity: Medium · Status: Unresolved)*

In `CatClaim`, the owner has exclusive control over setting and resetting claimable amounts for any user via `setClaimableAmount` and `setClaimableAmounts`. Additionally, the owner can deposit and withdraw all CAT tokens from the contract using `depositCat` and `withdrawCat`. This centralization means the owner has full discretion over who can claim, how much, and can manage or drain the contract's funds at any time (7.3, 7.4).

**Recommendation:** If possible, explore mechanisms to decentralize the setting of claimable amounts, perhaps through a pre-defined schedule or a community-governed process. For fund withdrawals, consider implementing a time-lock or requiring a higher threshold of multisig signers for large amounts to enhance security and trust.


### `M-03` — Owner's Control Over NFT Minting and Metadata  *(Severity: Medium · Status: Unresolved)*

In `PolyJetClub`, the owner possesses exclusive rights to mint all NFTs up to `MAX_SUPPLY` via `mint` and `batchMint`, and can change the `baseURI` at any time using `setBaseURI`. This centralization allows the owner to control the entire distribution and metadata of the NFT collection, potentially impacting its perceived value or authenticity if the owner's key is compromised or acts maliciously (7.3, 7.4).

**Recommendation:** Consider implementing a time-lock for `setBaseURI` to provide transparency before metadata changes. For minting, if a public sale or decentralized distribution is planned, ensure the owner's minting capabilities are limited or phased out after initial distribution, or integrate a transparent minting schedule.


### `L-01` — Pausability Centralization  *(Severity: Low · Status: Unresolved)*

All contracts implement pausable functionality, allowing the owner to halt core contract operations (e.g., token transfers, claims, NFT minting) at will. While a common emergency mechanism, this feature is entirely controlled by the owner, which could disrupt user activity or be used to freeze assets without immediate recourse (7.3, 7.8).

**Recommendation:** Clearly document the conditions under which the pause functionality would be invoked. For enhanced decentralization, consider requiring a multi-signature approval or a time-lock for pausing and unpausing, especially for prolonged periods, to prevent arbitrary halts.


### `I-01` — Immutable Contract Design  *(Severity: Informational · Status: Unresolved)*

The contracts are deployed as immutable implementations and do not incorporate any upgradeability mechanisms (e.g., proxy patterns). While this eliminates risks associated with complex upgrade processes, it means that any future bug fixes, feature enhancements, or changes to the protocol logic would necessitate a complete redeployment of the contracts and a migration of assets, which can be a complex and costly process (7.7).

**Recommendation:** Ensure comprehensive testing and auditing are conducted prior to deployment, given the immutability of the contracts. For future projects, evaluate the trade-offs between immutability and upgradeability based on the project's long-term vision and potential for evolving requirements.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0667...9424`](https://bscscan.com/address/0x0667873e07ffec6509525b4e4cd97409e1fe9424) |
| **Network** | BNB Chain |
| **Price** | $1.8200 |
| **24h Volume** | $1.18M |
| **Liquidity** | $21.81M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 95.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1325 buys / 367 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x16ace0bcb190fb62fad68ecc26f428505e413b0b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
