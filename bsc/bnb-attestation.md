---
token: BNB Attestation
ticker: BAS
network: bsc
risk_score: 84
status: critical
date: 2026-08-17
---

# BNB Attestation (BAS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 84/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnb-attestation-bsc)

---

## Audit Summary

The BASToken contract is an ERC20Capped token with custom access control, pausing, and whitelisting functionalities. It leverages well-audited OpenZeppelin libraries. The audit identified a critical access control design flaw where the PAUSER_ROLE is configured to be its own administrator, creating a single point of failure for role management. Significant centralization of power in the DEFAULT_ADMIN_ROLE and PAUSER_ROLE also presents high economic and governance risks.

> **Final Recommendation:** Address the critical access control flaw by reconfiguring the PAUSER_ROLE's administrator to the DEFAULT_ADMIN_ROLE to ensure proper role management and prevent a single point of failure. Implement robust multi-signature wallet solutions for all critical roles (DEFAULT_ADMIN_ROLE, PAUSER_ROLE, MINTER_ROLE) to mitigate centralization risks and enhance operational security. Clearly document the intended use and implications of the whitelist mechanism, especially during paused states, to manage user expectations and potential economic impacts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract demonstrates good technical quality, utilizing battle-tested OpenZeppelin libraries for ERC20, ERC20Capped, AccessControl, and Pausable functionalities (7.2 Code Security). The custom… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the DEFAULT_ADMIN_ROLE holding significant power, including setting the minter and recovering arbitrary ERC20 tokens (7.4 Economic, 7.5… |
| **Upgrades** | 2/10 | High | The BASToken contract is implemented as a standard, non-upgradeable ERC20 token. It does not utilize any proxy patterns (e.g., UUPS, Transparent) or upgrade mechanisms. Therefore, there are no… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — PAUSER_ROLE Self-Administration Creates Unmanageable Role  *(Severity: Critical · Status: Unresolved)*

The constructor calls `_setRoleAdmin(PAUSER_ROLE, PAUSER_ROLE)`. This configuration means that only an address already possessing the PAUSER_ROLE can grant or revoke the PAUSER_ROLE from other addresses. The DEFAULT_ADMIN_ROLE, which typically manages all other roles, loses its ability to manage PAUSER_ROLE members. If the initial PAUSER_ROLE holder's key is lost or compromised, it becomes impossible to add new PAUSER_ROLE holders or remove existing ones, leading to an unmanageable and potentially unrecoverable critical role (7.3 Access Control, 7.8 Operations).

**Recommendation:** Change the role administration for PAUSER_ROLE to DEFAULT_ADMIN_ROLE. The constructor should call `_setRoleAdmin(PAUSER_ROLE, DEFAULT_ADMIN_ROLE)` instead of `_setRoleAdmin(PAUSER_ROLE, PAUSER_ROLE)`. This ensures that the DEFAULT_ADMIN_ROLE retains control over managing PAUSER_ROLE members.


### `H-01` — High Centralization of Power  *(Severity: High · Status: Unresolved)*

The contract design grants significant power to a few privileged roles. The DEFAULT_ADMIN_ROLE can set the MINTER_ROLE and recover any ERC20 tokens accidentally sent to the contract. The PAUSER_ROLE can pause/unpause the contract and manage the whitelist, effectively controlling token transferability and liquidity. The MINTER_ROLE can mint new tokens up to the cap. This high degree of centralization introduces single points of failure and potential for abuse if these privileged accounts are compromised or act maliciously (7.4 Economic, 7.5 Governance).

**Recommendation:** Implement multi-signature wallets (e.g., Gnosis Safe) for all critical roles (DEFAULT_ADMIN_ROLE, PAUSER_ROLE, MINTER_ROLE) to distribute control and require multiple approvals for sensitive operations. Consider a time-locked mechanism for critical administrative actions or a transition to a decentralized autonomous organization (DAO) for governance over time.


### `M-01` — Whitelist Mechanism During Pause Can Restrict Transfers  *(Severity: Medium · Status: Unresolved)*

When the contract is paused, token transfers are only permitted if both the sender and receiver are on the whitelist, or if it's a minting operation. The PAUSER_ROLE has the sole authority to add or remove addresses from this whitelist. While this mechanism might be intended for specific operational control, it gives the PAUSER_ROLE the ability to selectively restrict or allow transfers, potentially impacting market liquidity or creating a censorship vector (7.4 Economic, 7.8 Operations).

**Recommendation:** Clearly document the intended use cases and implications of the whitelist mechanism, especially during paused states. Consider implementing a time-lock for whitelist changes to provide transparency and allow users to react. If possible, explore more decentralized or community-governed approaches for whitelist management.


### `L-01` — Minter Role Can Be Granted to Multiple Addresses  *(Severity: Low · Status: Unresolved)*

The `setMinter` function allows the DEFAULT_ADMIN_ROLE to grant the MINTER_ROLE to any address. There is no explicit mechanism to revoke a previously granted MINTER_ROLE before assigning a new one, nor is there a restriction on the number of addresses that can hold the MINTER_ROLE simultaneously. This could lead to multiple entities having minting capabilities, which might not align with the project's intended operational model (7.3 Access Control).

**Recommendation:** If only a single minter is desired, modify the `setMinter` function to first revoke the MINTER_ROLE from any existing minter before granting it to a new address. Alternatively, if multiple minters are acceptable, explicitly document this design choice and ensure robust operational procedures for managing multiple minting entities.


### `I-01` — Contract Deploys in Paused State  *(Severity: Informational · Status: Unresolved)*

The contract's constructor includes `_pause()`, meaning the token is deployed in a paused state. This prevents most token transfers (except whitelisted transfers or minting) immediately after deployment until the `unpause()` function is called by an account with the PAUSER_ROLE. This is likely a deliberate design choice for initial setup or pre-launch phases (7.8 Operations).

**Recommendation:** Ensure that the operational plan for unpausing the contract and enabling full token transfers is clearly defined and communicated to all stakeholders. This includes the timing of the unpause event and the responsibilities of the PAUSER_ROLE.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f0d...4e37`](https://bscscan.com/address/0x0f0df6cb17ee5e883eddfef9153fc6036bdb4e37) |
| **Network** | BNB Chain |
| **Price** | $0.02748 |
| **24h Volume** | $1.85M |
| **Liquidity** | $1.97M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 76.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4597 buys / 5257 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa341e8e8ee6bf97fa1d18c2d12f00555dc78207e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnb-attestation-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
