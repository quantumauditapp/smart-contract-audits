---
token: Flower
ticker: FLOWER
network: base
risk_score: 33
status: medium
date: 2026-08-11
---

# Flower (FLOWER) — Smart Contract Security Analysis | Base

> **Risk Score: 33/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flower-base)

---

## Audit Summary

The FlowerOFT contract implements an ERC-20 token with Pausable and ERC-1363 extensions, leveraging LayerZero v2 for omnichain functionality. The contract is well-structured, inheriting from established OpenZeppelin and LayerZero libraries. Key controls, such as pausing transfers, are managed by a single owner address, which is a multisig, mitigating some centralization risks.

> **Final Recommendation:** Ensure the multisig controlling the `Ownable` address is managed with the highest security standards, including robust key management, clear operational procedures, and regular audits of its members. For future iterations, consider implementing a time-lock for critical administrative actions like pausing/unpausing to provide a grace period for users and further decentralize control. Thoroughly monitor LayerZero security announcements and best practices to maintain the integrity of the omnichain functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) is sound, utilizing battle-tested OpenZeppelin and LayerZero libraries for core ERC-20, pausable, and omnichain functionalities. Code security (7.2) benefits from… |
| **Governance / Economics** | 4/10 | Medium | Access control (7.3) is primarily managed by the `Ownable` pattern, granting the owner the ability to pause and unpause token transfers. The prefill indicates the owner is a multisig with a 2/5… |
| **Upgrades** | 6/10 | Medium | The FlowerOFT contract is deployed as an immutable contract, as confirmed by the `is_proxy: false` status (7.7 Upgrades). This design choice eliminates risks associated with upgrade mechanisms, such… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 33.6% |
| **Top-3 Unlocked** | 48.6% |

## Security Findings

_🟡 1 Medium · ⚪ 3 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The `Ownable` owner has significant control over the contract, specifically the ability to pause and unpause all token transfers. While the prefill indicates the owner is a multisig (2/5 threshold), this still represents a central point of control. If the multisig keys are compromised, or if the signers collude or act maliciously, it could lead to a denial of service for token holders or other adverse actions.

**Recommendation:** Ensure robust security practices for the multisig, including strong key management, secure operational procedures, and regular audits of multisig members. For critical operations like pausing, consider implementing a time-lock to provide a delay before execution, allowing users to react and increasing transparency. Explore options for more decentralized governance if the project's roadmap allows.


### `I-01` — Dependency on LayerZero v2 Security  *(Severity: Informational · Status: Unresolved)*

The `FlowerOFT` contract heavily relies on the security and correct functioning of the LayerZero v2 protocol and its endpoint for its omnichain capabilities (7.6 External). Any vulnerabilities, misconfigurations, or operational issues within the LayerZero infrastructure could directly impact the cross-chain functionality, integrity, and availability of the FlowerOFT token.

**Recommendation:** Maintain continuous monitoring of LayerZero security announcements, updates, and best practices. Ensure the `_lzEndpoint` address configured in the constructor is the official and trusted LayerZero endpoint for the respective network. Understand the implications of LayerZero's security model and its impact on the token's overall risk profile.


### `I-02` — Immutability and Lack of Upgradeability  *(Severity: Informational · Status: Unresolved)*

The contract is not designed with an upgradeability mechanism (e.g., proxy pattern), as confirmed by the `is_proxy: false` status (7.7 Upgrades). While this reduces complexity and eliminates certain upgrade-related risks, it means that any discovered critical vulnerabilities or desired feature enhancements would necessitate a new contract deployment and a potentially complex migration process for existing token holders and integrated protocols.

**Recommendation:** Acknowledge the implications of immutability. For future projects or if long-term flexibility, bug fixes, or feature additions are anticipated, consider implementing an upgradeable proxy pattern (e.g., UUPS) from the outset. For the current contract, ensure thorough testing and auditing before deployment to minimize the chance of needing a redeployment.


### `I-03` — Pausable Mechanism Impact  *(Severity: Informational · Status: Unresolved)*

The `Pausable` mechanism allows the `onlyOwner` to halt all token transfers by calling `pause()` (7.3 Access Control). While intended for emergency situations like critical bug discovery or exploit mitigation, it introduces a single point of failure for token utility. If the owner account is compromised or acts maliciously, it could lead to a denial of service for all token holders.

**Recommendation:** Clearly communicate the purpose and conditions under which the pause function would be used to the community. Consider adding a time-lock for the `pause()` and `unpause()` functions, or requiring a multi-party decision mechanism for unpausing in future versions, to further decentralize control and provide transparency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e12...b380`](https://basescan.org/address/0x3e12b9d6a4d12cd9b4a6d613872d0eb32f68b380) |
| **Network** | Base |
| **Price** | $0.102 |
| **24h Volume** | $118.4K |
| **Liquidity** | $254.1K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 585 buys / 630 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xafe30319a948f322585fafc1cab1671a47eb3786)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flower-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
