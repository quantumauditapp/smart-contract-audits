---
token: HeyAnon
ticker: ANON
network: ethereum
risk_score: 81
status: high
date: 2026-09-12
---

# HeyAnon (ANON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 81/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/heyanon-eth)

---

## Audit Summary

The HeyAnon contract implements an Omnichain Fungible Token (OFT) utilizing LayerZero V2 for cross-chain functionality and OpenZeppelin's Ownable for access control. The audit identified a high degree of centralization of control through the owner/delegate address and a critical dependency on the LayerZero V2 protocol's security. The contract's simplicity and reliance on well-audited libraries are strengths, but these centralized points of control and external dependencies introduce inherent risks.

> **Final Recommendation:** Prioritize the security of the `_delegate` address, ideally by securing it with a robust multisignature wallet and strict operational procedures. Conduct thorough due diligence on the LayerZero V2 protocol and its security posture, understanding that the token's cross-chain functionality is directly tied to its integrity. Consider implementing additional monitoring and alerting for critical LayerZero events or token movements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract `HeyAnon` is a straightforward implementation of an Omnichain Fungible Token (OFT) using LayerZero V2 and OpenZeppelin's `Ownable` for access control (7.1 Architecture). The code is… |
| **Governance / Economics** | 1/10 | High | The economic model is that of a standard ERC-20 token with cross-chain capabilities, relying on the underlying `OFT` implementation. The primary governance and economic risk stems from the highly… |
| **Upgrades** | 6/10 | Medium | The `HeyAnon` contract is deployed as a standard, non-upgradeable implementation (7.7 Upgrades). This design choice eliminates upgrade-specific risks such as proxy storage collisions or incorrect… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — High Centralization of Control  *(Severity: High · Status: Unresolved)*

The `_delegate` address provided in the constructor becomes both the `Ownable` owner and the `OFT` delegate. This grants a single entity extensive control over the token's administrative functions, including LayerZero configurations, pausing, and potentially other critical operations inherited from `OFT`. A compromise of this address would severely impact the protocol's cross-chain functionality and overall integrity (7.3 Access Control, 7.4 Economic).

**Recommendation:** If possible, consider separating the `Ownable` owner role from the `OFT` delegate role, assigning them to different, highly secured entities or multisig wallets. If a single address must hold both roles, ensure it is a robustly secured multisignature wallet with a high threshold and strict operational security protocols.


### `M-01` — Critical Dependency on LayerZero V2 Protocol Security  *(Severity: Medium · Status: Unresolved)*

The `HeyAnon` token's core functionality relies entirely on the security and correct operation of the LayerZero V2 protocol, including its endpoint, message libraries, relayers, and oracles. Any vulnerabilities, misconfigurations, or compromises within the LayerZero infrastructure could directly affect the cross-chain transfer capabilities and overall integrity of the `HeyAnon` token (7.6 External).

**Recommendation:** Maintain continuous monitoring of LayerZero V2 security announcements, audits, and operational status. Implement robust monitoring for cross-chain transactions and LayerZero-specific events related to the `HeyAnon` token. Develop a contingency plan for scenarios where LayerZero V2 experiences significant disruptions or security incidents.


### `L-01` — Reliance on OFT's Pausing Mechanism  *(Severity: Low · Status: Unresolved)*

While the underlying `OFT` contract likely provides pausing mechanisms (e.g., `_pause` function callable by the owner/delegate), the `HeyAnon` contract itself does not implement any additional custom emergency functions or circuit breakers. This means the project relies solely on the inherited `OFT` controls for crisis management, without adding any specific `HeyAnon`-level emergency logic (7.8 Operations).

**Recommendation:** Evaluate if any specific `HeyAnon` business logic (if it were to expand beyond a simple token) would benefit from a dedicated, custom emergency pause or circuit breaker. For the current simple token, ensure the `OFT`'s pausing mechanism is well understood and accessible for rapid response by the owner/delegate.


### `I-01` — Constructor Input Validation  *(Severity: Informational · Status: Unresolved)*

The constructor initializes critical addresses such as `_lzEndpoint` and `_delegate`. While `Ownable` checks for `address(0)` for the owner, explicit validation for `_lzEndpoint` to ensure it's a non-zero address and potentially a known valid LayerZero endpoint, or additional checks for `_delegate` (e.g., not a contract address if it's expected to be an EOA or multisig), could enhance robustness (7.2 Code Security).

**Recommendation:** Consider adding explicit `require` statements in the constructor to validate that `_lzEndpoint` is not `address(0)`. For `_delegate`, while `Ownable` handles `address(0)`, further checks could be added if specific types of addresses (e.g., EOA vs. contract) are expected.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x79bb...e07c`](https://etherscan.io/address/0x79bbf4508b1391af3a0f4b30bb5fc4aa9ab0e07c) |
| **Network** | Ethereum |
| **Price** | $0.4223 |
| **24h Volume** | $369.2K |
| **Liquidity** | $104.7K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 72.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 301 buys / 288 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x20571f2be262ecc5ee12a67627c3c32f07c595b0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/heyanon-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
