---
token: Orderly Network
ticker: ORDER
network: arbitrum
risk_score: 63
status: high
date: 2026-08-16
---

# Orderly Network (ORDER) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 63/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orderly-network-arb)

---

## Audit Summary

The OrderOFT contract serves as an Omnichain Fungible Token (OFT) for the Orderly Network, leveraging LayerZero V2 for cross-chain functionality. The contract utilizes standard OpenZeppelin upgradeable patterns (UUPS, Ownable, Pausable) and LayerZero's OApp framework. While the architecture is robust, the high degree of centralized control by the owner (a multisig) over critical functions such as upgrades, pausing, and LayerZero peer/delegate configuration introduces significant operational and security risks. Proper management of the owner's private keys and careful execution of administrative functions are paramount.

> **Final Recommendation:** Strengthen the security posture by ensuring the multisig owner's operational security is of the highest standard, including robust key management and multi-factor authentication for signers. Implement comprehensive monitoring for all administrative actions, especially those related to LayerZero peer configuration and contract upgrades. Consider a time-lock mechanism for critical administrative functions to provide a window for community review and intervention, further decentralizing control and reducing immediate impact of a compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements LayerZero's OFTUpgradeable standard, providing robust cross-chain token transfer capabilities (7.1 Architecture). It correctly uses OpenZeppelin's `SafeERC20` for token… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a high degree of centralized control, with the owner (a 2/3 multisig) possessing exclusive rights to critical administrative functions such as pausing the contract, upgrading… |
| **Upgrades** | 2/10 | High | The contract correctly implements the UUPS proxy pattern, allowing for future upgrades of its logic (7.7 Upgrades). The `_authorizeUpgrade` function is restricted to the `onlyOwner` modifier… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 75.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The contract grants extensive administrative privileges to a single owner address (a 2/3 multisig). This owner can pause the contract, initiate upgrades, set LayerZero peers, and configure the LayerZero delegate. While a multisig provides some resilience against a single point of failure, a compromise of the multisig's keys would allow an attacker to take full control of the OFT's operations, potentially leading to asset loss or system disruption.

**Recommendation:** Ensure the multisig owner's operational security is paramount. Consider implementing a time-lock for critical administrative functions (e.g., upgrades, `setPeer`, `setDelegate`, `pause`) to introduce a delay between the transaction initiation and execution. This delay provides a window for detection and potential intervention, reducing the immediate impact of a compromised owner.


### `M-01` — Critical Initialization Parameters  *(Severity: Medium · Status: Unresolved)*

The `initialize` function takes `_lzEndpoint` and `_delegate` as critical parameters. The `_delegate` address is used to set both the contract's `Ownable` owner and the LayerZero endpoint's delegate. An incorrect or malicious address provided during initialization could lead to loss of ownership, misconfiguration of the LayerZero delegate, or unintended control over the contract.

**Recommendation:** Thoroughly verify all initialization parameters before deployment and execution. Implement a robust deployment process that includes multiple reviews of the initialization arguments. For production deployments, consider a multi-step initialization or a 'dry run' on a testnet to confirm correct setup.


### `M-02` — Reliance on LayerZero Endpoint Security  *(Severity: Medium · Status: Unresolved)*

The contract heavily relies on the security and correct functioning of the external LayerZero V2 endpoint. All cross-chain messaging, fee quoting, and token transfers (for LZ tokens) are routed through this endpoint. Any vulnerability, exploit, or misconfiguration within the LayerZero protocol or its endpoint could directly impact the security and functionality of the OrderOFT contract, potentially leading to frozen funds or unauthorized operations.

**Recommendation:** Maintain continuous monitoring of LayerZero's security announcements and updates. Establish a robust incident response plan for scenarios involving LayerZero protocol vulnerabilities. While direct control over the LayerZero endpoint is not possible, understanding its security posture is crucial for the OFT's overall security.


### `L-01` — Potential for Peer Misconfiguration  *(Severity: Low · Status: Unresolved)*

The `setPeer` and `setPeers` functions, callable only by the owner, are responsible for configuring valid cross-chain communication paths by mapping `eid` (endpoint ID) to `peer` (remote OApp address). An incorrect peer configuration could lead to legitimate cross-chain messages being sent to unintended or malicious contracts, or prevent valid messages from being processed, disrupting cross-chain functionality.

**Recommendation:** Implement strict internal procedures for verifying LayerZero peer addresses before setting them. Consider adding an event listener or monitoring system to alert on any changes to peer configurations, allowing for quick detection of unauthorized or erroneous updates.


### `I-01` — Gas Optimization for `setPeers` Function  *(Severity: Informational · Status: Unresolved)*

The `setPeers` function iterates through arrays (`_eids` and `_peers`) to set multiple peers in a single transaction. While functional, processing very large arrays in a single transaction could lead to high gas costs, potentially making the function expensive or even unusable if the array size exceeds block gas limits.

**Recommendation:** For practical purposes, ensure that the expected number of peers to be set in a single call to `setPeers` remains within reasonable gas limits. If a very large number of peers needs to be configured, consider batching the operations into smaller transactions or optimizing the loop if possible, though the current implementation is standard for this pattern.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4e20...97b8`](https://arbiscan.io/address/0x4e200fe2f3efb977d5fd9c430a41531fb04d97b8) |
| **Network** | Arbitrum |
| **Price** | $0.02926 |
| **24h Volume** | $38.4K |
| **Liquidity** | $141.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 88.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 282 buys / 331 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xb49eae16e45faebaa406e57c93263a5fcbc0c8d3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orderly-network-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
