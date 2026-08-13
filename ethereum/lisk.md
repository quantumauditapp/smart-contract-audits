---
token: Lisk
ticker: LSK
network: ethereum
risk_score: 45
status: medium
date: 2026-08-13
---

# Lisk (LSK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lisk-eth)

---

## Audit Summary

The L1LiskToken contract is an ERC20 token implementation utilizing battle-tested OpenZeppelin libraries for its core functionalities, including burnable tokens, permit functionality, two-step ownership transfer, and role-based access control. The contract's technical implementation is robust, leveraging standard patterns. However, significant centralization risks exist regarding the initial token distribution and the extensive control held by the contract owner over critical functions like burner role management. The contract is not upgradeable, which simplifies its architecture but removes flexibility for future enhancements or bug fixes.

> **Final Recommendation:** It is recommended to carefully plan and communicate the initial token distribution strategy, as the entire supply is minted to a single address. Consider implementing a multi-signature wallet for the contract owner to manage critical functions like adding/removing burners, thereby distributing control and reducing single points of failure. While the contract is not upgradeable, ensure thorough testing and auditing before deployment to mitigate the risks associated with immutable code.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of the L1LiskToken contract is sound, primarily due to its reliance on well-audited OpenZeppelin contracts (ERC20, ERC20Burnable, ERC20Permit, Ownable2Step… |
| **Governance / Economics** | 3/10 | High | The primary economic and governance risk stems from the highly centralized initial token distribution, where the entire 400 million LSK supply is minted to the deployer (7.4 Economic). This places… |
| **Upgrades** | 7/10 | Low | The L1LiskToken contract is not designed to be upgradeable, as it does not implement any proxy patterns (7.7 Upgrades). This means its logic is immutable once deployed, eliminating upgrade-related… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Initial Token Distribution  *(Severity: High · Status: Unresolved)*

The `L1LiskToken` contract's constructor mints the entire `TOTAL_SUPPLY` (400,000,000 LSK) directly to `msg.sender` (the deployer). This design centralizes the entire token supply under a single address, creating a significant single point of control and trust for all subsequent token distribution and market dynamics. A compromise of this address could have catastrophic consequences for the token's ecosystem.

**Recommendation:** Implement a more decentralized or transparent initial distribution mechanism. If the deployer's address is intended to be a treasury or distribution wallet, it should ideally be a robust multi-signature wallet with a high threshold. Clearly communicate the distribution plan to the community to manage expectations and trust.


### `M-01` — Owner's Extensive Control over Burner Role  *(Severity: Medium · Status: Unresolved)*

The contract owner has sole authority to grant and revoke the `BURNER_ROLE` via the `addBurner` and `renounceBurner` functions. While `Ownable2Step` provides a secure mechanism for ownership transfer, a compromised owner key could allow an attacker to grant themselves the `BURNER_ROLE` and burn tokens, or to revoke legitimate burners, leading to denial of service for burning operations.

**Recommendation:** Consider implementing a more decentralized approach for managing critical roles, such as requiring a multi-signature wallet for the owner or introducing a governance mechanism for role management. Alternatively, if the current design is intentional, ensure the owner's private key is secured with the highest possible standards.


### `L-01` — Unused AccessControl `grantRole`/`revokeRole` for `DEFAULT_ADMIN_ROLE`  *(Severity: Low · Status: Unresolved)*

The `L1LiskToken` contract inherits from OpenZeppelin's `AccessControl` but does not explicitly grant the `DEFAULT_ADMIN_ROLE` to any address in its constructor. Consequently, the generic `grantRole` and `revokeRole` functions provided by `AccessControl` are effectively unusable for roles whose admin is `DEFAULT_ADMIN_ROLE` (which includes `BURNER_ROLE` by default), as no address possesses the necessary `DEFAULT_ADMIN_ROLE` to call them. The contract instead uses `onlyOwner` functions (`addBurner`, `renounceBurner`) to manage the `BURNER_ROLE` directly.

**Recommendation:** This is not a vulnerability but a design inconsistency. If the intent is for the `owner` to be the sole manager of the `BURNER_ROLE`, the current implementation is functional. However, to align with `AccessControl`'s intended usage, consider explicitly granting `DEFAULT_ADMIN_ROLE` to the contract owner in the constructor if generic role management is desired for future roles. Otherwise, consider removing the `AccessControl` inheritance if its generic functions are not utilized.


### `I-01` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract lacks a mechanism to pause token transfers or burning in emergency situations. In the event of a critical vulnerability discovery, a major exploit in an integrated system, or unforeseen market manipulation, the inability to temporarily halt operations could lead to significant loss of funds or disruption.

**Recommendation:** Consider integrating an emergency pause mechanism (e.g., using OpenZeppelin's `Pausable` contract) that can be triggered by a trusted entity (e.g., a multi-signature wallet or governance) to temporarily halt critical operations. This provides a crucial safety switch for unforeseen circumstances.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6033...ae3f`](https://etherscan.io/address/0x6033f7f88332b8db6ad452b7c6d5bb643990ae3f) |
| **Network** | Ethereum |
| **Price** | $0.07822 |
| **24h Volume** | $216.3K |
| **Liquidity** | $202.0K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 93.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 271 buys / 271 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x6af632b8235f1a9d95a816f7a4090736346b763a8ab4e8327017aaae72d0d1d2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lisk-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
