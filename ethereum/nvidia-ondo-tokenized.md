---
token: NVIDIA (Ondo Tokenized)
ticker: NVDAON
network: ethereum
risk_score: 100
status: critical
date: 2026-09-25
---

# NVIDIA (Ondo Tokenized) (NVDAON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nvidia-ondo-tokenized-eth)

---

## Audit Summary

The GMToken contract, deployed as an upgradeable BeaconProxy, implements an ERC-20 token with extensive access control for minting, burning, and configuration. While leveraging well-audited OpenZeppelin libraries for upgradeability and access control, the contract exhibits a high degree of centralization. Critical findings include highly privileged roles that can unilaterally control token supply, burn user funds, and manipulate core token functionality by changing external dependencies. Upgrade safety also presents a high risk due to a missing `__gap` variable in the primary contract.

> **Final Recommendation:** It is strongly recommended to decentralize critical roles or implement robust multi-signature governance for highly privileged functions such as minting, burning, and setting external contract addresses. This will mitigate the significant centralization risks identified. Additionally, ensure the `GMToken` contract includes a `__gap` array to prevent storage collisions during future upgrades, adhering to best practices for upgradeable contracts. Thoroughly audit and secure all external dependencies, especially the compliance and pause manager contracts, as their integrity is paramount to the token's functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The GMToken contract utilizes OpenZeppelin's upgradeable ERC-20 and AccessControl libraries, which generally contribute to robust code security (7.2 Code Security). The `_beforeTokenTransfer` hook… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a highly centralized governance and economic model (7.5 Governance, 7.4 Economic). The `DEFAULT_ADMIN_ROLE` has ultimate control over all other roles, including `MINTER_ROLE`… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the BeaconProxy pattern and OpenZeppelin's `Initializable` base contracts, which is a standard and generally secure approach (7.1 Architecture). The… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.0% |
| **Top-3 Unlocked** | 78.4% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Centralized Control Over Critical Token Functions  *(Severity: Critical · Status: Unresolved)*

The `GMToken` contract grants highly privileged roles (`MINTER_ROLE`, `BURNER_ROLE`, `CONFIGURER_ROLE`) to potentially single entities, controlled by the `DEFAULT_ADMIN_ROLE`. The `MINTER_ROLE` can mint an arbitrary amount of tokens, leading to uncontrolled inflation. The `BURNER_ROLE` can burn tokens from *any* address, allowing for arbitrary fund confiscation. The `CONFIGURER_ROLE` can change the addresses of the `compliance` and `tokenPauseManager` contracts to arbitrary, potentially malicious, contracts, enabling a full denial of service or unauthorized transfer restrictions. This centralization poses a critical risk of economic manipulation, fund loss, or protocol shutdown if these rol…

**Recommendation:** Implement robust multi-signature (e.g., Gnosis Safe) control for all critical roles (`DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, `BURNER_ROLE`, `CONFIGURER_ROLE`). Consider introducing time-locks for sensitive operations like changing external contract addresses or granting/revoking critical roles. Clearly document the responsibilities and operational procedures for each role.


### `H-01` — Missing `__gap` Variable in `GMToken` for Upgrade Safety  *(Severity: High · Status: Unresolved)*

The `GMToken` contract, despite inheriting from OpenZeppelin's upgradeable contracts which include `__gap` arrays, does not declare its own `__gap` array at the end of its storage variables. While inherited `__gap`s protect the base contracts, any new state variables introduced directly into `GMToken` in a future upgrade could potentially overwrite storage slots of existing variables in inherited base contracts if not carefully placed, leading to storage collisions and unexpected behavior or loss of data.

**Recommendation:** Add a `uint256[50] private __gap;` (or appropriate size) at the very end of the `GMToken` contract's state variables to ensure forward compatibility and prevent storage collisions during future upgrades. This is a standard practice for upgradeable contracts.


### `H-02` — Critical Reliance on External Compliance and Pause Managers  *(Severity: High · Status: Unresolved)*

The `GMToken`'s core transfer functionality is critically dependent on the `OndoComplianceGMClientUpgradeable` and `TokenPauseManagerClientUpgradeable` contracts, which are external dependencies. The `_beforeTokenTransfer` hook calls `_checkTokenIsPaused()` and `_checkIsCompliant()` from these external contracts. A bug, compromise, or malicious configuration of these external contracts (e.g., by the `CONFIGURER_ROLE`) could lead to a complete denial of service for token transfers, arbitrary transfer restrictions, or other unintended behavior, severely impacting the token's utility and security.

**Recommendation:** Implement robust monitoring and auditing procedures for the external compliance and token pause manager contracts. Ensure these external contracts are themselves highly secure, immutable where possible, or controlled by strong multi-signature governance. Consider adding circuit breakers or emergency mechanisms to disable reliance on these external contracts in case of compromise or malfunction, if feasible.


### `M-01` — High Centralization of `DEFAULT_ADMIN_ROLE`  *(Severity: Medium · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` is granted to `msg.sender` during initialization and has the power to grant and revoke all other roles, including `MINTER_ROLE`, `BURNER_ROLE`, and `CONFIGURER_ROLE`. This centralizes significant administrative power in a single entity or a small group, creating a single point of failure. A compromise of the `DEFAULT_ADMIN_ROLE`'s private key could lead to a complete takeover of the token's functionality.

**Recommendation:** Assign the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet (e.g., Gnosis Safe) from the outset. Consider implementing a timelock for sensitive administrative actions, such as changing role administrators or granting/revoking critical roles, to provide a window for intervention in case of a malicious or erroneous action.


### `I-01` — Ambiguous `msg.sender` Compliance Check in `_beforeTokenTransfer`  *(Severity: Informational · Status: Unresolved)*

The `_beforeTokenTransfer` function includes a compliance check for `msg.sender` only if `from != msg.sender && to != msg.sender`. This implies `msg.sender` is an intermediary (e.g., an approved operator or a proxy contract). While not a direct vulnerability, this specific condition might lead to confusion or unexpected behavior in complex transfer scenarios, especially if the intent for `msg.sender`'s compliance in such cases is not explicitly defined or universally understood.

**Recommendation:** Clarify the intended behavior and implications of the `msg.sender` compliance check in the documentation. If the intent is to always check the actual `from` and `to` addresses, and `msg.sender`'s compliance is only relevant in specific proxy/operator patterns, ensure this logic is robust and well-tested across all expected use cases.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2d1f...bdee`](https://etherscan.io/address/0x2d1f7226bd1f780af6b9a49dcc0ae00e8df4bdee) |
| **Network** | Ethereum |
| **Price** | $225.2600 |
| **24h Volume** | $695.8K |
| **Liquidity** | $154.4K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 18d |
| **Top-10 Holders** | 75.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1039 buys / 855 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa9a6651fba74df1aab94065ffaabe750d6ed835b94a9e28925ec79beec2d5f73)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nvidia-ondo-tokenized-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
