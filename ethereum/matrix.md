---
token: Matrix
ticker: MTX
network: ethereum
risk_score: 41
status: medium
date: 2026-08-30
---

# Matrix (MTX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/matrix-eth)

---

## Audit Summary

The MTXTokenV1 contract is an upgradeable ERC-20 token utilizing OpenZeppelin's battle-tested libraries. It includes a sanctions list mechanism and owner-controlled upgradeability. While the core implementation is robust, significant risks stem from the centralized control over the sanctions list and the owner's extensive authority, particularly regarding upgrades and external dependencies.

> **Final Recommendation:** It is recommended to implement a robust governance mechanism for critical functions, especially for updating the `sanctionsList` and initiating upgrades, to mitigate the risks associated with centralized control. Consider introducing a time-lock or multi-signature approval process for these sensitive operations to provide a window for review and prevent immediate malicious actions. Additionally, evaluate the necessity and scope of the sanctions mechanism to ensure it aligns with the project's decentralization goals and user expectations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin upgradeable libraries for ERC-20, ERC-20 Permit, Ownable, and UUPS functionalities, demonstrating sound architectural choices (7.1 Architecture, 7.2… |
| **Governance / Economics** | 4/10 | Medium | The token's economic model involves an initial fixed supply distribution to specific addresses, with no further minting or burning functions (7.4 Economic). A major governance and economic risk is… |
| **Upgrades** | 2/10 | High | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's `UUPSUpgradeable` (7.7 Upgrades). Storage compatibility is maintained with the `__gap` variable, ensuring smooth future… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Owner's Extensive Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` role holds significant power within the `MTXTokenV1` contract. This includes the ability to upgrade the contract logic via the UUPS proxy pattern, change the `metadataURI`, and critically, update the `sanctionsList` contract. While the owner is identified as a contract (likely a multi-sig), a compromise of this owner contract would grant an attacker full control over the token's functionality, including the ability to introduce malicious logic through an upgrade or arbitrarily freeze user funds via the sanctions list (7.3 Access Control, 7.7 Upgrades, 7.8 Operations).

**Recommendation:** Strengthen the security of the owner contract, ensuring it is a robust multi-signature wallet or a well-audited governance contract with appropriate safeguards. For highly sensitive operations like upgrades and `sanctionsList` changes, consider adding a timelock mechanism to allow for community review and potential intervention before changes take effect.


### `M-02` — Centralized Sanctions List Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MTXTokenV1` contract relies on an external `ISanctionsList` contract to restrict token transfers for sanctioned addresses. The `owner` has the sole authority to update this `sanctionsList` to any arbitrary address via `setSanctionsList`. A malicious or compromised `SanctionsList` contract, or a compromised owner, could arbitrarily freeze funds or block transfers for any address, leading to significant censorship risk and potential loss of access to funds for users (7.3 Access Control, 7.4 Economic, 7.6 External).

**Recommendation:** Implement a more decentralized or time-locked approach for updating the `sanctionsList`. Consider requiring multiple approvals (e.g., via a multi-sig or DAO governance) and/or a timelock delay before a new `sanctionsList` address becomes active. Clearly document the criteria and process for sanctioning addresses and the expected behavior of the `ISanctionsList` contract.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MTXTokenV1` contract does not include a pause mechanism. In the event of a critical vulnerability discovered within the token contract itself, or an external attack on a dependency (such as the `SanctionsList`), there is no way for the owner or a governance body to temporarily halt operations to mitigate damage or fix the issue. This could lead to irreversible losses if an exploit is discovered and cannot be immediately contained (7.2 Code Security, 7.8 Operations).

**Recommendation:** Consider implementing an emergency pause mechanism (e.g., using OpenZeppelin's `PausableUpgradeable` contract). This would allow the owner (or a designated emergency multi-sig) to temporarily pause transfers and other critical functions in case of an unforeseen exploit or emergency, providing time to address the issue without further loss.


### `I-01` — Fixed Decimals (6)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The token's `decimals()` function is hardcoded to return 6, which is a non-standard value for ERC-20 tokens (typically 18). While this is a valid design choice and explicitly defined, it's important for integrators and users to be aware of this specific decimal value to prevent potential calculation errors or display issues in external systems, wallets, or DeFi protocols that might assume 18 decimals by default (7.4 Economic).

**Recommendation:** Ensure that all documentation, front-end interfaces, and integration guides clearly communicate that the MTX token uses 6 decimals. Developers integrating with the token should explicitly account for this decimal value in their calculations to avoid discrepancies.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...0000`](https://etherscan.io/address/0x000025b3816630ad283267d4eb3a5fc8b0200000) |
| **Network** | Ethereum |
| **Price** | $39.2000 |
| **24h Volume** | $24.7K |
| **Liquidity** | $2.97M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 105.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 185 buys / 26 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x0a900074fbfd3200bd33f3d81f7f56c77487bb1b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/matrix-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
