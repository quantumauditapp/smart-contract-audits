---
token: Jito Staked SOL
ticker: JITOSOL
network: base
risk_score: 62
status: high
date: 2026-07-22
---

# Jito Staked SOL (JITOSOL) — Smart Contract Security Analysis | Base

> **Risk Score: 62/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jito-staked-sol-base)

---

## Audit Summary

The CrossChainERC20 contract implements a standard ERC20 token with specialized cross-chain functionality, allowing a designated bridge contract to mint and burn tokens. The contract leverages Solady for optimized ERC20 functionality and includes the Initializable pattern. Key findings highlight the significant centralization risk associated with the bridge contract and a design choice that limits upgradeability flexibility if used with a proxy.

> **Final Recommendation:** Prioritize the security and operational robustness of the `_BRIDGE` contract, as it represents the primary point of control and risk for the token supply. Implement robust monitoring, multi-signature controls, and emergency response procedures for the bridge to mitigate the high centralization risk. If upgradeability is a future requirement, consider refactoring the `_BRIDGE` variable to be a storage variable managed by the `initialize` function, allowing it to be updated via proxy upgrades. If the current immutable design is intentional, ensure all stakeholders understand the implications of a permanently fixed bridge address.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract is well-structured, inheriting from Solady's optimized ERC20 and Initializable contracts. It uses Solidity 0.8.28, benefiting from built-in overflow/underflow protection. Access control… |
| **Governance / Economics** | 1/10 | High | The economic model of this token is highly centralized, as a single `_BRIDGE` address holds exclusive privileges to mint and burn tokens. This design introduces a significant single point of failure… |
| **Upgrades** | 3/10 | High | The contract incorporates the `Initializable` pattern and correctly calls `_disableInitializers()` in its constructor, indicating an intent for use as an upgradeable implementation. However, the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Centralization Risk of Bridge Contract  *(Severity: High · Status: Unresolved)*

The `CrossChainERC20` contract grants exclusive minting and burning privileges to a single `_BRIDGE` address. This design creates a significant centralization risk, as the security and integrity of the entire token supply are dependent on the security of this single bridge contract. A compromise of the `_BRIDGE` contract could lead to unauthorized minting, burning, or manipulation of the token supply, resulting in severe economic damage to the protocol and its users. This is an inherent design choice for cross-chain tokens but represents a critical operational and economic risk (7.3 Access Control, 7.4 Economic, 7.8 Operations).

**Recommendation:** Implement robust security measures for the `_BRIDGE` contract, including multi-signature control, time-locks for critical operations, and comprehensive monitoring. Consider a decentralized bridge architecture or a mechanism for community governance over the bridge in the long term. Establish clear emergency procedures for potential bridge exploits.


### `M-01` — Incompatible Design for Upgradeability (Immutable Bridge in Initializable Contract)  *(Severity: Medium · Status: Unresolved)*

The contract imports `Initializable` and uses the `initializer` modifier, indicating an intent for upgradeability via a proxy pattern. However, the `_BRIDGE` address is declared as `immutable` and set in the constructor. In an upgradeable proxy setup, the constructor of the implementation contract runs only once upon its initial deployment, not when the proxy is initialized or upgraded. This means the `_BRIDGE` address is permanently fixed for this specific implementation contract and cannot be changed through proxy upgrades. This design choice restricts the flexibility of the system, as the critical bridge contract itself cannot be upgraded or replaced without deploying an entirely new pro…

**Recommendation:** If upgradeability of the bridge address is desired, refactor `_BRIDGE` to be a regular storage variable. It should then be set during the `initialize` function call, allowing it to be updated via proxy upgrades. If the immutable nature of the bridge is an intentional design constraint, ensure this limitation is clearly documented and understood by all stakeholders.


### `I-01` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract lacks a mechanism to pause critical operations (e.g., minting, burning, or even transfers) in the event of an emergency, such as a detected vulnerability in the bridge contract or a major exploit. While the `onlyBridge` modifier centralizes control, a broader pause functionality can be crucial for damage control (7.8 Operations).

**Recommendation:** Consider implementing a pause mechanism, potentially controlled by a multi-signature wallet or a governance contract. This would allow the protocol to temporarily halt operations to mitigate damage during an incident or to perform necessary upgrades/fixes.


### `I-02` — `_remoteToken` Interpretation is External  *(Severity: Informational · Status: Unresolved)*

The `_remoteToken` variable, a `bytes32` identifier, is intended to represent the corresponding token on a remote chain. Its meaning, uniqueness, and enforcement are entirely external to this contract and depend on the logic implemented within the `_BRIDGE` contract and the remote chain's system. The `CrossChainERC20` contract itself does not validate or interpret this identifier beyond ensuring it's not zero (7.6 External).

**Recommendation:** Ensure that the `_BRIDGE` contract has robust logic for managing and validating `_remoteToken` identifiers to prevent collisions or misinterpretations across chains. Clear documentation should be provided for how `_remoteToken` values are generated and used within the broader cross-chain ecosystem.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x97be...34de`](https://basescan.org/address/0x97be14dd8f994a5364573bc035d85309e7cb34de) |
| **Network** | Base |
| **Price** | $100.3700 |
| **24h Volume** | $315.2K |
| **Liquidity** | $11.03M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 684 buys / 806 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe2b8c33ae97658cead06afd47c7f3857e5851871)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jito-staked-sol-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
