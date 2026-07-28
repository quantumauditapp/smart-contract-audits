---
token: LIGHT
ticker: LIGHT
network: bsc
risk_score: 40
status: medium
date: 2026-07-26
---

# LIGHT (LIGHT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/light-bsc)

---

## Audit Summary

This audit was conducted on a truncated Solidity code snippet, primarily consisting of standard libraries and LayerZero interfaces. A comprehensive security assessment of the core `LightOFT` contract logic, including token minting, burning, and cross-chain transfer mechanisms, could not be performed due to the unavailability of the full source code. The visible components utilize well-audited OpenZeppelin contracts and LayerZero's `AddressCast` library. The contract is owned by a 2/3 multisig, enhancing access control. However, the inherent reliance on the LayerZero protocol introduces external dependencies.

> **Final Recommendation:** It is strongly recommended to conduct a full security audit once the complete source code for the `LightOFT` contract is available, focusing on its core token logic, cross-chain transfer mechanisms, and administrative functions. Ensure comprehensive unit and integration tests cover all critical paths, especially those involving LayerZero interactions. Implement robust monitoring for all cross-chain transactions and administrative actions to detect anomalies promptly.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The provided code snippet includes standard OpenZeppelin interfaces (ERC-20, ERC-165) and the LayerZero `AddressCast` library, which appears to handle address conversions correctly with appropriate… |
| **Governance / Economics** | 4/10 | Medium | The contract ownership is managed by a 2/3 multisig (7.5 Governance), which is a robust access control mechanism, reducing single points of failure for administrative actions. Economically (7.4… |
| **Upgrades** | 7/10 | Low | The contract is not deployed as an upgradeable proxy (`is_proxy: false`), which eliminates risks associated with upgrade mechanisms (7.7 Upgrades), such as proxy initialization errors or storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — Incomplete Contract Source for Comprehensive Audit  *(Severity: Medium · Status: Unresolved)*

The provided source code is truncated, preventing a complete and thorough security audit of the `LightOFT` contract. Critical logic related to token minting, burning, cross-chain transfers, and specific administrative functions is not visible, making it impossible to assess potential vulnerabilities such as reentrancy, access control bypasses, or economic exploits within the core contract functionality.

**Recommendation:** Provide the complete and verified source code for the `LightOFT` contract to enable a full security assessment. This should include all inherited contracts and libraries that define the core business logic and interactions.


### `L-01` — Broad Solidity Pragma Directive  *(Severity: Low · Status: Unresolved)*

The `pragma solidity` statement `^0.8.20 ^0.8.22;` is overly broad, allowing compilation with a wide range of compiler versions. While the prefill specifies `0.8.29`, a broad pragma can lead to unexpected behavior or introduce vulnerabilities if the contract is compiled with a different, potentially incompatible, compiler version in the future.

**Recommendation:** Pin the Solidity pragma to a specific, tested compiler version (e.g., `pragma solidity 0.8.29;`) to ensure consistent compilation behavior and prevent potential issues arising from compiler version differences.


### `L-02` — Immutability Limits Bug Remediation  *(Severity: Low · Status: Unresolved)*

The contract is not upgradeable, as indicated by `is_proxy: false`. While this removes risks associated with upgrade mechanisms, it means that any critical bugs or vulnerabilities discovered post-deployment cannot be patched. Remediation would require deploying a new contract and migrating all users and assets, which is a complex, costly, and potentially disruptive process.

**Recommendation:** Acknowledge the implications of immutability. Ensure extremely rigorous testing and auditing before deployment. For future projects, consider an upgradeable architecture if the ability to fix bugs or add features is deemed critical.


### `I-01` — Dependency on LayerZero v2 Protocol Security  *(Severity: Informational · Status: Unresolved)*

The `LightOFT` contract, as a LayerZero Omnichain Fungible Token, inherently relies on the security and correct functioning of the underlying LayerZero v2 protocol and its configured message libraries. Any vulnerabilities, exploits, or misconfigurations within the LayerZero infrastructure could directly impact the security, integrity, and economic stability of the OFT.

**Recommendation:** Maintain continuous awareness of LayerZero protocol updates, security advisories, and best practices. Implement robust monitoring for LayerZero-related events and cross-chain message flows. Consider diversifying cross-chain solutions or implementing circuit breakers if the protocol allows for such mechanisms.


### `I-02` — `AddressCast` Library `unchecked` Block Usage Review  *(Severity: Informational · Status: Unresolved)*

The `AddressCast` library utilizes `unchecked` blocks for bit shifting operations. While these blocks are preceded by explicit `if` conditions to validate input sizes (e.g., `_addressBytes.length > 32`, `_size == 0 \|\| _size > 32`), it is crucial that these checks are exhaustive and correctly prevent all potential overflow/underflow scenarios that `unchecked` blocks are designed to bypass.

**Recommendation:** Ensure that the input validation logic preceding `unchecked` blocks is thoroughly reviewed and tested to guarantee that all edge cases and invalid inputs are handled, preventing any unexpected behavior or vulnerabilities from arising within the `unchecked` context.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x477c...3c0e`](https://bscscan.com/address/0x477c2c0459004e3354ba427fa285d7c053203c0e) |
| **Network** | BNB Chain |
| **Price** | $0.131 |
| **24h Volume** | $3.29M |
| **Liquidity** | $1.42M |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 91.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11510 buys / 12500 sells |

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

### Is LIGHT a scam?

Based on automated analysis, LIGHT scores 65/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is LIGHT safe to buy?

Our scanner flagged a risk score of 65/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has LIGHT been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xae02717e94c9b5bae817601a49b4584f58324015)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/light-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
