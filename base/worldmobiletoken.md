---
token: WorldMobileToken
ticker: WMTX
network: base
risk_score: 50
status: medium
date: 2026-09-25
---

# WorldMobileToken (WMTX) — Smart Contract Security Analysis | Base

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/worldmobiletoken-base)

---

## Audit Summary

The WorldMobileToken contract is an ERC20 token implementation leveraging OpenZeppelin's ERC20Capped, ERC20Permit, and AccessControl libraries. It features a fixed supply cap and defined roles for minting and burning. The primary security concern identified is the high degree of centralization, with the deployer initially holding all critical administrative roles, posing a single point of failure.

> **Final Recommendation:** To enhance the security posture of the WorldMobileToken, it is strongly recommended to decentralize control over critical administrative roles. Specifically, the `DEFAULT_ADMIN_ROLE` should be transferred to a robust multi-signature wallet or a well-governed DAO. This will prevent a single point of failure and require multiple approvals for sensitive operations like granting/revoking minter or burner roles.

Furthermore, establish and publicly document clear policies and procedures for the exercise of minting and burning capabilities. This transparency will build trust and provide predictability for token holders regarding potential supply adjustments. Consider implementing time-locks or community governance for any significant changes to the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical foundations by inheriting from battle-tested OpenZeppelin contracts for ERC20, capping, permit functionality, and access control (7.2 Code Security). The… |
| **Governance / Economics** | 2/10 | High | The token incorporates a fixed supply cap of 2 billion tokens (with 6 decimals), providing predictability for token holders (7.4 Economic). However, the `MINTER_ROLE` and `BURNER_ROLE` grant… |
| **Upgrades** | 3/10 | High | The WorldMobileToken contract is deployed as a standard, non-upgradeable implementation (7.7 Upgrades). This design choice eliminates the complexities and potential risks associated with upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.5% |
| **Top-3 Unlocked** | ⚠️ 97.2% |

## Security Findings

_🟡 2 Medium · ⚪ 1 Informational_

### `M-01` — Economic Impact of Minting/Burning Authority  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MINTER_ROLE` and `BURNER_ROLE` provide the capability to dynamically increase or decrease the token supply within the defined cap. While the cap limits the maximum supply, the discretion to mint new tokens or burn existing ones can have a significant impact on the token's economic value and stability if not managed transparently and predictably. Without clear governance policies, the exercise of these powers could lead to unexpected inflation or deflation, potentially harming token holders. (7.4 Economic, 7.5 Governance)

**Recommendation:** Establish and publicly communicate a clear policy for when and how minting and burning operations will be conducted. Consider implementing additional governance mechanisms, such as time-locks for large mints/burns or requiring community proposals for significant supply adjustments, to enhance transparency and predictability. This will help mitigate the risk of economic manipulation and build community confidence.


### `M-02` — Centralized Control of Critical Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constructor of the WorldMobileToken contract grants the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `BURNER_ROLE` to the deployer address (`_msgSender()`). This design centralizes complete control over token supply management (minting up to the cap, burning tokens) and the ability to assign/revoke other roles to a single external owned account (EOA). A compromise of this single EOA's private key would allow an attacker to mint new tokens (up to the cap), burn existing tokens, and arbitrarily reassign roles, leading to significant economic damage and loss of trust. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Transfer the `DEFAULT_ADMIN_ROLE` to a multi-signature wallet (e.g., Gnosis Safe) immediately after deployment. This will require multiple trusted parties to approve any administrative actions, significantly reducing the risk of a single point of failure or malicious activity. Consider also assigning the `MINTER_ROLE` and `BURNER_ROLE` to separate, controlled addresses or multi-sigs if their operations are distinct.


### `I-01` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The WorldMobileToken contract is deployed directly without utilizing an upgradeable proxy pattern. This means that the contract's logic is immutable and cannot be modified or updated after deployment. While this eliminates risks associated with upgrade mechanisms (e.g., proxy vulnerabilities, improper upgrade paths), it also means that any future bug fixes, security patches, or feature enhancements would necessitate deploying an entirely new contract and migrating all token holders. (7.7 Upgrades, 7.1 Architecture)

**Recommendation:** This is a design choice. Ensure that the current implementation has undergone thorough testing and auditing to minimize the likelihood of needing future changes. If future flexibility is desired, consider a migration plan to an upgradeable contract in the long term, or accept the immutability as a feature that guarantees unchanging contract behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e31...e98d`](https://basescan.org/address/0x3e31966d4f81c72d2a55310a6365a56a4393e98d) |
| **Network** | Base |
| **Price** | $0.02439 |
| **24h Volume** | $305.0K |
| **Liquidity** | $397.1K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 71.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 443 buys / 462 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x18c772b1e324256d4eae3d444aed7e856a6d86e2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/worldmobiletoken-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
