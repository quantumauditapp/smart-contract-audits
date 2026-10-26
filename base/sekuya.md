---
token: Sekuya
ticker: SKYA
network: base
risk_score: 40
status: medium
date: 2026-09-03
---

# Sekuya (SKYA) — Smart Contract Security Analysis | Base

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sekuya-base)

---

## Audit Summary

The SekuyaToken contract is an ERC20 token with burnable and access control features, built upon OpenZeppelin libraries. The primary risks identified are the centralized control over token minting and the single point of failure for administrative roles, which could lead to economic instability if compromised. The contract is not upgradeable, limiting future flexibility.

> **Final Recommendation:** It is strongly recommended to implement a robust multi-signature wallet for managing the `DEFAULT_ADMIN_ROLE` and `MINTER_ROLE` to mitigate the single point of failure risk. This would require multiple trusted parties to approve critical operations, enhancing security. Additionally, consider the long-term implications of a non-upgradeable contract; if future flexibility is desired, a proxy pattern should be explored for new deployments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical quality (7.2 Code Security) by leveraging battle-tested OpenZeppelin libraries for ERC20, ERC20Burnable, and AccessControl functionalities. This… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4 Economic) of SekuyaToken relies heavily on a centralized `MINTER_ROLE`, which can mint tokens up to a `MAX_SUPPLY`. This introduces a significant risk of token dilution if the… |
| **Upgrades** | 4/10 | Medium | The SekuyaToken contract is deployed as a standard implementation contract and does not utilize any proxy patterns (7.7 Upgrades). This means the contract's logic is immutable after deployment. While… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 52.0% — Null Address, UNCX |
| **Top-1 Unlocked Holder** | 28.2% |
| **Top-3 Unlocked** | 47.9% |

## Security Findings

_🟡 2 Medium · ⚪ 2 Informational_

### `M-01` — Single Point of Failure for Administrative Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract's constructor grants both the `DEFAULT_ADMIN_ROLE` and `MINTER_ROLE` to the deployer's address (`_msgSender()`). This design creates a single point of failure for all administrative functions and token minting. If the private key associated with this single address is compromised, an attacker could gain full control over role management (granting/revoking any role) and the ability to mint tokens up to the maximum supply.

**Recommendation:** Transfer the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet immediately after deployment. This will distribute control and require multiple approvals for critical administrative actions, significantly reducing the risk associated with a single compromised key.


### `M-02` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MINTER_ROLE` has the authority to mint new tokens up to the `MAX_SUPPLY` (1 billion tokens). This centralized control over the token supply introduces a significant economic risk, as the token supply can be increased by a single entity, potentially leading to dilution for existing token holders if not managed transparently and responsibly. This power is granted to the deployer in the constructor.

**Recommendation:** Implement a multi-signature wallet for the `MINTER_ROLE` to ensure that minting operations require consensus from multiple trusted parties. Clearly communicate the minting policy and schedule to the community. Consider mechanisms to decentralize or restrict minting power further in the future if appropriate for the project's roadmap.


### `I-01` — Non-Upgradeable Contract  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SekuyaToken` contract is deployed as a standard implementation contract and does not utilize any proxy patterns (e.g., UUPS, Transparent). This means that the contract's logic is immutable after deployment. Any future bug fixes, feature enhancements, or changes to the token's economic model would necessitate deploying an entirely new contract and migrating existing token holders, which can be a complex and costly process.

**Recommendation:** While not a vulnerability, it's important for the project team to be aware of this limitation. For future projects or if flexibility is a high priority, consider implementing an upgradeable proxy pattern (e.g., UUPS) to allow for future contract modifications without requiring a full redeployment and migration.


### `I-02` — Hardcoded Maximum Supply  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MAX_SUPPLY` for the token is defined as a `public constant` within the contract. While this provides clarity and prevents accidental changes, it means the maximum possible token supply cannot be adjusted after deployment without deploying a new contract. This rigidity might limit future economic model adjustments if the project's needs evolve.

**Recommendation:** Ensure that the `MAX_SUPPLY` value is thoroughly reviewed and aligns with the long-term vision for the token's economics. If future flexibility for supply adjustments is desired, consider making the `MAX_SUPPLY` a state variable that can be modified by a privileged role (e.g., `DEFAULT_ADMIN_ROLE`) under strict governance, though this introduces its own set of risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x623c...b6e9`](https://basescan.org/address/0x623cd3a3edf080057892aaf8d773bbb7a5c9b6e9) |
| **Network** | Base |
| **Price** | $0.000377 |
| **24h Volume** | $4.9K |
| **Liquidity** | $19.3K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 46.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1842 buys / 1754 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x795d45b4c50c906fa0bc2a0ae99d9e862aafaf2e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sekuya-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
