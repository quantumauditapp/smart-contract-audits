---
token: ACU
ticker: ACU
network: base
risk_score: 44
status: medium
date: 2026-08-13
---

# ACU (ACU) — Smart Contract Security Analysis | Base

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/acu-base)

---

## Audit Summary

The AcuOFT contract is an Omnichain Fungible Token (OFT) implementation built on LayerZero V2, inheriting from OpenZeppelin's Ownable. It provides standard token functionalities with cross-chain capabilities. The contract is simple, primarily relying on audited base contracts. Key findings include centralized owner control, non-standard token decimals, and the absence of an emergency pause mechanism.

> **Final Recommendation:** It is recommended to thoroughly document the implications of the 12-decimal precision for all integrators and ensure all frontends and external systems correctly handle this non-standard value. Consider implementing an emergency pause mechanism, potentially controlled by the multisig owner, to provide a safety net for critical situations. Furthermore, ensure the multisig owner address is secured with robust operational procedures, given its significant control over the token's cross-chain functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The AcuOFT contract (7.2 Code Security) is a straightforward implementation of LayerZero's OFT standard, inheriting from well-audited OpenZeppelin Ownable. The code is concise and follows common… |
| **Governance / Economics** | 3/10 | High | The contract's access control (7.3 Access Control) is managed by the `Ownable` pattern, with the owner (also the LayerZero delegate) having significant control over LayerZero configurations and other… |
| **Upgrades** | 7/10 | Low | The AcuOFT contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no direct upgrade safety concerns for this specific contract. Any future changes would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control by Owner/Delegate  *(Severity: High · Status: Unresolved)*

The `_delegate` address provided in the constructor becomes both the `Ownable` owner and the LayerZero delegate. This address has significant administrative control over the OFT contract, including setting LayerZero configurations (e.g., trusted remotes, message libraries, etc.) and other `Ownable` functions. While the prefill indicates a multisig is used, this single entity holds substantial power, making it a critical point of control.

**Recommendation:** Ensure the multisig owner address is secured with the highest level of operational security, including robust key management, multi-factor authentication, and strict governance procedures for executing transactions. Clearly define and communicate the scope of the owner's powers to all stakeholders.


### `M-01` — Non-Standard Decimals  *(Severity: Medium · Status: Unresolved)*

The `decimals()` function is explicitly overridden to return `12`. This deviates from the common ERC-20 standard of 18 decimals. While technically valid, this non-standard precision can lead to misinterpretations, display errors, or incorrect calculations in wallets, exchanges, and other DeFi protocols if they assume 18 decimals by default.

**Recommendation:** Thoroughly document the 12-decimal precision and ensure all integrating systems (frontends, wallets, exchanges, analytics platforms) are aware of and correctly handle this value. Implement clear checks in any off-chain or on-chain integrations to prevent errors due to decimal mismatches.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks an emergency pause mechanism that could halt token transfers or cross-chain operations. In the event of a critical vulnerability in the LayerZero protocol, a major exploit, or other unforeseen circumstances, the absence of such a mechanism could limit the ability to react quickly and protect user funds from further loss.

**Recommendation:** Consider implementing a `Pausable` mechanism (e.g., from OpenZeppelin) controlled by the multisig owner. This would allow the team to temporarily halt operations in emergencies, providing a crucial safety net. Ensure the pause mechanism has clear activation and deactivation policies.


### `I-01` — Reliance on LayerZero Protocol Security  *(Severity: Informational · Status: Unresolved)*

The `AcuOFT` contract is an Omnichain Fungible Token (OFT) and its core functionality, especially cross-chain transfers, is entirely dependent on the security and operational integrity of the LayerZero V2 protocol and its endpoint. Any vulnerabilities, misconfigurations, or operational issues within the LayerZero infrastructure could directly impact the security and functionality of this token.

**Recommendation:** Maintain continuous monitoring of the LayerZero protocol for security announcements, upgrades, and potential vulnerabilities. Ensure the LayerZero endpoint address used is the official and most secure one. Implement robust monitoring for cross-chain transactions.


### `I-02` — No Explicit `_lzEndpoint` Validation in Constructor  *(Severity: Informational · Status: Unresolved)*

The constructor accepts an `_lzEndpoint` address but does not include explicit validation (e.g., checking if it's a known LayerZero endpoint address or if it implements the `ILayerZeroEndpointV2` interface) before passing it to the `OFT` base constructor. While the `OFT` base contract likely handles interactions, a direct check could enhance robustness against misconfiguration.

**Recommendation:** Consider adding a require statement in the constructor to validate the `_lzEndpoint` address, for example, by checking if it's a non-zero address or if it supports the `ILayerZeroEndpointV2` interface using `IERC165` (if applicable to the endpoint contract).

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc5fe...3f0b`](https://basescan.org/address/0xc5fed7c8ccc75d8a72b601a66dffd7a489073f0b) |
| **Network** | Base |
| **Price** | $0.1212 |
| **24h Volume** | $365.0K |
| **Liquidity** | $241.3K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 89.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2445 buys / 2733 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6d76a0f856a2ba951da45da9be399509ad602e6a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/acu-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
