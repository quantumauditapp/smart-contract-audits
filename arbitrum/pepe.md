---
token: Pepe
ticker: PEPE
network: arbitrum
risk_score: 41
status: medium
date: 2026-09-22
---

# Pepe (PEPE) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepe-arb)

---

## Audit Summary

The PepeToken contract is an Omnichain Fungible Token (OFT) built on LayerZero, inheriting from OFTWithFee and LzApp. It enables cross-chain token transfers. The contract leverages the LayerZero protocol for its core messaging and security. While the architecture is standard for LayerZero applications and benefits from a multisig owner, significant control over critical bridge parameters remains centralized. The contract's security is highly dependent on the LayerZero protocol itself and the correct configuration of trusted remotes. The full source code for the inherited OFTWithFee contract was not provided for a comprehensive review of token-specific logic.

> **Final Recommendation:** It is crucial to ensure that the multisig owner's keys are secured with robust operational procedures and that the multisig threshold is appropriate for the level of control it holds. Regular audits of the LayerZero protocol and its endpoint are recommended, as the contract's security is inherently tied to this external dependency. Consider implementing an emergency pause mechanism for token transfers within the OFTWithFee contract to provide a rapid response capability in case of unforeseen vulnerabilities or exploits.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract leverages the well-audited LayerZero `LzApp` framework, providing robust cross-chain messaging capabilities with built-in security features like `trustedRemoteLookup` for source… |
| **Governance / Economics** | 6/10 | Medium | The ownership is managed by a multisig (5/8), which enhances security by requiring multiple approvals for critical operations like setting trusted remotes or LayerZero configurations (7.5… |
| **Upgrades** | 4/10 | Medium | The contract is not designed to be upgradeable, which eliminates the risks associated with proxy patterns, such as upgradeability bugs or malicious upgrade implementations (7.7 Upgrades). This… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 23.0% |
| **Top-3 Unlocked** | 48.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control Over Critical LayerZero Parameters  *(Severity: High · Status: Unresolved)*

The `onlyOwner` modifier protects critical functions such as `setTrustedRemote`, `setTrustedRemoteAddress`, `setMinDstGas`, `setPrecrime`, and LayerZero configuration settings. While the owner is a multisig (5/8), this still represents a significant centralization of power. A compromised owner key (or enough keys in the multisig) could misconfigure the bridge, leading to funds being sent to incorrect addresses, denial of service, or even spoofing of messages from untrusted sources if `trustedRemoteLookup` is set maliciously. This directly impacts 7.3 Access Control, 7.6 External, and 7.8 Operations.

**Recommendation:** Ensure the multisig owner's operational security is of the highest standard. Consider exploring decentralized governance mechanisms for critical parameter changes in the future, or implement time-locks for highly sensitive operations to provide a window for community review or emergency intervention.


### `M-01` — Dependency on LayerZero Protocol Security  *(Severity: Medium · Status: Unresolved)*

The `PepeToken` contract relies entirely on the security and correct functioning of the LayerZero protocol and its endpoint. Any vulnerabilities or exploits within the LayerZero infrastructure itself (e.g., issues with message delivery, endpoint security, or oracle mechanisms used by LayerZero) could directly impact the security and integrity of the `PepeToken` and its cross-chain transfers. This is an inherent external risk (7.6 External).

**Recommendation:** Monitor LayerZero security announcements and audits closely. Maintain a robust incident response plan that accounts for potential LayerZero-level vulnerabilities. While this is an external dependency, understanding its risks is crucial for the overall security posture.


### `L-01` — Lack of Emergency Pause/Circuit Breaker for Token Transfers  *(Severity: Low · Status: Unresolved)*

While `LzApp` has a `precrime` address and `forceResumeReceive` for LayerZero messaging, there isn't a direct mechanism within the `PepeToken` or `OFTWithFee` (as far as visible) to pause or halt token transfers or cross-chain operations in an emergency (e.g., if a major vulnerability is discovered in the token logic or LayerZero). This could lead to continued exploitation during an incident, impacting 7.2 Code Security and 7.8 Operations.

**Recommendation:** Consider implementing a pause mechanism (e.g., using OpenZeppelin's `Pausable` contract) within the `OFTWithFee` contract that can halt token transfers and cross-chain sends. This would provide a critical circuit breaker for emergency situations, controlled by the multisig owner.


### `I-01` — Incomplete OFTWithFee Implementation for Audit  *(Severity: Informational · Status: Unresolved)*

The provided code snippet for `PepeToken` imports `OFTWithFee` but does not include its source. This prevents a full security analysis of the token's core logic, including its fee mechanism, token transfer functions, and how it implements `_blockingLzReceive`. Potential vulnerabilities related to token handling, fee calculation, or reentrancy in `OFTWithFee` cannot be assessed. This impacts 7.1 Architecture, 7.2 Code Security, and 7.4 Economic.

**Recommendation:** For a comprehensive audit, provide the full source code of all inherited contracts, especially `OFTWithFee`, to allow for a complete security assessment of the token's core functionality.


### `I-02` — Immutable LayerZero Endpoint Address  *(Severity: Informational · Status: Unresolved)*

The `lzEndpoint` address is set as `immutable` in the constructor. While this is standard practice for LayerZero applications, it means the endpoint address cannot be changed post-deployment. If LayerZero were to upgrade its endpoint contract or if a critical vulnerability required a new endpoint deployment, the `PepeToken` contract would need to be redeployed to point to the new address, incurring significant operational overhead and requiring token migration. This impacts 7.1 Architecture and 7.8 Operations.

**Recommendation:** Acknowledge this design constraint. While not a direct vulnerability, it's important to understand the implications for future upgrades or changes to the LayerZero infrastructure. Plan for potential token migration scenarios in the long term.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x25d8...bb00`](https://arbiscan.io/address/0x25d887ce7a35172c62febfd67a1856f20faebb00) |
| **Network** | Arbitrum |
| **Price** | $0.00000499 |
| **24h Volume** | $40.4K |
| **Liquidity** | $47.7K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3y |
| **Top-10 Holders** | 22.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 166 buys / 121 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x1944ac04bd9fed9a2bcdb38b70c35949c864ec35)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepe-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
