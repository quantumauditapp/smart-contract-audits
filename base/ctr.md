---
token: CTR
ticker: CTR
network: base
risk_score: 48
status: high
date: 2026-08-11
---

# CTR (CTR) — Smart Contract Security Analysis | Base

> **Risk Score: 48/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ctr-base)

---

## Audit Summary

The Citrea Token OFT contract is a minimal implementation of a LayerZero Omnichain Fungible Token (OFT), inheriting from LayerZero's OFT base contract and OpenZeppelin's Ownable. The contract facilitates cross-chain token transfers via the LayerZero v2 protocol. The audit focused on the contract's specific implementation, its interaction with LayerZero, and its access control mechanisms. Key findings include centralized control over cross-chain configurations and inherent reliance on the security of the LayerZero protocol.

> **Final Recommendation:** Ensure the multisig controlling the owner address is robustly secured with strong operational procedures and key management. Regularly monitor the LayerZero protocol for security updates and announcements, as the contract's security is directly tied to its external dependencies. Consider implementing additional monitoring for critical owner actions and cross-chain transfer events to enhance operational oversight and detect potential anomalies promptly.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The CitreaTokenOFT contract is minimal, primarily inheriting from LayerZero's OFT and OpenZeppelin's Ownable. The code is straightforward and uses a recent Solidity version (0.8.33), benefiting from… |
| **Governance / Economics** | 2/10 | High | The contract employs an `Ownable` pattern, with the owner being a 3/5 multisig, which enhances security compared to a single EOA. This owner has significant control over critical cross-chain… |
| **Upgrades** | 7/10 | Low | The CitreaTokenOFT contract is not designed as an upgradeable proxy, meaning its logic is immutable once deployed. This simplifies the architecture by avoiding upgrade-related complexities and risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Cross-Chain Functionality  *(Severity: High · Status: Unresolved)*

The `owner` (a 3/5 multisig) has extensive control over the LayerZero OFT configuration, including setting trusted remotes, minimum destination gas, and potentially pausing cross-chain transfers via the inherited OFT functions. A compromise of the multisig could lead to redirection of cross-chain funds, denial of service for cross-chain operations, or manipulation of fees (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Ensure the multisig controlling the owner address adheres to the highest security standards, including robust key management, secure signing procedures, and regular audits of its members. Implement strict internal controls and monitoring for all owner-privileged functions. Consider a time-lock for critical configuration changes if feasible for the protocol's operational needs.


### `M-01` — Reliance on External LayerZero Protocol Security  *(Severity: Medium · Status: Unresolved)*

The `CitreaTokenOFT` contract is a wrapper around the LayerZero OFT implementation. Its security is fundamentally tied to the security and integrity of the LayerZero v2 protocol and its smart contracts (e.g., `OFT.sol`, `ILayerZeroEndpointV2.sol`). Any vulnerabilities or exploits within the LayerZero endpoint, message libraries, or OFT base contract could directly affect the safety of funds managed by this token (7.6 External).

**Recommendation:** Stay informed about LayerZero protocol updates, security audits, and any reported vulnerabilities. Implement robust monitoring for LayerZero endpoint activity and cross-chain transactions involving the token. While direct mitigation within this contract is limited, awareness and rapid response capabilities are crucial.


### `L-01` — Lack of Explicit Event Emission for Critical Owner Actions  *(Severity: Low · Status: Unresolved)*

While the inherited `OFT` base contract likely emits events for its critical functions (e.g., `setPeer`, `setMinDstGas`), the `CitreaTokenOFT` itself does not add any custom events for its constructor or any potential future owner-controlled functions. Explicit events for all critical state changes improve transparency and monitoring for off-chain systems (7.2 Code Security, 7.8 Operations).

**Recommendation:** For any future custom owner-controlled functions added to `CitreaTokenOFT`, ensure that appropriate events are emitted to log critical state changes. Review the `OFT` base contract's events to confirm comprehensive coverage for cross-chain configuration changes.


### `I-01` — Immutability of LayerZero Endpoint Address  *(Severity: Informational · Status: Unresolved)*

The LayerZero endpoint address (`_lzEndpoint`) is set in the constructor and cannot be changed after deployment. While this ensures stability and prevents malicious modification, it means that if the LayerZero endpoint itself needs to be upgraded or replaced (e.g., due to a critical vulnerability or protocol evolution), the `CitreaTokenOFT` contract would need to be redeployed, requiring users to migrate their tokens (7.1 Architecture, 7.7 Upgrades).

**Recommendation:** This is an architectural design choice. Acknowledge the implications of an immutable endpoint. If future flexibility is desired, consider an upgradeable proxy pattern for the token or a mechanism to update the endpoint address, though this adds complexity and potential attack surface.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1103...57f7`](https://basescan.org/address/0x11030f79109269d796fd0fb956d6244e502757f7) |
| **Network** | Base |
| **Price** | $0.008141 |
| **24h Volume** | $542.7K |
| **Liquidity** | $453.8K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 80.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3785 buys / 3881 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0ab02e160f0df68dc049b012c514857306960eae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ctr-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
