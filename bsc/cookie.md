---
token: Cookie
ticker: COOKIE
network: bsc
risk_score: 53
status: high
date: 2026-08-12
---

# Cookie (COOKIE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 53/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cookie-bsc)

---

## Audit Summary

The OmnichainCookie contract is an Omnichain Fungible Token (OFT) built on LayerZero, inheriting from OpenZeppelin's Ownable and LayerZero's OFT. The contract's core logic is minimal, primarily relying on well-audited external libraries. Key risks identified relate to the centralized administrative control via the owner/delegate address and the inherent dependencies on the LayerZero protocol for cross-chain functionality. The contract is not upgradeable, which implies immutability but also inflexibility for future changes.

> **Final Recommendation:** It is crucial to ensure the security of the `_delegate` address, as it holds extensive administrative control; consider implementing a time-lock for critical administrative actions. Establish robust monitoring for LayerZero endpoint health and cross-chain transaction integrity. Evaluate the necessity of an emergency pause mechanism for the token, either directly in the contract or through LayerZero's capabilities, to mitigate risks during unforeseen events. Given the non-upgradeable nature, thorough testing and a clear long-term strategy are paramount.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin (Ownable, ERC20) and LayerZero (OFT) libraries, contributing to a strong technical foundation (7.1 Architecture, 7.2 Code Security). The custom logic… |
| **Governance / Economics** | 3/10 | High | The `_delegate` address, which also serves as the `Ownable` owner, holds significant administrative power over the token's cross-chain operations and general contract management (7.5 Governance).… |
| **Upgrades** | 7/10 | Low | The OmnichainCookie contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, which can be a security strength by preventing unexpected… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 94.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Administrative Control via Delegate Address  *(Severity: High · Status: Unresolved)*

The `_delegate` address provided in the constructor serves a dual role: it becomes the `Ownable` owner and the LayerZero OFT delegate. This grants a single entity (or multisig) comprehensive control over both the standard `Ownable` functions (e.g., `transferOwnership`) and all LayerZero-specific administrative functions (e.g., `setTrustedRemote`, `setFeeManager`, `setMinDstGas`). A compromise of this address would lead to full control over the token's cross-chain operations and ownership, posing a significant centralization risk (7.3 Access Control, 7.5 Governance).

**Recommendation:** While the current owner is a multisig, consider implementing a time-lock mechanism for critical administrative functions (e.g., `transferOwnership`, `setTrustedRemote`) to provide a delay for review and potential intervention. Regularly audit and review the security posture of the multisig wallet controlling this address.


### `M-01` — Reliance on LayerZero Endpoint Security and Liveness  *(Severity: Medium · Status: Unresolved)*

The core functionality of the OmnichainCookie token, specifically its cross-chain transfers, is entirely dependent on the LayerZero protocol and its `_lzEndpoint`. Any vulnerabilities, operational failures, or compromises within the LayerZero endpoint, its relayers, or oracles could directly impact the ability to transfer tokens across chains, potentially leading to frozen funds or incorrect state (7.6 External, 7.4 Economic).

**Recommendation:** Implement robust monitoring for the LayerZero endpoint's health, transaction finality, and any reported vulnerabilities. Establish an emergency response plan for potential LayerZero-related incidents. Consider diversifying cross-chain solutions in the future if the protocol's design allows.


### `M-02` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The OmnichainCookie contract does not include a direct, contract-level mechanism to pause token transfers or cross-chain operations. In the event of a critical vulnerability, an exploit, or a major issue with the LayerZero bridge, the absence of a pause function could prevent immediate mitigation, potentially leading to significant loss of funds or protocol disruption (7.8 Operations).

**Recommendation:** Evaluate the feasibility and necessity of integrating a pause mechanism (e.g., OpenZeppelin's `Pausable` module) into the contract. If implemented, ensure the pause functionality is controlled by a secure, multi-signature wallet with a clear activation policy and emergency procedures.


### `L-01` — Constructor Delegate Parameter Importance  *(Severity: Low · Status: Unresolved)*

The `_delegate` address passed to the constructor is critical as it initializes both the `OFT` delegate and the `Ownable` owner. While the prefill indicates this is a multisig, any misconfiguration or error in providing this address during deployment would result in an irreversible single point of failure or an inaccessible contract (7.3 Access Control, 7.8 Operations).

**Recommendation:** Ensure rigorous pre-deployment checks and verification of the `_delegate` address, confirming it corresponds to a securely managed multi-signature wallet. Implement a robust deployment checklist and consider a dry-run deployment on a testnet to validate all constructor parameters.


### `I-01` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

The OmnichainCookie contract is implemented directly and does not utilize a proxy pattern, meaning it is not upgradeable. This design choice ensures immutability and predictability of the contract's logic (7.7 Upgrades). However, it also implies that any future bug fixes, security patches, or desired feature enhancements would necessitate deploying an entirely new contract and migrating existing token holders, which can be a complex and resource-intensive process.

**Recommendation:** Acknowledge the implications of non-upgradeability. Ensure the current contract logic is thoroughly audited and robust. Plan for potential future migrations by considering mechanisms to facilitate token transfers to a new contract if necessary, or accept the immutability as a core feature.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc004...265f`](https://bscscan.com/address/0xc0041ef357b183448b235a8ea73ce4e4ec8c265f) |
| **Network** | BNB Chain |
| **Price** | $0.01217 |
| **24h Volume** | $877.2K |
| **Liquidity** | $243.7K |
| **Volume / Liquidity** | 3.6× |
| **Token Age** | 2y |
| **Top-10 Holders** | 64.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4198 buys / 4108 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd4fb9d253739c5db6aad90ad2409757d224ccc0c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cookie-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
