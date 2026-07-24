---
token: Caldera
ticker: ERA
network: ethereum
risk_score: 84
status: critical
date: 2026-07-22
---

# Caldera (ERA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 84/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/caldera-eth)

---

## Audit Summary

This audit focused on the provided ERC1967Proxy contract, which is a standard UUPS proxy implementation from OpenZeppelin. The proxy contract itself is robust and well-tested. However, a full security assessment is significantly limited as the source code for the associated implementation contract (CalderaToken) was not provided and is unverified. Key risks identified relate to the security of the upgrade mechanism's administrative control and potential storage collision issues if the implementation is not carefully designed.

> **Final Recommendation:** Prioritize a full audit of the implementation contract (CalderaToken) to ensure its security, especially regarding access control for upgrade functions, storage layout, and overall business logic. Implement robust administrative controls for upgrades, such as a multi-signature wallet or a timelock, to mitigate the risk of unauthorized or malicious upgrades. Thoroughly test all upgrade paths in a staging environment before deployment to production.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The audited contract is a standard OpenZeppelin ERC1967Proxy, which is a well-vetted and widely used UUPS proxy implementation (7.1 Architecture). Its `delegatecall` mechanism is correctly… |
| **Governance / Economics** | 1/10 | High | The economic and governance risks are primarily tied to the upgradeability mechanism (7.5 Governance). As a UUPS proxy, the administrative control for upgrades resides within the implementation… |
| **Upgrades** | 1/10 | High | The contract implements the UUPS (ERC-1967) proxy pattern, allowing for seamless upgrades of the underlying logic (7.7 Upgrades). This flexibility is a strength, but also introduces significant risk… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟠 2 High · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Lack of Implementation Contract Source Code  *(Severity: High · Status: Unresolved)*

The source code for the proxy's implementation contract (0x1a91caf199a6b309d9c74a9b43aed8c6674d6e43, 'CalderaToken') was not provided and is unverified on-chain. This severely limits the scope of the audit, as the security of the entire system heavily relies on the implementation's logic, including its access control, business logic, and storage management. Without this, potential vulnerabilities such as reentrancy, integer overflows, or critical access control flaws within the core logic cannot be identified (7.2 Code Security, 7.3 Access Control).

**Recommendation:** Provide the full, verified source code for the implementation contract (CalderaToken) to allow for a comprehensive security audit of the entire system. Ensure the implementation contract is thoroughly reviewed for all common vulnerability patterns.


### `H-02` — Criticality of Admin Key Security for UUPS Upgrades  *(Severity: High · Status: Unresolved)*

As a UUPS proxy, the ability to upgrade the implementation logic resides within a function in the implementation contract itself (e.g., `_authorizeUpgrade` or `upgradeTo`). The security of the address or mechanism controlling this upgrade function is paramount. If this administrative control is compromised, an attacker could upgrade the contract to a malicious implementation, leading to complete loss of funds or control over the protocol (7.3 Access Control, 7.7 Upgrades). The prefill indicates no admin slot populated, which is expected for UUPS, meaning the admin logic is in the implementation.

**Recommendation:** Ensure the administrative control for the upgrade function in the implementation contract is secured by a robust mechanism, such as a multi-signature wallet with a high threshold, a timelock, or a well-tested governance module. Avoid single points of failure for upgradeability control.


### `L-01` — Potential for Storage Collisions in Implementation  *(Severity: Low · Status: Unresolved)*

When using a proxy pattern, it is crucial that the implementation contract's storage layout does not conflict with the proxy's reserved storage slots (e.g., `IMPLEMENTATION_SLOT`, `ADMIN_SLOT`, `BEACON_SLOT` as defined in ERC1967Utils). While OpenZeppelin's UUPS proxy handles its own storage correctly, a poorly designed implementation contract could inadvertently overwrite these slots or suffer from its own state variables being overwritten by future upgrades if not carefully managed (7.7 Upgrades).

**Recommendation:** Ensure that all implementation contracts adhere strictly to the UUPS storage layout guidelines. Specifically, avoid declaring state variables at the beginning of the implementation contract that might collide with the proxy's reserved slots. Use tools like `hardhat-upgrades` or `forge-upgrades` to verify storage compatibility during development and before each upgrade.


### `L-02` — Upgrade Function Protection Best Practices  *(Severity: Low · Status: Unresolved)*

The `upgradeToAndCall` function, which is called by the proxy's constructor and typically by the upgrade function in the implementation, is critical. While the `ERC1967Utils` library handles the low-level upgrade, the public-facing upgrade function in the implementation contract must be adequately protected. Without proper access control (e.g., `onlyOwner` or a governance mechanism) and potentially a timelock, an upgrade could be front-run or executed maliciously (7.3 Access Control, 7.6 External).

**Recommendation:** Implement robust access control for the upgrade function within the implementation contract. Consider adding a timelock to introduce a delay between proposing and executing an upgrade, allowing users to react and reducing the risk of front-running or malicious rapid upgrades.


### `I-01` — Standard OpenZeppelin ERC1967Proxy Implementation  *(Severity: Informational · Status: Resolved)*

The contract utilizes the `ERC1967Proxy` from OpenZeppelin Contracts, which is a widely adopted and thoroughly audited implementation of the UUPS (Universal Upgradeable Proxy Standard) pattern. This provides a solid and secure foundation for upgradeability, leveraging battle-tested code for its core proxy logic (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Continue to rely on well-established and audited libraries like OpenZeppelin for core infrastructure components. Ensure that any custom modifications or integrations with this proxy are also thoroughly reviewed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe2ad...de2a`](https://etherscan.io/address/0xe2ad0bf751834f2fbdc62a41014f84d67ca1de2a) |
| **Network** | Ethereum |
| **Price** | $0.104 |
| **24h Volume** | $7.2K |
| **Liquidity** | $10.7K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 380 buys / 321 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x4d63da0421ab1d71fbf2a3d3c8625a66d9b9799d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/caldera-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
