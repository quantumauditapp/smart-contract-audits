---
token: Huma Finance
ticker: HUMA
network: bsc
risk_score: 47
status: medium
date: 2026-09-26
---

# Huma Finance (HUMA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/huma-finance-bsc)

---

## Audit Summary

The BNBOFT contract is an Omni-Fungible Token (OFT) implementation built on LayerZero V2, inheriting from LayerZero's OFT and OpenZeppelin's Ownable contracts. It provides cross-chain transfer capabilities for a token with 6 decimals. The contract itself is minimal, primarily relying on well-audited external libraries. Key risks identified relate to the extensive control held by the contract owner and the inherent dependency on the LayerZero protocol's security and operational integrity.

> **Final Recommendation:** It is crucial to ensure the security and operational integrity of the 2/2 multisig controlling the BNBOFT contract, as it holds extensive administrative privileges over cross-chain functionality. Implement robust key management practices and consider increasing the multisig threshold for enhanced security. Additionally, ongoing monitoring of the LayerZero protocol's security announcements and updates is recommended due to the contract's heavy reliance on its infrastructure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The BNBOFT contract is minimal, inheriting core functionality from well-audited OpenZeppelin `Ownable` and LayerZero `OFT` libraries (7.2 Code Security). It only overrides the `decimals()` function… |
| **Governance / Economics** | 1/10 | High | The contract utilizes the `Ownable` pattern, with ownership held by a 2/2 multisig, which provides a layer of security against single points of failure for administrative actions (7.5 Governance).… |
| **Upgrades** | 7/10 | Low | The contract is deployed as a standard implementation, avoiding the complexities and potential risks associated with proxy upgrade patterns. This ensures the contract's logic is immutable once… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Extensive Owner Privileges  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Ownable` pattern grants the owner (a 2/2 multisig) extensive control over critical LayerZero OFT configurations, including setting trusted remotes, message libraries, and fee settings. These privileges allow the owner to significantly influence the cross-chain functionality and security of the token. A compromise of the multisig or malicious action by its signers could lead to severe consequences such as halting cross-chain transfers, redirecting funds, or imposing arbitrary fees (7.3 Access Control, 7.5 Governance).

**Recommendation:** While the `Ownable` pattern is standard, consider implementing a more decentralized governance model for critical parameters, such as time-locked changes or a higher multisig threshold (e.g., 3/5). Ensure the multisig signers are highly trusted individuals and follow best practices for key management. Implement robust monitoring for any changes made by the owner.


### `L-01` — External Dependency Risk (LayerZero Protocol)  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract's core functionality, specifically its cross-chain capabilities, relies entirely on the security and operational integrity of the LayerZero protocol and its endpoint. Any vulnerabilities, exploits, or failures within the LayerZero infrastructure could directly affect the BNBOFT token's ability to perform cross-chain transfers, potentially leading to loss of funds or service disruption (7.6 External).

**Recommendation:** Maintain continuous awareness of LayerZero protocol updates, security audits, and community announcements. Implement monitoring for LayerZero endpoint status and any reported incidents. Diversify cross-chain solutions if feasible, or ensure robust contingency plans are in place for LayerZero-related disruptions.


### `I-01` — Immutability of Contract  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The BNBOFT contract is deployed as a standard implementation and is not designed with an upgrade proxy pattern. This means that once deployed, its code cannot be modified. Any future bug fixes, feature enhancements, or changes to the token's logic would necessitate deploying an entirely new contract and migrating existing token holders, which can be a complex, costly, and disruptive process (7.7 Upgrades).

**Recommendation:** This is a design choice. If future upgradeability is desired, consider implementing a proxy pattern (e.g., UUPS) for future deployments. For the current contract, ensure thorough testing and auditing before deployment to minimize the need for future changes.


### `I-02` — Hardcoded Decimals Value  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `decimals()` function in the BNBOFT contract is hardcoded to return `6`. While this is an intentional design choice for the token's precision, it means that the decimal precision cannot be altered post-deployment. This immutability might limit future flexibility if a different decimal precision becomes desirable for ecosystem compatibility or other reasons (7.1 Architecture).

**Recommendation:** This is a design decision. Ensure that the chosen decimal precision of 6 is suitable for all current and anticipated future use cases of the token. If flexibility was a concern, a configurable decimal value could have been implemented, though it adds complexity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9251...a8e6`](https://bscscan.com/address/0x92516e0ddf1ddbf7fab1b79cac26689fdc5ba8e6) |
| **Network** | BNB Chain |
| **Price** | $0.02713 |
| **24h Volume** | $2.68M |
| **Liquidity** | $3.15M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8568 buys / 8243 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7874f0ecd450a5f06acb85543fe1d0d48e1c525f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/huma-finance-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-26*
