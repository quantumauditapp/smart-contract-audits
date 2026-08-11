---
token: Sport.fun
ticker: FUN
network: base
risk_score: 72
status: critical
date: 2026-08-11
---

# Sport.fun (FUN) — Smart Contract Security Analysis | Base

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sportfun-base)

---

## Audit Summary

The Fun token contract implements a standard ERC20 token with UUPS upgradeability and OpenZeppelin's AccessControl. While leveraging well-audited libraries, the contract exhibits significant centralization risks. The entire token supply is minted to a single owner address, which also holds all administrative and upgrade roles. This creates a critical single point of failure for both economic control and contract integrity.

> **Final Recommendation:** It is strongly recommended to decentralize control over the contract's administrative roles and token supply. Transfer `DEFAULT_ADMIN_ROLE` and `GOVERNOR_ROLE` to a robust multi-signature wallet or a decentralized autonomous organization (DAO) to mitigate the single point of failure risk. Consider implementing a token distribution strategy that avoids concentrating the entire supply in a single address, and evaluate the need for a token burn mechanism or a pause functionality for emergency situations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract is built upon well-audited OpenZeppelin Upgradeable libraries for ERC20, AccessControl, and UUPS, contributing to high code security and architectural soundness (7.1 Architecture, 7.2… |
| **Governance / Economics** | 1/10 | High | The contract utilizes OpenZeppelin's AccessControlUpgradeable for robust role-based access management, defining `DEFAULT_ADMIN_ROLE` and `GOVERNOR_ROLE`. However, a significant economic risk exists… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS upgradeability pattern using OpenZeppelin's `UUPSUpgradeable` module, ensuring a secure and standard upgrade path. The `_authorizeUpgrade` function is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Centralized Control of Token Supply  *(Severity: High · Status: Unresolved)*

The `initialize` function mints the entire `MAX_SUPPLY` (1,000,000,000 * 1e18 tokens) to the `owner` address. This grants the initial `owner` complete control over the token's distribution and market dynamics, posing a significant centralization risk. A single entity holds all tokens, which could lead to market manipulation or a lack of trust from the community (7.4 Economic).

**Recommendation:** Implement a more decentralized token distribution strategy. Consider vesting schedules, community airdrops, or a gradual release mechanism instead of minting the entire supply to a single address. If the current design is intentional, clearly communicate this centralization to users.


### `H-02` — Single Point of Failure for Administrative and Upgrade Roles  *(Severity: High · Status: Unresolved)*

During initialization, the `owner` address is granted both `DEFAULT_ADMIN_ROLE` and `GOVERNOR_ROLE`. The `DEFAULT_ADMIN_ROLE` can manage all other roles, including `GOVERNOR_ROLE`, which is responsible for authorizing contract upgrades. This setup creates a single point of failure: if the `owner`'s private key is compromised, an attacker would gain full administrative control over the contract, including the ability to upgrade it to malicious code and manage all roles (7.3 Access Control, 7.5 Governance, 7.7 Upgrades).

**Recommendation:** Transfer `DEFAULT_ADMIN_ROLE` and `GOVERNOR_ROLE` to a multi-signature wallet or a DAO governance system. This decentralizes control and requires multiple approvals for critical operations, significantly reducing the risk associated with a single compromised key.


### `M-01` — Lack of Explicit Token Burn Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract does not provide an explicit function for burning tokens. While `_mint` is used once during initialization, there is no corresponding `_burn` function or a mechanism to reduce the total supply after initial minting. This might be an intentional design choice, but it limits flexibility for supply management, such as implementing deflationary mechanisms or burning tokens from a treasury (7.4 Economic).

**Recommendation:** If a burn mechanism is desired for future tokenomics or supply management, consider adding a `burn` function, potentially restricted by a role (e.g., `GOVERNOR_ROLE`), that calls `_burn` from the ERC20Upgradeable base contract. If not desired, document this design choice.


### `L-01` — Absence of Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract does not include a pause mechanism (e.g., `PausableUpgradeable`) to halt token transfers or other critical operations in case of an emergency, such as a discovered vulnerability or a major market disruption. While not always strictly necessary, a pause function can be a valuable tool for mitigating risks in a centralized token system (7.8 Operations).

**Recommendation:** Consider integrating OpenZeppelin's `PausableUpgradeable` module. This would allow a designated role (e.g., `GOVERNOR_ROLE` or a new `PAUSER_ROLE`) to temporarily pause and unpause contract functionality, providing an emergency stop-gap measure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x16ee...dd92`](https://basescan.org/address/0x16ee7ecac70d1028e7712751e2ee6ba808a7dd92) |
| **Network** | Base |
| **Price** | $0.02159 |
| **24h Volume** | $117.0K |
| **Liquidity** | $347.1K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 76.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1084 buys / 1228 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x659be70647b0f63217d60e077f4417b1ecc65064)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sportfun-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
