---
token: Tevaera
ticker: TEVA
network: base
risk_score: 100
status: critical
date: 2026-08-13
---

# Tevaera (TEVA) — Smart Contract Security Analysis | Base

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tevaera-base)

---

## Audit Summary

The TevaTokenV1 contract, deployed as an upgradeable proxy, implements a standard ERC20 token with burnable, capped, permit, and voting functionalities. It leverages battle-tested OpenZeppelin libraries, providing a solid technical foundation. However, the audit identified significant centralization risks, with a single EOA controlling all critical administrative roles and upgrade capabilities. Additionally, the high potential for token dilution presents a notable economic risk. While the code quality is high, these centralization and economic factors elevate the overall risk profile.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to transition all critical administrative roles, including the `DEFAULT_ADMIN_ROLE`, `MINTER_ADMIN_ROLE`, `BURNER_ADMIN_ROLE`, and the `ProxyAdmin` ownership, to a robust multi-signature wallet (e.g., Gnosis Safe) or a decentralized autonomous organization (DAO). This will eliminate single points of failure and enhance the security posture against private key compromise or malicious intent.

Furthermore, clear communication regarding the token's minting schedule and rationale is crucial, especially given the high potential for dilution. Consider implementing a timelock for significant minting operations or a more granular, transparent control mechanism for supply adjustments to build trust and predictability within the ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract (7.1 Architecture, 7.2 Code Security) utilizes battle-tested OpenZeppelin upgradeable libraries, ensuring a robust and secure foundation for ERC20 functionality, access control, and… |
| **Governance / Economics** | 1/10 | High | The token has a hard cap (MAX_CAP) of 4 billion tokens, and minting/burning are role-gated, providing some economic control (7.4 Economic). ERC20Votes is included, suggesting potential future… |
| **Upgrades** | 1/10 | High | The contract employs the Transparent Upgradeable Proxy pattern with OpenZeppelin's `Initializable` and `_disableInitializers` for safe and standard upgradeability (7.7 Upgrades). This allows for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → EOA |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 3 High · 🟡 2 Medium · 🟢 1 Low_

### `H-01` — Centralized Control of Critical Roles  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE`, `MINTER_ADMIN_ROLE`, and `BURNER_ADMIN_ROLE` are all granted to `msg.sender` during initialization. In a TransparentUpgradeableProxy setup, this `msg.sender` is typically the `ProxyAdmin` owner, which is an EOA (0x936d73597651733e4bf13e305c77fc31b22faabe). This single EOA has complete control over granting and revoking `MINTER_ROLE` and `BURNER_ROLE`, effectively centralizing control over token supply and destruction. A compromise of this EOA would allow an attacker to mint tokens up to the cap or burn tokens arbitrarily.

**Recommendation:** Transfer the `DEFAULT_ADMIN_ROLE`, `MINTER_ADMIN_ROLE`, and `BURNER_ADMIN_ROLE` to a multi-signature wallet (e.g., Gnosis Safe) or a robust DAO governance contract. This distributes control and requires multiple approvals for critical operations, significantly reducing the risk of a single point of failure.


### `H-02` — Centralized Upgrade Authority  *(Severity: High · Status: Unresolved)*

The `TransparentUpgradeableProxy` is controlled by a `ProxyAdmin` contract, which is owned by a single EOA (0x936d73597651733e4bf13e305c77fc31b22faabe). This EOA has sole authority to upgrade the contract's implementation logic. A compromise of this EOA would allow an attacker to deploy malicious contract logic, potentially leading to loss of funds, freezing of assets, or other severe consequences.

**Recommendation:** Transfer ownership of the `ProxyAdmin` contract to a multi-signature wallet or a DAO. This ensures that any future upgrades require consensus from multiple trusted parties, enhancing the security and trustworthiness of the upgrade process.


### `H-03` — High Potential for Token Dilution  *(Severity: High · Status: Unresolved)*

The provided data indicates a `mint_annual_dilution_pct` of 258.14%. While the token has a `MAX_CAP` of 4 billion, this high dilution rate suggests a significant capacity for rapid token inflation. If the `MINTER_ROLE` is misused or compromised, or if the minting schedule is not transparently managed, this could lead to substantial dilution of existing token holders' value, impacting market stability and investor confidence.

**Recommendation:** Clearly communicate the project's minting strategy, schedule, and rationale to the community. Consider implementing additional controls such as a timelock for large minting operations or a more granular, rate-limited minting mechanism to provide greater predictability and prevent sudden supply shocks. Regular transparency reports on token supply changes are also recommended.


### `M-01` — Lack of On-Chain Governance for Critical Parameters  *(Severity: Medium · Status: Unresolved)*

While the contract includes `ERC20VotesUpgradeable`, indicating a potential for off-chain voting, there is no integrated on-chain governance mechanism (e.g., OpenZeppelin Governor) that allows token holders to directly influence critical contract parameters, role assignments, or upgrade decisions. All such decisions currently rest with the centralized administrative EOA.

**Recommendation:** Explore integrating a robust on-chain governance module, such as OpenZeppelin's Governor contracts, to gradually decentralize decision-making power. This would allow token holders to propose, vote on, and execute changes to the contract, including role management and upgrades, thereby enhancing community participation and long-term resilience.


### `M-02` — Reliance on EOA for Critical Operations  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` for the `AccessControl` and the owner of the `ProxyAdmin` are both single External Owned Accounts (EOAs). This creates a single point of failure where the compromise of a single private key could lead to complete control over the token contract, including minting, burning, and upgrading its logic. This poses a significant operational security risk.

**Recommendation:** Transition all critical EOA roles to multi-signature wallets (e.g., Gnosis Safe) with a sufficient number of signers. This enhances security by requiring multiple independent approvals for sensitive operations, significantly reducing the risk associated with a single private key compromise.


### `L-01` — Block Timestamp Dependency for Delegation Expiry  *(Severity: Low · Status: Unresolved)*

The `delegateOnBehalf` function uses `block.timestamp` to check the `_expiry` of a delegation signature. While generally acceptable for time-based checks, `block.timestamp` can be manipulated by miners within a small window (typically up to 15 seconds). This could potentially allow a miner to slightly extend or shorten the validity period of a delegation signature.

**Recommendation:** For delegation expiry, this minor manipulation risk is generally considered acceptable and does not typically pose a critical security threat. No immediate code change is required, but it's important to be aware of this characteristic of `block.timestamp` when designing time-sensitive logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0030...894c`](https://basescan.org/address/0x00309d634d11541b857f927be91ad2f0bd78894c) |
| **Network** | Base |
| **Price** | $0.0005295 |
| **24h Volume** | $50.7K |
| **Liquidity** | $28.5K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 68.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2365 buys / 2318 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x70fd35ad3e981cb924560737a83ec99bf5796ba2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tevaera-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
