---
token: iStonks
ticker: ISTONKS
network: base
risk_score: 47
status: medium
date: 2026-09-13
---

# iStonks (ISTONKS) — Smart Contract Security Analysis | Base

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/istonks-base)

---

## Audit Summary

The StonkToken contract is an ERC20 token implementation inheriting from OpenZeppelin's secure ERC20 standard. Key features include an immutable 'launcher' address receiving the total supply and a 'tokenURI' function that queries an external contract for metadata. The primary risk identified is the high centralization of the token supply to the 'launcher' address, which holds all initial tokens. Additionally, the 'tokenURI' function introduces an external dependency, and the 'creator' address is stored but unused.

> **Final Recommendation:** Address the critical centralization risk by implementing a transparent and decentralized distribution strategy for the tokens held by the `launcher` address. Consider using a multi-signature wallet for the `launcher` if it represents a team or community. Evaluate the necessity of the `tokenURI` external dependency and ensure the `launcher` contract is highly secure and reliable. If the `creator` address has no intended function, remove it to optimize gas and clarity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's robust ERC20 implementation, ensuring standard token functionalities are secure (7.2 Code Security). The custom `_hexAddress` function is correctly implemented.… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is straightforward, being a standard ERC20 token without complex DeFi primitives. A significant concern is the initial minting of the entire `totalSupply` to a single… |
| **Upgrades** | 5/10 | Medium | The StonkToken contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). This design choice eliminates risks associated with proxy patterns, such as upgradeability bugs or proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 90.1% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Token Supply  *(Severity: Critical · Status: Unresolved)*

The `StonkToken` contract mints its entire `totalSupply` to a single `launcher` address during construction. This grants the `launcher` address complete control over the token's initial distribution, liquidity, and potential market manipulation. This high degree of centralization poses a significant economic and access control risk (7.4 Economic, 7.3 Access Control).

**Recommendation:** Implement a more decentralized and transparent token distribution mechanism. If the `launcher` is an operational entity, consider securing the address with a multi-signature wallet. Clearly communicate the `launcher`'s role and the planned distribution strategy to the community to manage expectations and build trust.


### `M-01` — External Call Dependency in `tokenURI`  *(Severity: Medium · Status: Unresolved)*

The `tokenURI()` function makes an external call to the `launcher` contract to retrieve `baseTokenURI()`. While a `try/catch` block handles reverts, a compromised or malicious `launcher` contract could return unexpected or misleading metadata, or cause excessive gas consumption, potentially impacting dApps or interfaces that rely on this function for token information (7.2 Code Security, 7.6 External).

**Recommendation:** Ensure the `launcher` contract is highly secure and trustworthy. Consider implementing a mechanism to update the `launcher` address in case of compromise or inactivity, or a fallback to a default URI. Document the implications of this external dependency for users and integrators, highlighting the reliance on the `launcher`'s availability and integrity.


### `L-01` — Unused `creator` Address Variable  *(Severity: Low · Status: Unresolved)*

The `creator` address is stored as an immutable state variable in the constructor but is not utilized anywhere else within the contract's logic. This indicates either an incomplete feature, a design oversight, or unnecessary storage, consuming gas for deployment and state (7.1 Architecture, 7.3 Access Control).

**Recommendation:** If the `creator` variable serves no functional purpose, remove it to optimize contract size and gas costs. If it is intended for a future feature, clearly define its role and implement the corresponding logic.


### `I-01` — Non-Standard `tokenURI` for ERC20  *(Severity: Informational · Status: Unresolved)*

The `StonkToken` contract implements a `tokenURI()` function, which is typically associated with ERC721 or ERC1155 tokens for metadata. While technically permissible for an ERC20, its presence is non-standard and might lead to confusion for integrators or users expecting standard ERC20 behavior without such metadata functions (7.1 Architecture).

**Recommendation:** Clearly document the purpose and expected behavior of the `tokenURI()` function for this ERC20 token. Ensure dApps integrating with `StonkToken` are aware of this non-standard extension and how to interpret its output.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcb2b...e267`](https://basescan.org/address/0xcb2baff7177c8966a8b059b3df3e9323dc2ee267) |
| **Network** | Base |
| **Price** | $0.0003686 |
| **24h Volume** | $254.0K |
| **Liquidity** | $73.1K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 30.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 961 buys / 646 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x9f8353f61574da73218206ad3f70d9455bfed9c4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/istonks-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
