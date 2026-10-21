---
token: OPEN
ticker: OPEN
network: bsc
risk_score: 52
status: medium
date: 2026-09-03
---

# OPEN (OPEN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/open-bsc)

---

## Audit Summary

The OmnichainOpen contract is a straightforward implementation of a LayerZero Omnichain Fungible Token (OFT), inheriting from LayerZero's OFT and OpenZeppelin's Ownable. The contract's custom logic is minimal, primarily focused on constructor initialization. It leverages well-audited external libraries, contributing to a strong technical foundation. The ownership is managed by a 3/5 multisig, enhancing access control security. The primary risks are inherent dependencies on the LayerZero protocol and the immutability of the contract.

> **Final Recommendation:** The OmnichainOpen contract demonstrates a solid foundation due to its reliance on audited libraries and a multisig ownership structure. It is crucial to maintain vigilance over the security of the underlying LayerZero protocol, as the contract's functionality is entirely dependent on it. For future iterations, consider the implications of immutability and potential strategies for upgradeability if long-term flexibility is desired.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is a straightforward implementation of LayerZero's OFT standard, inheriting from `OFT` and `Ownable`. It leverages battle-tested OpenZeppelin and LayerZero libraries, contributing to… |
| **Governance / Economics** | 1/10 | High | The contract employs OpenZeppelin's `Ownable` for access control, with ownership initially assigned to a `_delegate` address, which is a 3/5 multisig (7.3 Access Control, 7.5 Governance). This… |
| **Upgrades** | 7/10 | Low | The `OmnichainOpen` contract is deployed as a standard, non-proxy implementation, meaning it is immutable post-deployment (7.7 Upgrades). This design choice provides certainty regarding the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 1 Informational_

### `L-01` — Centralized Administrative Control  *(Severity: Low · Status: Unresolved)*

The contract utilizes OpenZeppelin's `Ownable` pattern, granting a single owner (a 3/5 multisig) significant administrative control over critical OFT functions, such as setting trusted remotes, managing fees, and pausing operations (7.3 Access Control, 7.5 Governance). While a multisig mitigates single points of failure, it still represents a centralized control point whose compromise could lead to significant issues.

**Recommendation:** Ensure the multisig wallet holding ownership is secured with best practices, including strong key management, multi-factor authentication, and strict operational procedures. Regularly review the multisig signers and their permissions. Consider implementing time-locks for critical administrative actions to provide a window for community review or emergency response.


### `L-02` — Immutability and Upgradeability  *(Severity: Low · Status: Unresolved)*

The `OmnichainOpen` contract is deployed as a standard, non-proxy contract, making it immutable post-deployment (7.7 Upgrades). This design choice provides certainty regarding the contract's code but means that any future bug fixes, feature enhancements, or protocol upgrades would require deploying an entirely new contract and migrating assets. This process can be complex, costly, and disruptive to users (7.1 Architecture, 7.8 Operations).

**Recommendation:** Acknowledge the implications of immutability. If future flexibility or upgradeability is a critical requirement, consider migrating to an upgradeable proxy pattern (e.g., UUPS) in a future version. For the current immutable contract, ensure thorough testing and auditing before deployment to minimize the need for future changes.


### `I-01` — Dependency on LayerZero Protocol  *(Severity: Informational · Status: Unresolved)*

The `OmnichainOpen` contract is built upon LayerZero's Omnichain Fungible Token (OFT) standard. Its security, functionality, and cross-chain capabilities are entirely dependent on the robustness and operational integrity of the LayerZero protocol and its `OFT` implementation. Any vulnerabilities, exploits, or operational issues within the LayerZero ecosystem could directly impact the assets managed by this contract (7.6 External).

**Recommendation:** While this is an inherent architectural choice, it is crucial for the protocol to continuously monitor LayerZero's security advisories, audits, and community updates. Implement robust monitoring for LayerZero's endpoint and messaging channels to detect anomalies promptly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa227...9447`](https://bscscan.com/address/0xa227cc36938f0c9e09ce0e64dfab226cad739447) |
| **Network** | BNB Chain |
| **Price** | $0.1188 |
| **24h Volume** | $177.6K |
| **Liquidity** | $430.3K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2214 buys / 2054 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x419f8539c423d66dc42bd80d6f0bdd6fd4c21dce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/open-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
