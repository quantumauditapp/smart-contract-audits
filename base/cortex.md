---
token: Cortex
ticker: CX
network: base
risk_score: 77
status: high
date: 2026-09-17
---

# Cortex (CX) — Smart Contract Security Analysis | Base

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cortex-base)

---

## Audit Summary

The Cortex (CX) token contract is an ERC-20 token with interchain capabilities, built upon OpenZeppelin standards and custom interchain application logic. The contract exhibits a robust technical foundation, leveraging audited OpenZeppelin libraries and Solidity 0.8.24 for built-in overflow/underflow protection. However, the design incorporates significant centralized control over token supply and transfer mechanisms, managed by specific roles. Furthermore, its interchain functionality introduces dependencies on external clients and requires careful operational management of transaction fees. While no critical vulnerabilities were identified, the high degree of centralized power and external dependencies warrant careful consideration.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement a robust multi-signature wallet for managing the `GOVERNANCE_ROLE` and `MINTER_ROLE` keys, ideally with a high threshold of signers. Comprehensive monitoring should be in place for all administrative actions, especially those related to token supply and transfer controls. Additionally, thorough due diligence on the security and operational reliability of the external interchain client is crucial, as the protocol's interchain functionality directly depends on it.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation (7.2 Code Security) benefits from using Solidity 0.8.24, which includes default overflow/underflow checks, and extensive reliance on battle-tested OpenZeppelin contracts… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) and governance structure (7.5 Governance) are highly centralized. The `GOVERNANCE_ROLE` has extensive control, including the ability to toggle an… |
| **Upgrades** | 3/10 | High | The provided contract code (7.7 Upgrades) does not implement any explicit proxy or upgradeability patterns. Therefore, the contract is assumed to be non-upgradeable, which eliminates upgrade-specific… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Token Supply and Transfers  *(Severity: High · Status: Unresolved)*

The `GOVERNANCE_ROLE` possesses significant power, including the ability to `toggleAllowList`, `enableTransfers` (which can halt all transfers for non-allowlisted users), and `burnAllocation` from any account. The `MINTER_ROLE` can `mint` an unlimited supply of tokens. This high degree of centralization (7.3 Access Control, 7.5 Governance) means that a single compromised key or malicious actor holding these roles could lead to severe economic manipulation, including arbitrary token burning, unlimited inflation, or a complete denial of service for token transfers (7.4 Economic).

**Recommendation:** Implement a robust multi-signature wallet for the `GOVERNANCE_ROLE` and `MINTER_ROLE` with a high threshold of required signers. Consider implementing time-locks for critical administrative actions to provide a window for community review or emergency intervention. Clearly document the responsibilities and operational procedures for these roles.


### `M-01` — Operational Risk for Interchain Messaging Fees  *(Severity: Medium · Status: Unresolved)*

The `_sendInterchainMessage` function requires the contract to hold sufficient native tokens (e.g., ETH on Ethereum, MATIC on Polygon) to cover the `messageFee` for outgoing interchain transactions. If the contract's native token balance falls below the required fee, interchain messages cannot be sent, leading to a denial of service for interchain functionality (7.8 Operations). This requires continuous operational oversight to ensure the contract is adequately funded.

**Recommendation:** Establish a clear operational procedure for monitoring and topping up the contract's native token balance. Consider implementing a mechanism for authorized parties to deposit native tokens into the contract specifically for interchain fees, or integrate with a treasury management system. Implement alerts for low native token balances.


### `M-02` — Dependency on External Interchain Client Security  *(Severity: Medium · Status: Unresolved)*

The `AbstractICApp` contract, and by extension `CX`, relies heavily on an external `IInterchainClientV1` for all interchain communication, including sending and receiving messages, and calculating fees. The security and integrity of this external client are paramount (7.6 External). Any vulnerability, compromise, or malicious behavior within the `IInterchainClientV1` implementation could directly impact the `CX` token's interchain functionality, potentially leading to loss of funds, incorrect message routing, or a complete halt of interchain operations.

**Recommendation:** Conduct thorough due diligence on the `IInterchainClientV1` contract, including reviewing its audit reports, security practices, and operational history. Implement robust monitoring for all interactions with the interchain client. Consider a mechanism to update or replace the interchain client in case of a critical vulnerability or compromise, if the architecture allows.


### `L-01` — Lack of Granular Pause/Unpause for Interchain App  *(Severity: Low · Status: Unresolved)*

While the `_transfersEnabled` flag provides a mechanism to control token transfers, there isn't a separate, explicit pause/unpause mechanism specifically for the interchain application functionality (e.g., `appReceive`, `_sendInterchainMessage`). In an emergency related to the interchain client or network, a more granular control to temporarily halt interchain operations without affecting local token transfers might be beneficial (7.8 Operations).

**Recommendation:** Consider adding a separate `_interchainEnabled` flag or a similar pausing mechanism specifically for interchain operations, controlled by the `GOVERNANCE_ROLE`. This would allow for more targeted emergency responses without impacting the core ERC-20 transfer functionality.


### `I-01` — Complex Inheritance Structure  *(Severity: Informational · Status: Unresolved)*

The `CX` contract inherits from multiple OpenZeppelin contracts (`ERC20Burnable`, `ERC20Permit`, `ERC20Votes`) and custom base contracts (`CXEvents`, `InterchainToken`, `AbstractICApp`). This complex inheritance hierarchy (7.1 Architecture) increases the overall complexity of the codebase and the potential for subtle interaction bugs or unexpected behavior, despite the robustness of OpenZeppelin libraries.

**Recommendation:** Ensure comprehensive unit and integration tests cover all inherited functionalities and custom overrides, especially focusing on interactions between different base contracts. Maintain clear documentation of the inheritance hierarchy and function override logic to aid future development and auditing efforts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...6033`](https://basescan.org/address/0x000000000000012def132e61759048be5b5c6033) |
| **Network** | Base |
| **Price** | $0.03334 |
| **24h Volume** | $1.86M |
| **Liquidity** | $385.3K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 101.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2334 buys / 2332 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x9249f441005947831eaaf9135b319ad97bcd6bdf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cortex-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-17*
