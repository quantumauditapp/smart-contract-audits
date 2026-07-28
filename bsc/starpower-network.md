---
token: Starpower Network
ticker: STAR
network: bsc
risk_score: 49
status: high
date: 2026-07-27
---

# Starpower Network (STAR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/starpower-network-bsc)

---

## Audit Summary

This audit report is based on a partial source code submission, specifically OpenZeppelin library dependencies (`Context.sol`, `ECDSA.sol`). The core contract, `PeerToken`, was not provided for review. Consequently, a comprehensive security assessment of the `PeerToken` contract's specific logic, functionality, and potential vulnerabilities could not be performed. The findings primarily address general architectural considerations and the implications of the missing source code, alongside observations about the provided libraries and the contract's operational setup.

> **Final Recommendation:** To enhance the security posture, it is crucial to provide the complete source code for the `PeerToken` contract for a comprehensive audit. For critical administrative functions, consider transitioning from an EOA owner to a multi-signature wallet to mitigate single points of failure. Evaluate the trade-offs of immutability versus upgradeability for future deployments, ensuring thorough testing if a non-upgradeable design is chosen.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The provided code consists of well-audited OpenZeppelin libraries (Context, ECDSA), which are robust and widely used, indicating a strong foundation for these components (7.2 Code Security). However… |
| **Governance / Economics** | 2/10 | High | The contract is controlled by an Externally Owned Account (EOA) owner, `0xb8169426da25f63f557189492cfb0e7b9f52ca7a`, which centralizes significant administrative power (7.5 Governance). This single… |
| **Upgrades** | 6/10 | Medium | The contract is not deployed as an upgradeable proxy, meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates risks associated with proxy implementation bugs or upgrade path… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control by EOA Owner  *(Severity: Medium · Status: Unresolved)*

The `PeerToken` contract is controlled by an Externally Owned Account (EOA) at `0xb8169426da25f63f557189492cfb0e7b9f52ca7a`. This centralizes significant power, such as potential minting, burning, pausing, or parameter modification, depending on the token's implementation. An EOA is a single point of failure; if its private key is compromised, the entire contract's integrity could be at risk (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for critical administrative functions. This distributes control among multiple trusted parties, significantly reducing the risk associated with a single compromised key. Alternatively, explore transitioning to a decentralized governance model.


### `L-01` — Lack of Upgradeability  *(Severity: Low · Status: Unresolved)*

The contract is not deployed as an upgradeable proxy. This means that once deployed, its logic cannot be modified. While this eliminates upgrade-related risks (7.7 Upgrades), it also prevents bug fixes, feature enhancements, or parameter adjustments without a full redeployment and migration of user funds/states (7.8 Operations).

**Recommendation:** For future deployments, evaluate the trade-offs between non-upgradeable and upgradeable contracts. If flexibility for bug fixes or feature additions is desired, consider using a well-audited proxy pattern (e.g., UUPS). If immutability is a core design principle, ensure the initial deployment is thoroughly tested and audited.


### `I-01` — Incomplete Source Code Provided for Core Contract  *(Severity: Informational · Status: Unresolved)*

The source code for the main contract, `PeerToken`, was not provided for review. Only OpenZeppelin library dependencies (`Context.sol`, `ECDSA.sol`) were available. This prevents a comprehensive security assessment of the contract's specific business logic, state variables, and potential vulnerabilities (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Provide the complete and verified source code for the `PeerToken` contract to enable a thorough and accurate security audit. Without the full source, the overall risk assessment remains significantly limited.


### `I-02` — Reliance on Well-Audited OpenZeppelin Libraries  *(Severity: Informational · Status: Resolved)*

The provided code snippet exclusively consists of standard, battle-tested OpenZeppelin contracts (`Context`, `ECDSA`). These libraries are widely used and have undergone extensive audits and community review, significantly reducing the risk of vulnerabilities within these specific components (7.2 Code Security).

**Recommendation:** Continue to leverage well-vetted and actively maintained libraries. Ensure that the versions used are up-to-date and compatible with the project's Solidity compiler version to benefit from the latest security patches and improvements.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8fce...787c`](https://bscscan.com/address/0x8fce7206e3043dd360f115afa956ee31b90b787c) |
| **Network** | BNB Chain |
| **Price** | $0.1013 |
| **24h Volume** | $2.05M |
| **Liquidity** | $1.49M |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 47.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6520 buys / 6888 sells |

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

### Is Starpower Network a scam?

Based on automated analysis, Starpower Network scores 63/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Starpower Network safe to buy?

Our scanner flagged a risk score of 63/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Starpower Network been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb4db9fcda97fd7b02eaf1e8317e6ddb04bacc1af)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/starpower-network-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-27*
