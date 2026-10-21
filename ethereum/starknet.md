---
token: Starknet
ticker: STRK
network: ethereum
risk_score: 69
status: high
date: 2026-09-18
---

# Starknet (STRK) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 69/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/starknet-eth)

---

## Audit Summary

The StarkNet Token contract is a standard ERC20 token with voting capabilities and role-based access control, primarily utilizing OpenZeppelin libraries. The core functionality is sound, but significant centralization risks exist due to the minting authority and the single point of control for administrative roles. The contract is immutable, which eliminates upgrade risks but prevents future fixes or feature additions.

> **Final Recommendation:** To mitigate the identified high risks, it is strongly recommended to decentralize the control of the `DEFAULT_ADMIN_ROLE` and `MINTER_ROLE`. Transfer these critical roles to a robust multi-signature wallet with a sufficient number of trusted signers or, ideally, to a decentralized autonomous organization (DAO) governance contract. Additionally, consider implementing a timelock for critical administrative actions, such as granting or revoking roles, to provide a window for community review and emergency intervention. For future token designs, evaluate the inclusion of an emergency pause mechanism to provide a safety net against unforeseen exploits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract architecture (7.1) is straightforward, implementing a standard ERC20 token with OpenZeppelin's AccessControl and ERC20Votes. Code security (7.2) is robust due to the extensive use of… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) carries a high risk due to the `mint` function, which allows an authorized `MINTER_ROLE` to create an arbitrary amount of tokens, potentially leading to hyperinflation and… |
| **Upgrades** | 3/10 | High | The contract is not designed to be upgradeable (7.7), which eliminates all risks associated with upgrade mechanisms, such as proxy implementation bugs or improper upgrade paths. This immutability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `mint` function allows an account with the `MINTER_ROLE` to create an arbitrary amount of new tokens. This capability, if misused or compromised, can lead to uncontrolled supply inflation, devaluing existing tokens and disrupting the token's economic stability. The `MINTER_ROLE` is initially controlled by the `DEFAULT_ADMIN_ROLE`.

**Recommendation:** Transfer the `MINTER_ROLE` to a secure multi-signature wallet or a DAO governance contract. Implement a timelock for minting operations and consider adding rate limits or caps on the amount that can be minted within a specific period.


### `H-02` — Centralized Role Management  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has complete authority over all other roles, including the `MINTER_ROLE`. This creates a single point of failure: if the private key controlling the `DEFAULT_ADMIN_ROLE` is compromised, an attacker could gain full administrative control, including the ability to mint tokens and manage all other roles without restriction.

**Recommendation:** Transfer the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet or a DAO governance contract. Implement a timelock for any changes to role administrators or the granting/revoking of critical roles to allow for community oversight and emergency response.


### `M-01` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The contract lacks a mechanism to pause token transfers or minting in emergency situations, such as a critical vulnerability discovery, a major exploit in an integrated DeFi protocol, or a significant market manipulation event. Without a pause function, the project team would have limited ability to mitigate ongoing damage during an incident.

**Recommendation:** Consider integrating OpenZeppelin's `Pausable` contract. This would allow a designated role (e.g., controlled by a multi-signature wallet or governance) to temporarily halt critical operations, providing a safety mechanism during emergencies.


### `I-01` — Immutability of Contract Logic  *(Severity: Informational · Status: Unresolved)*

The `StarkNetToken` contract is deployed as a standard, non-upgradeable contract. This design choice eliminates the complexities and potential risks associated with upgrade mechanisms (e.g., proxy implementation bugs, improper upgrade paths). However, it also means that any discovered vulnerabilities or desired feature enhancements cannot be addressed without deploying a new contract and migrating all token holders.

**Recommendation:** Acknowledge the implications of immutability. For future projects, carefully evaluate the trade-offs between immutability (simplicity, reduced upgrade risk) and upgradeability (flexibility for bug fixes, feature additions) based on the project's long-term strategy and risk tolerance.


### `I-02` — Reliance on OpenZeppelin Contracts  *(Severity: Informational · Status: Unresolved)*

The contract extensively utilizes battle-tested and widely audited OpenZeppelin libraries for core functionalities such as ERC20, AccessControl, and ERC20Votes. This significantly reduces the likelihood of common low-level vulnerabilities (e.g., reentrancy, integer overflows) in the implemented components, contributing to a higher baseline of code security.

**Recommendation:** Continue to monitor OpenZeppelin's security advisories and ensure that any future deployments or integrations with OpenZeppelin contracts are based on the latest stable and audited versions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xca14...2766`](https://etherscan.io/address/0xca14007eff0db1f8135f4c25b34de49ab0d42766) |
| **Network** | Ethereum |
| **Price** | $0.03583 |
| **24h Volume** | $81.6K |
| **Liquidity** | $94.3K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 68.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 108 buys / 41 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x7e5e452e215b011fa394c8e1903be800f6872f0a6b7f45f078b7cac40af13c26)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/starknet-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-18*
