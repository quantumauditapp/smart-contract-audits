---
token: MOR
ticker: MOR
network: arbitrum
risk_score: 76
status: critical
date: 2026-08-15
---

# MOR (MOR) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 76/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mor-arb)

---

## Audit Summary

The MOROFT contract implements an omnichain ERC-20 token utilizing LayerZero's OFT standard. The audit identified high risks related to centralized minting authority and the contract's immutability, which prevents post-deployment upgrades. Medium risks include critical LayerZero configuration management, while low risks pertain to external dependencies. The project benefits from using audited libraries and a multisig for ownership, but the inherent inflationary mechanism and lack of upgradeability warrant careful consideration.

> **Final Recommendation:** It is recommended to implement robust operational security measures for the multisig owner and any designated minter addresses, including strict key management and multi-factor authentication. Given the contract's immutability, thorough pre-deployment testing and formal verification are crucial to minimize the risk of unpatchable vulnerabilities. Additionally, consider establishing clear policies and transparency around the minting process to manage inflationary expectations and maintain token holder trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages well-audited LayerZero OFT and OpenZeppelin libraries, ensuring robust core ERC-20 functionality and cross-chain messaging (7.2 Code Security). The `supportsInterface`… |
| **Governance / Economics** | 1/10 | High | Critical administrative functions, such as `updateMinter` and LayerZero configurations, are protected by `onlyOwner` and controlled by a 5/9 multisig, enhancing operational security (7.3 Access… |
| **Upgrades** | 6/10 | Medium | The contract's immutability provides certainty regarding its deployed logic, as it cannot be altered post-deployment. However, the `MOROFT` contract is not designed with any upgradeability mechanism… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Centralized Minting Authority and Inflationary Risk  *(Severity: High · Status: Unresolved)*

The `MOROFT` contract includes a `mint` function accessible only by addresses designated as `minter`. The `updateMinter` function, which controls these roles, is restricted to the contract owner. This centralized control over token supply allows the designated minter(s) to mint an arbitrary amount of tokens, introducing significant inflationary risk to the token's economic model (7.4 Economic). A compromise of the minter's private key or a malicious action by the owner could lead to uncontrolled token issuance and severe devaluation.

**Recommendation:** Implement a time-locked or multi-signature mechanism for minting operations, or introduce a maximum minting limit per period. Consider integrating a governance mechanism (e.g., DAO) to approve minting requests, decentralizing control. Ensure strict operational security for the owner multisig and any designated minter addresses.


### `H-02` — Immutability and Lack of Upgradeability  *(Severity: High · Status: Unresolved)*

The `MOROFT` contract is deployed as a standard, non-proxy contract, meaning it is immutable once deployed. There is no mechanism to upgrade the contract's logic (7.7 Upgrades). This poses a significant risk because any critical bugs, vulnerabilities, or necessary feature enhancements discovered post-deployment cannot be patched. Remediation would require deploying a new contract and migrating all token holders, which is a complex, costly, and disruptive process for the protocol and its users.

**Recommendation:** For future deployments, consider implementing an upgradeable proxy pattern (e.g., UUPS or Transparent Proxy) to allow for bug fixes and feature enhancements without requiring a token migration. For the current deployment, ensure extremely thorough testing, formal verification, and a robust incident response plan are in place.


### `M-01` — Critical LayerZero Configuration Management  *(Severity: Medium · Status: Unresolved)*

The `MOROFT` contract inherits from LayerZero's `OFT` contract, which includes several `onlyOwner` functions for critical cross-chain configuration (e.g., `setPeer`, `setTrustedRemote`, `setMinDstGas`, `setFeeManager`). Incorrect configuration of these parameters, or a compromise of the owner's address, could lead to funds being stuck during cross-chain transfers, excessive gas fees, or potential exploits related to message relaying (7.6 External, 7.8 Operations). While the owner is a multisig, the complexity of LayerZero configuration requires careful management.

**Recommendation:** Establish clear, documented procedures for all LayerZero configuration changes. Implement a robust testing environment to validate configuration changes before applying them to production. Consider adding a timelock to critical LayerZero configuration changes to provide a window for review and potential intervention.


### `L-01` — Dependency on External LayerZero Security  *(Severity: Low · Status: Unresolved)*

The `MOROFT` token's omnichain functionality is entirely dependent on the security and operational integrity of the LayerZero protocol. Any vulnerabilities, exploits, or operational failures within the LayerZero network itself could directly impact the `MOROFT` token, potentially leading to loss of funds during cross-chain transfers or disruption of its core functionality (7.6 External).

**Recommendation:** While direct control over LayerZero's core security is not possible, the project should continuously monitor LayerZero's security announcements, audits, and operational status. Maintain a contingency plan for potential LayerZero disruptions, such as communication strategies for users and potential mitigation steps.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x092b...fc86`](https://arbiscan.io/address/0x092baadb7def4c3981454dd9c0a0d7ff07bcfc86) |
| **Network** | Arbitrum |
| **Price** | $1.9400 |
| **24h Volume** | $37.7K |
| **Liquidity** | $1.06M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 71.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 301 buys / 52 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xe5cf22ee4988d54141b77050967e1052bd9c7f7a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mor-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
