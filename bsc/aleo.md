---
token: Aleo
ticker: ALEO
network: bsc
risk_score: 78
status: high
date: 2026-09-26
---

# Aleo (ALEO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 78/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aleo-bsc)

---

## Audit Summary

The WrappedTokens contract implements an upgradeable ERC-20 token with burnable, pausable, and permit functionalities, leveraging OpenZeppelin's battle-tested libraries. The contract utilizes AccessControl for managing DEFAULT_ADMIN_ROLE, PAUSER_ROLE, and MINTER_ROLE. While the architecture is sound and follows best practices for upgradeable tokens, significant centralization risks exist due to the powers granted to the MINTER_ROLE and PAUSER_ROLE, which can impact token supply and transferability. The DEFAULT_ADMIN_ROLE also represents a single point of failure for overall role management.

> **Final Recommendation:** It is strongly recommended to implement robust multi-signature controls for all critical roles, especially the DEFAULT_ADMIN_ROLE, MINTER_ROLE, and PAUSER_ROLE, to mitigate the risks associated with centralized control. Consider implementing a time-lock mechanism for sensitive administrative actions to provide a window for community review or emergency intervention. Additionally, evaluate the necessity and scope of the MINTER_ROLE's unlimited minting capability and explore options for capping or decentralizing this power if feasible for the project's long-term vision.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract is built upon well-audited OpenZeppelin upgradeable libraries, ensuring a solid foundation for code security (7.2) and architectural patterns (7.1). Standard ERC-20, burnable, pausable… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) of the WrappedTokens contract presents a high degree of centralization. The MINTER_ROLE has unlimited minting capability, posing a significant inflation risk if compromised.… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS proxy pattern (7.7) using OpenZeppelin's `Initializable` and upgradeable base contracts. The `_disableInitializers()` in the constructor and the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `MINTER_ROLE` possesses the unrestricted ability to mint new tokens. This centralization introduces a significant economic risk (7.4), as a compromised or malicious minter could inflate the token supply, devaluing existing holdings and impacting the token's stability. This is an access control flaw (7.3) with direct economic consequences.

**Recommendation:** Implement multi-signature control for the `MINTER_ROLE` to require multiple approvals for minting operations. Consider introducing a minting cap or a rate limit to control inflation. If possible, explore mechanisms to decentralize or remove the minting capability entirely once the desired supply is reached.


### `H-02` — Centralized Pausing Authority  *(Severity: High · Status: Unresolved)*

The `PAUSER_ROLE` can unilaterally pause and unpause all token transfers. While useful for emergency situations, this power can disrupt liquidity, prevent users from moving funds, and potentially be abused if the role is compromised (7.3). This poses a significant operational and economic risk (7.4, 7.8).

**Recommendation:** Implement multi-signature control for the `PAUSER_ROLE`. Consider adding a time-lock for unpausing functionality to allow for community review or emergency response. Clearly define the conditions under which pausing is permissible in project documentation.


### `M-01` — Critical Role Management by Default Admin  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke all other roles, including `MINTER_ROLE` and `PAUSER_ROLE`. This makes the `DEFAULT_ADMIN_ROLE` a single point of failure (7.3, 7.8); its compromise would grant an attacker full control over the token's critical functions, including minting and pausing.

**Recommendation:** Implement multi-signature control for the `DEFAULT_ADMIN_ROLE` to ensure that no single entity can unilaterally manage critical roles. Consider transferring the `DEFAULT_ADMIN_ROLE` to a robust governance mechanism or a DAO if applicable.


### `L-01` — Dependency on OpenZeppelin Libraries  *(Severity: Low · Status: Unresolved)*

The contract extensively uses OpenZeppelin's upgradeable contracts. While these libraries are widely audited and considered secure, any future vulnerabilities discovered within them could indirectly impact the `WrappedTokens` contract (7.2, 7.6). This is a general risk inherent in using external dependencies.

**Recommendation:** Stay informed about security updates and advisories from OpenZeppelin. Regularly review the project's dependencies and consider upgrading to newer versions if security patches are released. This is a continuous operational security practice.


### `I-01` — Hardcoded Decimals  *(Severity: Informational · Status: Unresolved)*

The `decimals()` function is explicitly set to return `6`. This is a design decision and not a vulnerability (7.1), but it's a critical parameter for all integrations (e.g., exchanges, wallets, dApps) and should be clearly communicated to users and developers to prevent misinterpretation of token values.

**Recommendation:** Ensure that the fixed decimal value of 6 is prominently documented in all relevant project materials, including whitepapers, developer guides, and API specifications, to avoid integration errors.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6cff...4dd2`](https://bscscan.com/address/0x6cfffa5bfd4277a04d83307feedfe2d18d944dd2) |
| **Network** | BNB Chain |
| **Price** | $0.02768 |
| **24h Volume** | $556.5K |
| **Liquidity** | $194.7K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2008 buys / 1977 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa325b22090aa2d5528b01cc6974699da4b9cc875)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aleo-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-26*
