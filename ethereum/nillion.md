---
token: Nillion
ticker: NIL
network: ethereum
risk_score: 79
status: critical
date: 2026-07-28
---

# Nillion (NIL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 79/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nillion-eth)

---

## Audit Summary

The audit covers an ERC-20 token contract, Nillion, implemented as an upgradeable UUPS proxy. The contract utilizes OpenZeppelin's battle-tested libraries for ERC-20, burnable functionality, access control, and upgradeability. Key roles such as DEFAULT_ADMIN_ROLE, MINTER_ROLE, BURNER_ROLE, and UPGRADER_ROLE are initially assigned to the deployer address, creating a highly centralized control structure. While the code itself is well-structured, this centralization introduces significant economic and operational risks, particularly concerning unlimited minting, arbitrary burning, and unchecked upgrade capabilities.

> **Final Recommendation:** Prioritize decentralizing control over critical administrative and operational roles. Implement a robust multi-signature wallet for the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, `BURNER_ROLE`, and `UPGRADER_ROLE` to mitigate single points of failure and enhance security. Carefully evaluate the necessity of continuous unlimited minting and arbitrary burning capabilities; if not essential, consider revoking or restricting these roles. For upgrades, consider adding a timelock mechanism to provide a delay for community review before changes are enacted.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture is sound, leveraging OpenZeppelin's upgradeable contracts for ERC-20, burnable tokens, and UUPS proxy patterns (7.1 Architecture). The custom logic for `burn` and… |
| **Governance / Economics** | 1/10 | High | The contract's economic model features an initial supply of 1 billion tokens with 6 decimals. A primary concern is the highly centralized control over critical economic functions (7.4 Economic). The… |
| **Upgrades** | 1/10 | High | The contract employs the UUPS upgradeability pattern, a standard and robust mechanism for contract evolution (7.7 Upgrades). The `_authorizeUpgrade` function is correctly restricted by the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟠 3 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Centralized Control of Critical Roles (Minter, Burner, Upgrader, Admin)  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, `BURNER_ROLE`, and `UPGRADER_ROLE` are all initially granted to the `msg.sender` (initializer). The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke all other roles, including itself. This high degree of centralization means that a compromise of this single address would grant an attacker full control over token minting, burning (from any address), and contract upgradeability, posing a critical risk to the protocol's integrity and user funds (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Implement a robust multi-signature wallet (e.g., Gnosis Safe) for the `DEFAULT_ADMIN_ROLE` to distribute control and require multiple approvals for critical operations. Consider delegating specific roles (e.g., `MINTER_ROLE`, `BURNER_ROLE`) to separate, potentially more restricted, entities or smart contracts if their functionality is required long-term.


### `H-02` — Unlimited Minting Capability  *(Severity: High · Status: Unresolved)*

The `MINTER_ROLE` allows an authorized address to mint an arbitrary amount of new tokens at any time. This capability can lead to uncontrolled supply inflation, significantly devaluing existing tokens and impacting the project's economy (7.4 Economic, 7.3 Access Control).

**Recommendation:** Evaluate if continuous minting is truly necessary. If not, consider revoking the `MINTER_ROLE` after the initial token distribution. If minting is required, implement a controlled minting mechanism (e.g., capped minting, time-locked minting, or a governance-controlled minting process) to prevent arbitrary supply increases.


### `H-03` — Arbitrary Token Burning Capability  *(Severity: High · Status: Unresolved)*

The `BURNER_ROLE` allows an authorized address to burn tokens from *any* specified address (`from`). This means a malicious or compromised `BURNER_ROLE` holder could drain tokens from user accounts, leading to direct loss of user funds (7.4 Economic, 7.3 Access Control).

**Recommendation:** Re-evaluate the necessity of the `BURNER_ROLE` having the ability to burn from arbitrary addresses. If burning is only intended for specific scenarios (e.g., protocol-owned tokens, specific user opt-in), restrict the `burn` function to only allow burning from `msg.sender` or implement a more granular access control mechanism. If the functionality is critical, ensure the `BURNER_ROLE` is controlled by a highly secure, multi-signature wallet.


### `M-01` — Upgradeability Risk with Centralized Control  *(Severity: Medium · Status: Unresolved)*

The contract uses the UUPS upgradeability pattern, allowing the contract logic to be changed. The `UPGRADER_ROLE` is initially granted to the `msg.sender` (initializer). While UUPS is a standard pattern, a compromised `UPGRADER_ROLE` holder could upgrade the contract to malicious code, potentially leading to loss of funds, freezing of assets, or other severe consequences (7.7 Upgrades, 7.3 Access Control).

**Recommendation:** Ensure the `UPGRADER_ROLE` is controlled by a robust multi-signature wallet with a high threshold. Consider implementing a timelock for upgrades to provide users with a window to react to proposed changes. Thoroughly audit all proposed upgrade implementations before deployment.


### `I-01` — Constructor `_disableInitializers()` in Implementation  *(Severity: Informational · Status: Resolved)*

The `Nillion` contract's constructor calls `_disableInitializers()`. This is a good security practice for upgradeable contracts, preventing the implementation contract from being initialized directly, which could lead to state corruption if it were accidentally called (7.2 Code Security).

**Recommendation:** No action required; this is a positive security measure.


### `I-02` — Decimals Override  *(Severity: Informational · Status: Resolved)*

The `decimals()` function is explicitly overridden to return 6 instead of the default 18 for ERC-20 tokens. This is a design choice that impacts how the token amount is displayed and handled by interfaces and integrations (7.1 Architecture).

**Recommendation:** Ensure all front-ends, exchanges, and integrations are aware of and correctly handle the 6-decimal precision to prevent display errors or miscalculations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7cf9...2d47`](https://etherscan.io/address/0x7cf9a80db3b29ee8efe3710aadb7b95270572d47) |
| **Network** | Ethereum |
| **Price** | $0.03638 |
| **24h Volume** | $162.3K |
| **Liquidity** | $285.5K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 8mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 304 buys / 264 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xc63eb6794f7b98afa83a350eceb9052401c6da65e2e27d8b3479e12bbc720b91)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nillion-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-28*
