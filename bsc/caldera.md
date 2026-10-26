---
token: Caldera
ticker: ERA
network: bsc
risk_score: 46
status: medium
date: 2026-08-31
---

# Caldera (ERA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/caldera-bsc)

---

## Audit Summary

The MetaERC20Spoke contract serves as an ERC20 token implementation for a cross-chain messaging system, enabling token transfers across different domains. It utilizes OpenZeppelin's upgradeable contracts and AccessControl for robust foundational security. While the contract demonstrates good practices in code quality and upgradeability, a significant logic flaw was identified concerning the `mintedBalance` update during emergency reissuance, which could impact token utility and economic consistency. Centralized control by the `ADMIN_ROLE`, though managed by a multisig, also presents a notable risk.

> **Final Recommendation:** It is crucial to address the `mintedBalance` inconsistency in the `EMERGENCY_REISSUE` function to ensure the token's economic model remains sound and users can reliably transfer reissued tokens cross-chain. Clarify the intended behavior of `mintedBalance` and implement the necessary update logic. Additionally, while the `ADMIN_ROLE` is multisig-controlled, consider implementing time-locks or further decentralization for highly sensitive administrative actions to mitigate centralization risks and enhance overall protocol resilience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 and AccessControl, ensuring robust foundational components and automatic overflow/underflow checks (7.2 Code Security). It also employs clear… |
| **Governance / Economics** | 1/10 | High | The protocol benefits from a multisig `ADMIN_ROLE` for critical operations, enhancing operational security for sensitive functions like `EMERGENCY_REISSUE` and `setSecurityThreshold` (7.3 Access… |
| **Upgrades** | 4/10 | Medium | The contract is designed for upgradeability using the TransparentUpgradeableProxy pattern, incorporating OpenZeppelin's `initializer` modifier and `__gap` storage variables to ensure future… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 3-of-5 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control by `ADMIN_ROLE`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ADMIN_ROLE` possesses significant control over the contract's critical functions, including `EMERGENCY_REISSUE` (which can mint tokens) and `setSecurityThreshold` (which affects cross-chain routing logic). While the prefill indicates the admin is a multisig, the concentration of such power in a single role, even if controlled by a multisig, presents a centralization risk. A compromise of the multisig could lead to unauthorized minting or manipulation of cross-chain transfer conditions. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Implement additional safeguards or time-locks for highly sensitive administrative actions, especially those involving token minting or significant changes to economic parameters. Consider a separate role or a more granular access control mechanism if specific admin actions can be delegated or require different levels of approval. Ensure robust operational security for the multisig.


### `M-02` — Inconsistent `mintedBalance` Update in `EMERGENCY_REISSUE`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `EMERGENCY_REISSUE` function allows an admin to mint tokens to a recipient based on a previous transfer record. However, it calls `_mint` without updating the `mintedBalance` state variable. The `mintedBalance` variable is crucial for tracking the total supply of tokens that can be burned for cross-chain transfers via `_preDispatchHook`. If tokens are reissued without incrementing `mintedBalance`, it can lead to two issues: 1) Users holding tokens issued via `EMERGENCY_REISSUE` might be unable to transfer them cross-chain if `mintedBalance` becomes insufficient, leading to `MintedBalanceUnderflow` reverts. 2) The `

**Recommendation:** Clarify the intended behavior of `mintedBalance` in relation to `EMERGENCY_REISSUE`. If `EMERGENCY_REISSUE` is meant to reintroduce tokens that were effectively 'lost' from the bridged supply and should be eligible for cross-chain transfers, `mintedBalance` should be incremented by `localAmount` after `_mint`. If these tokens are not intended to be eligible for cross-chain burning, this should be explicitly documented and understood as a design choice with its implications for user experience.


### `L-01` — Potential for Front-Running `setSecurityThreshold`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setSecurityThreshold` function, callable by the `ADMIN_ROLE`, updates a critical parameter that influences the routing of cross-chain transfers. While an admin function, a malicious actor could potentially front-run a transaction that changes this threshold if they can predict the new value and exploit the brief window between transaction submission and inclusion. For example, if the threshold is being significantly lowered, an attacker might attempt to initiate a large transfer that would otherwise be routed via the hub, hoping it gets processed directly before the new threshold takes effect. (7.4 Economic)

**Recommendation:** While the impact is limited due to it being an admin function, consider implementing a timelock for changes to critical parameters like `securityThreshold`. This would provide users and other systems with a grace period to react to upcoming changes, mitigating front-running risks.


### `I-01` — Reliance on External Metalayer Protocol Security  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MetaERC20Spoke` contract is an integral part of the broader Hyperlane Metalayer cross-chain messaging system. Its security and functionality are heavily dependent on the correct and secure operation of the `IMetalayerRouter` and the underlying Metalayer protocol. Any vulnerabilities or exploits within the Metalayer infrastructure could directly impact the security and integrity of tokens managed by this `MetaERC20Spoke` contract. (7.6 External)

**Recommendation:** Ensure thorough audits and continuous monitoring of the entire Metalayer protocol, including all interconnected contracts and off-chain components. Maintain clear documentation of the assumptions and trust model regarding the Metalayer infrastructure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0031...6bce`](https://bscscan.com/address/0x00312400303d02c323295f6e8b7309bc30fb6bce) |
| **Network** | BNB Chain |
| **Price** | $0.05868 |
| **24h Volume** | $11.3K |
| **Liquidity** | $53.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5493 buys / 5398 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x55d0119a43a0e2c54fd6eb1f17e3b883eedba602)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/caldera-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
