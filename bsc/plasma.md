---
token: Plasma
ticker: XPL
network: bsc
risk_score: 71
status: critical
date: 2026-08-13
---

# Plasma (XPL) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 71/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/plasma-bsc)

---

## Audit Summary

The PlasmaOFT contract is an Omnichain Fungible Token (OFT) built on LayerZero, inheriting from OpenZeppelin's Ownable. The contract itself is minimal, primarily serving as a wrapper for LayerZero's OFT functionality. Key strengths include the use of well-audited OpenZeppelin components and a robust multisig ownership structure. The primary risks stem from its reliance on the LayerZero protocol's security and the inherent complexities of cross-chain bridge operations.

> **Final Recommendation:** It is recommended to conduct thorough due diligence on the LayerZero protocol's security and operational practices, as the PlasmaOFT contract's safety is intrinsically linked to it. Implement robust monitoring for cross-chain transactions and LayerZero endpoint configurations. Consider integrating an emergency pause mechanism at a higher level if the protocol design allows, to provide a circuit breaker in extreme circumstances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The PlasmaOFT contract is a straightforward implementation of an Omnichain Fungible Token (OFT) using LayerZero's OFT library and OpenZeppelin's Ownable. The code is minimal and leverages… |
| **Governance / Economics** | 1/10 | High | The contract's ownership is managed by a robust 4-of-6 multisig, significantly mitigating risks associated with single points of failure or compromised private keys (7.3 Access Control, 7.5… |
| **Upgrades** | 6/10 | Medium | The PlasmaOFT contract is deployed as a standard, non-upgradeable implementation (7.7 Upgrades). This eliminates upgrade-specific risks such as proxy misconfigurations or logic contract… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 93.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Cross-Chain Bridge Security Risk  *(Severity: High · Status: Unresolved)*

The contract's core functionality relies on the LayerZero protocol for cross-chain token transfers. Bridge protocols are complex and have historically been targets for significant exploits, leading to substantial asset losses. Any vulnerability in the LayerZero endpoint, message passing, or associated relayers could directly impact the security of PlasmaOFT tokens across chains.

**Recommendation:** Conduct continuous monitoring of LayerZero protocol security announcements and audits. Implement robust off-chain monitoring for unusual cross-chain activity. Diversify bridge reliance if possible in future iterations.


### `M-01` — Dependency on LayerZero Protocol  *(Severity: Medium · Status: Unresolved)*

The PlasmaOFT contract is a wrapper around LayerZero's OFT implementation. Its security and functionality are entirely dependent on the correctness and security of the LayerZero libraries and the underlying LayerZero endpoint. While LayerZero is a prominent solution, any undiscovered vulnerability or operational issue within their extensive codebase could directly affect this contract.

**Recommendation:** Maintain a deep understanding of the LayerZero protocol's architecture and security model. Regularly review LayerZero's official documentation, security updates, and audit reports. Ensure the `_lzEndpoint` address is correctly configured and points to the official, audited LayerZero endpoint.


### `M-02` — Lack of Emergency Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The PlasmaOFT contract, as a standard ERC-20/OFT implementation, does not include an emergency pause or circuit breaker mechanism. In the event of a critical vulnerability, exploit, or market manipulation, there is no immediate way for the owner to halt token transfers or cross-chain operations to prevent further loss of funds.

**Recommendation:** Evaluate the feasibility of integrating a pause mechanism, potentially at a higher protocol level or through a governance-controlled wrapper, to provide an emergency stop functionality. This would allow the owner (multisig) to temporarily freeze operations in critical situations, subject to predefined conditions and governance approval.


### `L-01` — Configuration Risk for LayerZero Parameters  *(Severity: Low · Status: Unresolved)*

The constructor takes `_lzEndpoint` and `_delegate` as parameters, which are critical for LayerZero operations and ownership. Incorrectly setting these parameters during deployment could lead to the contract being inoperable, funds being sent to the wrong endpoint, or control being assigned to an unintended address.

**Recommendation:** Implement a rigorous deployment checklist and multi-party verification process for all constructor arguments, especially `_lzEndpoint` and `_delegate`. Ensure these addresses are thoroughly vetted and correspond to the intended, audited components.


### `I-01` — Centralized Owner Privileges (Mitigated by Multisig)  *(Severity: Informational · Status: Unresolved)*

The contract inherits `Ownable`, granting the owner (the `_delegate` address) significant administrative control. While the provided prefill indicates this owner is a 4-of-6 multisig, centralizing control, even with a multisig, means that a compromise of the multisig signers could lead to unauthorized actions, such as reconfiguring LayerZero parameters or potentially impacting token functionality.

**Recommendation:** Maintain strict security practices for all multisig signers, including hardware wallets, strong authentication, and secure key management. Regularly review the multisig's operational procedures and ensure a clear understanding of the owner's capabilities and responsibilities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x405f...26b0`](https://bscscan.com/address/0x405fbc9004d857903bfd6b3357792d71a50726b0) |
| **Network** | BNB Chain |
| **Price** | $0.07492 |
| **24h Volume** | $229.9K |
| **Liquidity** | $347.3K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 90.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2083 buys / 2456 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x50203df8efcddba9755c886f086b9b2d537a15f9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/plasma-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
