---
token: Cluster Protocol
ticker: CP
network: base
risk_score: 60
status: medium
date: 2026-09-03
---

# Cluster Protocol (CP) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cluster-protocol-base)

---

## Audit Summary

The CPToken contract implements an ERC20 token with additional features like ERC20Permit and a custom authorization mechanism for transfers and receives. It utilizes OpenZeppelin's AccessControl for role-based permissions, including MINTER_ROLE and BURNER_ROLE, and enforces a MAX_SUPPLY. The contract demonstrates good adherence to established standards and includes robust checks for authorization validity and signature verification. However, the centralized nature of the DEFAULT_ADMIN_ROLE poses a significant single point of failure, and the reliance on block.timestamp for authorization validity introduces a minor risk of miner manipulation. An unused _ccipAdmin variable also suggests potential for incomplete features or lack of clarity.

> **Final Recommendation:** To enhance the security and decentralization of the CPToken protocol, it is strongly recommended to implement a robust multi-signature wallet or a decentralized autonomous organization (DAO) to control the DEFAULT_ADMIN_ROLE. This measure will distribute administrative power, mitigate the risk of a single point of failure, and improve the overall trust model. Additionally, ensure that the validAfter and validBefore parameters for signed authorizations are set with sufficiently wide time windows to minimize the impact of potential miner timestamp manipulation. Finally, clarify and document the intended purpose of the _ccipAdmin variable to ensure transparency and prepare for any future integrations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The CPToken contract is built upon well-audited OpenZeppelin libraries for ERC20, ERC20Permit, and AccessControl, contributing to a solid technical foundation (7.2 Code Security). The custom… |
| **Governance / Economics** | 2/10 | High | The contract establishes a clear role-based access control system with DEFAULT_ADMIN_ROLE, MINTER_ROLE, and BURNER_ROLE, ensuring controlled token supply management and privileged operations (7.3… |
| **Upgrades** | 3/10 | High | The CPToken contract is implemented as a standard, non-upgradeable ERC20 token. This design choice simplifies the deployment and reduces the complexity associated with upgrade mechanisms, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 1 Informational_

### `M-01` — Potential for Miner Manipulation of Timestamps in Authorization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_requireValidAuthorization` function, used by `transferWithAuthorization` and `receiveWithAuthorization`, relies on `block.timestamp` to enforce `validAfter` and `validBefore` conditions. While `block.timestamp` is a standard practice, it can be manipulated by miners within a certain range (up to 900 seconds on Ethereum). If the `validAfter`/`validBefore` window is very narrow (e.g., a few blocks), a miner could potentially front-run or delay a transaction to cause it to fail due to timestamp expiry or prematurity, even if the user intended it to be valid. This could lead to user frustration or failed transactions

**Recommendation:** Ensure that the `validAfter` and `validBefore` windows are sufficiently wide (e.g., several hours or days) to mitigate the impact of miner timestamp manipulation. Users should be made aware of this characteristic when generating signed authorizations.


### `M-02` — Centralized Control of Critical Roles  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds significant power within the CPToken contract. This role is responsible for granting `MINTER_ROLE` and `BURNER_ROLE`, and for setting the `_ccipAdmin` address. If this role is controlled by a single External Owned Account (EOA), it represents a single point of failure. A compromised or malicious administrator could mint tokens up to `MAX_SUPPLY`, burn tokens from any account that has granted an allowance to the `BURNER_ROLE` holder, and potentially influence cross-chain operations via the `_ccipAdmin` (if it's used externally). This centralization poses a high risk to the protocol's secur

**Recommendation:** Implement a multi-signature wallet or a robust governance mechanism (e.g., DAO) to control the `DEFAULT_ADMIN_ROLE`. This will distribute administrative power and reduce the risk associated with a single point of failure.


### `I-01` — Unused `_ccipAdmin` Variable  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_ccipAdmin` state variable is declared, initialized in the constructor, and has a setter function (`setCCIPAdmin`) restricted to `DEFAULT_ADMIN_ROLE`, along with a getter. However, no other logic within the `CPToken` contract directly utilizes this variable. This suggests it might be a placeholder for future functionality or integration with an external CCIP system. Without its intended use, it represents an incomplete feature or dead code within the current contract scope, potentially leading to confusion or an unnecessary attack surface if its external purpose is not well-defined (7.1 Architecture, 7.2 Code Secu

**Recommendation:** Clearly document the intended purpose and usage of the `_ccipAdmin` variable. If it's for future integration, ensure that the external system's security is thoroughly reviewed once implemented. If it's not intended for use, consider removing it to reduce contract complexity and improve clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x001a...3f77`](https://basescan.org/address/0x001aad84c21a5cd4d696c56d44866e9703c43f77) |
| **Network** | Base |
| **Price** | $0.03762 |
| **24h Volume** | $6.12M |
| **Liquidity** | $923.0K |
| **Volume / Liquidity** | 6.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 88.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9690 buys / 8141 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x78fa9fb7a76c8ea204754a8d4ff301aa29935e8e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cluster-protocol-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
