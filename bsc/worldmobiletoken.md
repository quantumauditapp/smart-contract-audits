---
token: WorldMobileToken
ticker: WMTX
network: bsc
risk_score: 75
status: high
date: 2026-09-20
---

# WorldMobileToken (WMTX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/worldmobiletoken-bsc)

---

## Audit Summary

The WorldMobileToken contract is an ERC20 token utilizing OpenZeppelin's battle-tested libraries for capped supply, permit functionality, and role-based access control. While the code quality is high due to OpenZeppelin's foundation, significant centralization exists with the deployer holding all administrative roles. Additionally, the token uses a non-standard 6-decimal precision, which requires careful handling by integrators.

> **Final Recommendation:** It is strongly recommended to transfer the `DEFAULT_ADMIN_ROLE` to a secure multi-signature wallet immediately after deployment to mitigate the single point of failure risk. This will enhance the security posture by requiring multiple approvals for critical administrative actions, including granting or revoking `MINTER_ROLE` and `BURNER_ROLE`. Furthermore, ensure all external integrations (exchanges, wallets, dApps) are explicitly aware of and correctly handle the token's 6-decimal precision to prevent miscalculations or display errors. Consider clear documentation and communication regarding this non-standard decimal value.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages battle-tested OpenZeppelin libraries for ERC20, ERC20Capped, ERC20Permit, and AccessControl, contributing to a solid foundation (7.2 Code Security). The implementation… |
| **Governance / Economics** | 1/10 | High | The token design incorporates a fixed supply cap and explicit roles for minting and burning, providing controlled supply management (7.4 Economic). However, the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`… |
| **Upgrades** | 3/10 | High | The `WorldMobileToken` contract is deployed as a standard implementation and does not utilize any proxy patterns, meaning it is not upgradeable (7.7 Upgrades). This ensures immutability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Access Control and Single Point of Failure  *(Severity: High · Status: Unresolved)*

The contract's constructor grants the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `BURNER_ROLE` to the deployer's address (`_msgSender()`). This design centralizes significant power in a single entity. The `DEFAULT_ADMIN_ROLE` can grant or revoke any other role, including `MINTER_ROLE` and `BURNER_ROLE`. A compromise of the deployer's private key would allow an attacker to mint new tokens up to the cap, burn existing tokens, or manipulate roles, leading to severe economic impact and loss of trust (7.3 Access Control, 7.8 Operations).

**Recommendation:** Transfer the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet (e.g., Gnosis Safe) immediately after deployment. This distributes control and requires multiple approvals for critical administrative actions, significantly reducing the risk associated with a single point of failure.


### `M-01` — Non-Standard ERC20 Decimals  *(Severity: Medium · Status: Unresolved)*

The `decimals()` function is overridden to return 6, whereas the widely adopted standard for ERC20 tokens is 18 decimals. This deviation can lead to significant integration challenges, miscalculations, and user confusion across various platforms such as exchanges, wallets, block explorers, and DeFi protocols that often assume 18 decimals by default (7.1 Architecture, 7.4 Economic).

**Recommendation:** Ensure all external systems and user interfaces interacting with the WorldMobileToken are explicitly aware of and correctly configured to handle 6 decimals. Provide clear documentation and communication regarding this non-standard precision to prevent errors and ensure accurate display of token amounts.


### `L-01` — Lack of Dedicated `DEFAULT_ADMIN_ROLE` Transfer Function  *(Severity: Low · Status: Unresolved)*

While the `AccessControl` contract allows for granting and revoking roles, there isn't a dedicated, explicit function to safely transfer the `DEFAULT_ADMIN_ROLE` to a new address or a multi-signature wallet in a single, atomic transaction. Transferring this critical role requires a multi-step process (granting to new admin, then revoking from old admin), which can be error-prone if not executed carefully (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a custom `transferAdmin` function that allows the current `DEFAULT_ADMIN_ROLE` to transfer its role to a new address in a single, atomic transaction, or ensure a well-documented and tested procedure is followed for manual transfer. This reduces the risk of accidental loss of administrative control during the transfer process.


### `I-01` — Contract Immutability (Non-Upgradeable)  *(Severity: Informational · Status: Unresolved)*

The `WorldMobileToken` contract is deployed as a standard implementation and does not incorporate any proxy patterns (e.g., UUPS, Transparent). This means the contract's logic is immutable once deployed to the blockchain. While this provides certainty regarding the contract's behavior, it also implies that any future bug fixes, security patches, or feature enhancements would necessitate deploying an entirely new contract and migrating all token holders (7.7 Upgrades).

**Recommendation:** Acknowledge the immutability of the contract. For future projects, consider using upgradeable proxy patterns if flexibility for future updates or bug fixes is desired. For this contract, ensure thorough testing before deployment, as no post-deployment logic changes are possible.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdbb5...39d7`](https://bscscan.com/address/0xdbb5cf12408a3ac17d668037ce289f9ea75439d7) |
| **Network** | BNB Chain |
| **Price** | $0.01895 |
| **24h Volume** | $577.1K |
| **Liquidity** | $440.4K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 91.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1460 buys / 1423 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x4da61cf492de579536ef09709a404b842cd57eaf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/worldmobiletoken-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
