---
token: Portal
ticker: PORTAL
network: ethereum
risk_score: 77
status: critical
date: 2026-06-10
---

# Portal (PORTAL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 77/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/portal-eth)

---

## Audit Summary

The PortalToken contract is an ERC20 token leveraging OpenZeppelin extensions for permit, pausable, and burnable functionalities. It introduces a custom mechanism to calculate circulating supply by subtracting tokens held by a designated proxy address. The audit identified significant centralization risks due to the owner's extensive control over critical functions, and a high dependency on an external proxy contract for accurate circulating supply reporting, which could impact the token's economic stability and market perception.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement a multi-signature wallet or a time-locked contract for the `owner` role to decentralize control over critical functions like pausing, disabling permit, and setting the proxy address. This will reduce the single point of failure risk and introduce a necessary delay for sensitive operations.
Furthermore, a comprehensive security audit of the external `proxy` contract is crucial, along with clear documentation of its operational procedures and security model. For future flexibility, consider adopting an upgradeable proxy pattern for core contracts to allow for seamless bug fixes and feature enhancements without requiring disruptive token migrations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages battle-tested OpenZeppelin libraries for its core ERC20, Ownable, Permit, Pausable, and Burnable functionalities, ensuring a solid foundation (7.2 Code Security). The custom… |
| **Governance / Economics** | 1/10 | High | The token's economic model is a straightforward ERC20 with a fixed total supply and initial distribution to vesting addresses and a treasury. However, the `owner` role holds highly centralized… |
| **Upgrades** | 6/10 | Medium | The `PortalToken` contract is deployed as a standard, non-upgradeable implementation (7.7 Upgrades). This design choice means that any future bug fixes, security patches, or feature enhancements… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `owner` role has extensive control over critical token functions, including pausing transfers (`pause`), enabling/disabling permit functionality (`disablePermit`), and setting the `proxy` address (`setProxyAddress`) which directly impacts the reported `totalSupply`. A compromise of the owner's private key could lead to a complete halt of token operations, manipulation of circulating supply, or disruption of user interactions.

**Recommendation:** Implement a multi-signature wallet or a time-locked contract for the `owner` role to introduce a delay and require multiple approvals for critical operations. This decentralizes control and reduces the risk associated with a single point of failure.


### `H-02` — Critical Dependency on External Proxy for Circulating Supply  *(Severity: High · Status: Unresolved)*

The `totalSupply()` function is overridden to subtract the balance held by a `proxy` address, intended for cross-chain functionality. The security and integrity of the `PortalToken`'s reported circulating supply are critically dependent on the correct functioning and security of this external `proxy` contract. A malicious or compromised `proxy` could manipulate the perceived circulating supply, leading to economic instability or misrepresentation.

**Recommendation:** Thoroughly audit the external `proxy` contract to ensure its robustness and security. Implement strong access controls and monitoring for the `proxy` address. Clearly document the operational procedures and security model of the `proxy` and consider mechanisms to revoke or update the `proxy` address in a secure, multi-party controlled manner.


### `M-01` — Lack of Upgradeability  *(Severity: Medium · Status: Unresolved)*

The `PortalToken` contract is deployed as a standard implementation without any built-in upgradeability mechanism (e.g., UUPS, Transparent proxies). This means that any future bug fixes, security patches, or feature enhancements would necessitate deploying an entirely new token contract and migrating all existing token holders, which is a complex, costly, and disruptive process.

**Recommendation:** For long-term projects, consider implementing an upgradeable proxy pattern (e.g., UUPS) to allow for future contract modifications without requiring a full token migration. If upgradeability is not desired, ensure the current implementation is extremely robust and thoroughly tested.


### `L-01` — Owner Can Disable Permit Functionality  *(Severity: Low · Status: Unresolved)*

The `disablePermit` function allows the owner to enable or disable the ERC20 Permit functionality. While this is an intended feature, disabling `permit` could disrupt user experience or integrations that rely on gasless approvals. This power is centralized with the owner.

**Recommendation:** Clearly communicate the operational policy regarding the `permitEnabled` state. Consider if this control needs to be managed by a multi-sig or a more decentralized mechanism if the project aims for progressive decentralization.


### `I-01` — Reliance on Off-Chain Mitigation for Vesting Deposits  *(Severity: Informational · Status: Unresolved)*

The constructor's comment states that "potential address duplication is mitigated by the deployment scripts" for `vestingDeposits`. This indicates a reliance on off-chain processes to ensure correct initial token distribution. While not a direct contract vulnerability, a failure in the deployment script could lead to unintended initial token allocations.

**Recommendation:** Implement on-chain validation or a more robust deployment process to prevent potential issues with `vestingDeposits` duplication or errors, if possible. Ensure deployment scripts are thoroughly tested and reviewed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1bbe...1fed`](https://etherscan.io/address/0x1bbe973bef3a977fc51cbed703e8ffdefe001fed) |
| **Network** | Ethereum |
| **Price** | $0.01056 |
| **24h Volume** | $246 |
| **Liquidity** | $6.6K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 73.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 386 buys / 331 sells |

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

## Frequently Asked Questions

### Is Portal a scam?

Based on the provided data, we cannot definitively label Portal a scam. However, it exhibits significant red flags often associated with high-risk projects. The high-risk score of 67/100, combined with unrenounced ownership, unlocked liquidity, and extreme token concentration, indicates a strong potential for investor losses due to developer action or market manipulation rather than a secure investment. Investors should proceed with extreme caution.

### Is Portal safe to buy?

Portal is not considered safe to buy based on its current security profile and high-risk score of 67/100. Key risk factors include unrenounced contract ownership, allowing potential malicious changes, and unlocked liquidity, which enables a 'rug pull' by liquidity providers. The highly concentrated token supply, with 66.0% held by the top 10, also poses a significant risk of price manipulation. These factors indicate substantial investment risks.

### Has Portal been audited?

The Portal token contract is verified, meaning its code is publicly available for anyone to review on the blockchain explorer. This transparency is beneficial. However, contract verification is not the same as a professional security audit. An independent security audit involves a thorough review by experts to identify vulnerabilities, logical flaws, and potential attack vectors beyond just code visibility. The provided data does not indicate that Portal has undergone such an audit.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf9bc02a0f79ee8b6982a754979c9dbd909ccee10)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/portal-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
