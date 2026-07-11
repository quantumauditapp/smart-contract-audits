---
token: RaveDAO
ticker: RAVE
network: ethereum
risk_score: 98
status: critical
date: 2026-06-29
---

# RaveDAO (RAVE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 98/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ravedao-eth)

---

## Audit Summary

The RaveToken contract is an ERC-20 token implementing LayerZero's Omnichain Fungible Token (OFT) standard, inheriting from OpenZeppelin's Ownable. The contract provides basic ERC-20 functionality, cross-chain transfers via LayerZero, and a burn function. Key strengths include the use of battle-tested OpenZeppelin and LayerZero libraries. Identified risks primarily revolve around centralized control over critical cross-chain configurations and inherent dependencies on the LayerZero protocol.

> **Final Recommendation:** The RaveToken contract is generally well-implemented, leveraging robust external libraries. The primary areas for improvement involve decentralizing critical access control mechanisms and enhancing operational resilience. We recommend considering a multi-signature wallet or a time-locked governance for sensitive LayerZero configurations and implementing a pause mechanism for emergencies. For enhanced security and operational robustness, consider a Premium Deploy option, which includes continuous monitoring and incident response planning.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes well-audited OpenZeppelin and LayerZero libraries, contributing to a solid foundation (7.2 Code Security). The `burn` function is correctly implemented, allowing users to burn th |
| **Governance / Economics** | 1/10 | High | The economic model is straightforward, with `totalSupply` minted to the owner at deployment, which is a common initial distribution strategy (7.4 Economic). The primary governance risk stems from the  |
| **Upgrades** | 4/10 | Medium | The RaveToken contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). This design choice eliminates the complexities and potential risks associated with proxy upgrade patterns. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control Over LayerZero Configurations  *(Severity: Medium · Status: Unresolved)*

The `RaveToken` contract inherits `Ownable` and `OFT`. The `owner` address, set at deployment, has significant control over the `OFT`'s configuration parameters, such as `setTrustedRemote`, `setEnforcedOptions`, and `setDelegate`. This centralization means the owner can unilaterally change critical cross-chain parameters, potentially impacting token transfers or security. This poses a single point of failure and trust assumption.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for critical `OFT` configuration changes to reduce single-point-of-failure risk and enhance decentralization. This would require multiple approvals or a delay before sensitive changes take effect.


### `M-02` — Dependency on LayerZero Protocol  *(Severity: Medium · Status: Unresolved)*

The `RaveToken` contract heavily relies on the LayerZero protocol for its omnichain functionality. Any vulnerabilities, exploits, or operational issues within the LayerZero endpoint, its messaging system, or its security model (e.g., oracles, relayer network) could directly impact the security and functionality of `RaveToken`'s cross-chain transfers. This introduces an external dependency risk.

**Recommendation:** Project teams should closely monitor LayerZero's security updates, audits, and operational status. Implement robust monitoring for LayerZero-related events and potential anomalies. Maintain contingency plans for potential LayerZero service disruptions or security incidents.


### `L-01` — Lack of Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The `RaveToken` contract, being an ERC-20 with cross-chain capabilities, does not include a pause mechanism. In the event of a critical vulnerability, exploit, or emergency (e.g., a LayerZero exploit or a bug in the token logic), there is no way for the owner or a governance body to temporarily halt transfers or cross-chain operations to mitigate damage.

**Recommendation:** Consider integrating a `Pausable` mechanism (e.g., from OpenZeppelin) that allows the owner or a designated role to pause and unpause critical functions like `transfer`, `transferFrom`, `burn`, and potentially `_debit` (for cross-chain sends) in emergencies. This should be carefully designed to avoid centralization of power.


### `I-01` — Initial Total Supply Minted to Owner  *(Severity: Informational · Status: Unresolved)*

In the constructor, the entire `totalSupply` of `RaveToken` is minted directly to the `owner` address. While this is a common pattern for initial token distribution, it means the owner holds 100% of the initial token supply, giving them significant control over the token's immediate liquidity and market dynamics.

**Recommendation:** Ensure transparency regarding the initial token distribution plan. If the intention is for broader distribution, consider implementing a vesting schedule, airdrop mechanism, or liquidity provision strategy to decentralize token holdings post-deployment.


### `I-02` — Use of Floating Pragma Version  *(Severity: Informational · Status: Unresolved)*

The contract uses `pragma solidity ^0.8.28;`. A floating pragma allows the contract to be compiled with any future 0.8.x version. While this can leverage newer compiler features, it introduces the risk of unexpected behavior if a future compiler version introduces breaking changes or new bugs that affect the contract's logic.

**Recommendation:** Pin the Solidity compiler version to a specific, tested version (e.g., `pragma solidity 0.8.28;`) to ensure deterministic compilation and prevent unexpected behavior from future compiler updates. This practice enhances reproducibility and reduces potential risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1720...db97`](https://etherscan.io/address/0x17205fab260a7a6383a81452ce6315a39370db97) |
| **Network** | Ethereum |
| **Price** | $0.4702 |
| **24h Volume** | $678.7K |
| **Liquidity** | $408.0K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 97.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1228 buys / 1122 sells |

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

## Frequently Asked Questions

### Is RaveDAO a scam?

Based on the provided data, RaveDAO exhibits several characteristics commonly associated with high-risk projects. The unrenounced contract ownership, extreme token centralization (97.3% in top 10 holders), and unlocked liquidity are significant red flags that can indicate a heightened potential for malicious actions or severe market manipulation. These factors contribute to its critical risk score of 71/100.

### Is RaveDAO safe to buy?

Investing in RaveDAO carries significant risk, reflected by its critical risk score of 71/100. Key safety concerns include the unrenounced contract ownership, allowing potential future alterations by the deployer, and the highly concentrated token supply that enables substantial market control by a few large holders. Additionally, the lack of locked liquidity means the project is vulnerable to liquidity withdrawals, posing a substantial risk to investor funds.

### Has RaveDAO been audited?

The RaveDAO contract has been verified on Etherscan, which means its code is publicly available and matches the deployed bytecode. However, contract verification is not the same as a professional security audit. An audit involves a thorough review by cybersecurity experts to identify vulnerabilities, and there is no information provided to suggest RaveDAO has undergone such a process.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xca47e80bd01a1f5bcc8cf709d48a5399d533447e03d56f488498dc83c35b5831)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ravedao-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-29*
