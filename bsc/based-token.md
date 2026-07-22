---
token: Based Token
ticker: BASED
network: bsc
risk_score: 67
status: high
date: 2026-07-22
---

# Based Token (BASED) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/based-token-bsc)

---

## Audit Summary

This audit focused on the provided Solidity interfaces for LayerZero V2 components, including `ILayerZeroEndpointV2`, `ILayerZeroReceiver`, and related manager interfaces. It's important to note that only interface definitions were provided, not the actual implementation logic. Therefore, the audit assesses potential risks and architectural considerations for any contract implementing these interfaces, rather than specific vulnerabilities in a deployed contract. The prefill indicated a contract named 'BasedOFT' at the given address, but the provided source code consists solely of LayerZero V2 interfaces, suggesting a mismatch in the audit scope definition. The findings highlight critical access control considerations, reentrancy risks for implementers, and the inherent complexity of cross-chain messaging.

> **Final Recommendation:** Implementers of LayerZero V2 interfaces must prioritize robust access control for all sensitive management functions, ensuring only authorized entities can make critical configuration changes. Thorough reentrancy checks and secure coding practices are paramount for `lzReceive` implementations, especially when handling value transfers or external calls. Additionally, careful consideration should be given to the economic implications of fee calculations and potential oracle dependencies. Comprehensive testing, including cross-chain scenarios and edge cases, is essential before deployment. Finally, integrating emergency pause mechanisms can provide a crucial safety net for operational risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The LayerZero V2 interfaces define a complex cross-chain messaging architecture (7.1 Architecture) with distinct roles for endpoints, message libraries, and receivers. The design emphasizes… |
| **Governance / Economics** | 2/10 | High | The interfaces expose several critical functions that, in an implementation, would require strong access control and governance (7.3 Access Control, 7.5 Governance). Functions like `setLzToken`… |
| **Upgrades** | 5/10 | Medium | As only interfaces were provided, direct upgradeability concerns (7.7 Upgrades) for these specific contracts are not applicable. However, the LayerZero V2 protocol itself is designed to be extensible… |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Critical Access Control for Core Management Functions  *(Severity: High · Status: Unresolved)*

The `ILayerZeroEndpointV2` and `IMessageLibManager` interfaces expose highly sensitive functions such as `setLzToken`, `setDelegate`, `registerLibrary`, `setDefaultSendLibrary`, `setReceiveLibrary`, and `setConfig`. In an implementation, these functions control fundamental aspects of the LayerZero protocol, including token configurations, delegate permissions, and the registration/selection of message libraries. Inadequate access control (7.3 Access Control) for these functions could allow unauthorized entities to compromise the protocol, manipulate fees, or disrupt cross-chain messaging.

**Recommendation:** Implement robust, multi-layered access control mechanisms (e.g., Ownable2Step, multi-signature wallets, or governance contracts) for all critical management functions. Ensure that only trusted and authorized addresses can invoke these functions. Regularly review and audit the access control logic.


### `M-01` — Reentrancy Risk in `lzReceive` Implementations  *(Severity: Medium · Status: Unresolved)*

The `lzReceive` function, present in both `ILayerZeroEndpointV2` and `ILayerZeroReceiver`, is designed to handle incoming cross-chain messages. If an implementing contract performs external calls (e.g., token transfers, interactions with other contracts) based on the received message before updating its internal state, it could be vulnerable to reentrancy attacks (7.2 Code Security). An attacker could craft a malicious message to re-enter the `lzReceive` function or other sensitive functions, leading to unintended state changes or fund drains.

**Recommendation:** Implement the Checks-Effects-Interactions pattern within `lzReceive` and any functions it calls. Ensure all state changes are completed before any external calls are made. Consider using reentrancy guards (e.g., OpenZeppelin's `ReentrancyGuard`) if complex interactions are unavoidable.


### `M-02` — Economic Attack Vectors via Fee Calculation  *(Severity: Medium · Status: Unresolved)*

The `quote` function in `ILayerZeroEndpointV2` returns `MessagingFee` which includes `nativeFee` and `lzTokenFee`. If the underlying implementation's fee calculation relies on external price feeds, manipulable on-chain data, or parameters that can be influenced by malicious actors, it could lead to economic exploits (7.4 Economic). Attackers might be able to artificially inflate or deflate fees, making cross-chain operations uneconomical or allowing for fund draining if fees are paid in a manipulable asset.

**Recommendation:** Ensure that the fee calculation mechanism in the implementation is robust, transparent, and resistant to manipulation. If external oracles are used, integrate reputable, decentralized oracle solutions (e.g., Chainlink) with proper validation and fallback mechanisms. Regularly monitor fee parameters and their impact on the protocol's economics.


### `L-01` — Lack of Emergency Mechanisms in Interfaces  *(Severity: Low · Status: Unresolved)*

The provided interfaces do not include functions for emergency pausing or circuit breakers. While interfaces define functionality, a robust implementation of a critical cross-chain protocol component (7.8 Operations) should incorporate mechanisms to halt or restrict operations in the event of a severe vulnerability, exploit, or unforeseen issue. Without such mechanisms, a critical bug could lead to irreversible damage before a fix can be deployed.

**Recommendation:** Implement emergency pause functionality (e.g., using OpenZeppelin's `Pausable` contract) in any concrete contract that implements these LayerZero V2 interfaces. This mechanism should be controlled by a trusted multi-signature wallet or a robust governance system.


### `I-01` — Incomplete Audit Scope: Interfaces Only  *(Severity: Informational · Status: Unresolved)*

The audit was conducted solely on Solidity interface definitions for LayerZero V2 components. No concrete implementation logic was provided or analyzed. This significantly limits the scope of the audit, as actual vulnerabilities often reside in the implementation details rather than the interface definitions themselves. The prefill also indicated a different contract name ('BasedOFT') than the provided source code (LayerZero V2 interfaces), leading to a discrepancy in the audit target.

**Recommendation:** For a comprehensive security assessment, provide the full source code of the deployed or intended implementation contracts, including all dependencies. Ensure the provided source code matches the intended audit target and deployed addresses.


### `I-02` — Inherent Complexity of Cross-Chain Messaging  *(Severity: Informational · Status: Unresolved)*

The LayerZero V2 protocol, as evidenced by its extensive interfaces (`ILayerZeroEndpointV2`, `IMessageLibManager`, `IMessagingChannel`, etc.), represents a highly complex system for secure cross-chain communication (7.1 Architecture). This inherent complexity increases the surface area for potential misconfigurations, integration errors, or subtle logical flaws in implementations. Securely building on or integrating with such a system requires deep technical understanding and meticulous attention to detail.

**Recommendation:** Teams implementing or integrating with LayerZero V2 should invest in comprehensive documentation, internal code reviews, and external audits. Adopt a phased deployment strategy with extensive testing on testnets. Maintain a strong understanding of the LayerZero V2 protocol's specifications and best practices.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1d28...8e4d`](https://bscscan.com/address/0x1d28d989f9e3ccb8b15d0cec601734514f958e4d) |
| **Network** | BNB Chain |
| **Price** | $0.08531 |
| **24h Volume** | $265.3K |
| **Liquidity** | $212.4K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 3mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 850 buys / 826 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x07b7556ede0f9a6a7d155a78bc0573f531001a57)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/based-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
