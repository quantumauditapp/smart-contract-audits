---
token: Kava
ticker: KAVA
network: bsc
risk_score: 44
status: medium
date: 2026-09-14
---

# Kava (KAVA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kava-bsc)

---

## Audit Summary

The KavaOFT contract is a minimal wrapper around LayerZero's Omnichain Fungible Token (OFT) standard, inheriting from `OFT` and OpenZeppelin's `Ownable`. It facilitates cross-chain token transfers via the LayerZero v2 protocol. The contract itself is simple and well-structured, primarily relying on the security and functionality of the underlying LayerZero libraries. Key security considerations revolve around the extensive control granted to the contract owner (a multisig) over LayerZero configurations and the inherent dependency on the LayerZero protocol's security.

> **Final Recommendation:** Prioritize the secure management of the owner's multisig keys, as this entity holds significant control over critical LayerZero configurations. Implement robust operational procedures for any administrative actions, including multi-party review and time-locks where appropriate, to prevent unauthorized or erroneous changes. Thoroughly review and understand the implications of all LayerZero configuration parameters before deployment and during any subsequent updates to ensure the integrity and security of cross-chain token transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The KavaOFT contract exhibits high code quality, being a straightforward implementation that primarily delegates logic to the audited LayerZero OFT library (7.2 Code Security). The architecture is… |
| **Governance / Economics** | 3/10 | High | The contract owner, specified as a multisig, holds extensive administrative control over critical LayerZero configurations (7.5 Governance). This includes setting trusted remote addresses, minimum… |
| **Upgrades** | 7/10 | Low | The KavaOFT contract itself is not designed as an upgradeable proxy (7.7 Upgrades). Its implementation is immutable once deployed. This simplifies its security profile by removing upgrade-related… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner over LayerZero Configurations  *(Severity: High · Status: Unresolved)*

The `_delegate` address, which becomes the `Ownable` owner, has extensive control over the LayerZero OFT's operational parameters. This includes the ability to call functions like `setTrustedRemoteAddress`, `setMinDstGas`, `setPrecrime`, `setFeeManager`, and `setDelegate` (from `ILayerZeroEndpointV2`). Misuse or compromise of this owner address could lead to funds being misrouted, stuck, or subject to excessive fees, impacting the integrity and economic security of cross-chain transfers. While the prefill indicates the owner is a multisig, the concentration of power remains a significant risk factor (7.3 Access Control, 7.4 Economic, 7.8 Operations).

**Recommendation:** Ensure the owner's multisig is secured with robust key management practices, including strong operational security, geographical distribution of signers, and regular audits. Consider implementing a timelock for critical administrative actions to provide a window for detection and mitigation of malicious or erroneous changes. All configuration changes should undergo thorough review and testing.


### `M-01` — Heavy Reliance on LayerZero Protocol Security  *(Severity: Medium · Status: Unresolved)*

The KavaOFT contract is a thin wrapper around the LayerZero OFT library and directly interacts with the LayerZero v2 Endpoint. Its security and functionality are entirely dependent on the correctness and security of these underlying LayerZero components. Any vulnerabilities, bugs, or design flaws within the LayerZero protocol itself (e.g., in `OFT.sol` or `ILayerZeroEndpointV2.sol`) could directly impact the KavaOFT contract and potentially lead to loss of funds or operational failures (7.6 External).

**Recommendation:** While direct auditing of LayerZero's core contracts is outside the scope of this specific contract audit, it is crucial for the project team to stay informed about LayerZero's security posture, including any audits, bug bounties, or reported vulnerabilities. Maintain a strategy for responding to potential LayerZero-level incidents, such as pausing functionality if possible or communicating risks to users.


### `L-01` — Immutable LayerZero Endpoint Address  *(Severity: Low · Status: Unresolved)*

The `_lzEndpoint` address is set during the contract's construction and cannot be modified thereafter. This design choice ensures that the contract always interacts with a specific, known LayerZero endpoint (7.1 Architecture). However, it also means that if the LayerZero protocol were to deprecate the current endpoint, or if a critical vulnerability in the endpoint required an immediate replacement, the KavaOFT contract would need to be redeployed to point to a new endpoint (7.8 Operations).

**Recommendation:** Acknowledge this design trade-off. For future versions or similar contracts, consider if a mechanism for the owner to update the LayerZero endpoint address (e.g., via a controlled `setLzEndpoint` function with a timelock) might be beneficial, weighing the added complexity and attack surface against the flexibility gained. For the current contract, ensure the chosen endpoint is stable and well-supported.


### `I-01` — Dual Role of Constructor `_delegate` Parameter  *(Severity: Informational · Status: Unresolved)*

The `_delegate` parameter in the `KavaOFT` constructor serves two distinct roles: it is passed to the `OFT` base contract as its delegate and also becomes the `Ownable` owner of the `KavaOFT` contract. This dual assignment means the same address controls both the LayerZero-specific delegate functions and the general contract ownership (7.1 Architecture, 7.3 Access Control).

**Recommendation:** Ensure that deployers and administrators are fully aware of this dual role. While not a vulnerability, clarity on the responsibilities and powers associated with the `_delegate` address is important for proper operational security and understanding of the contract's control structure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9baf...ad79`](https://bscscan.com/address/0x9bafc8d4b487cebff201721702507a3e2c67ad79) |
| **Network** | BNB Chain |
| **Price** | $0.06348 |
| **24h Volume** | $1.28M |
| **Liquidity** | $436.7K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4700 buys / 4968 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x99e1a43e738b026a2cd4359409594debab61b48d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kava-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
