---
token: ResearchCoin
ticker: RSC
network: base
risk_score: 55
status: high
date: 2026-07-23
---

# ResearchCoin (RSC) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/researchcoin-base)

---

## Audit Summary

The OptimismMintableERC20 contract serves as a standard ERC20 token designed for cross-chain bridging within the Optimism ecosystem. It correctly implements restricted minting and burning capabilities via a designated bridge contract. The contract leverages well-audited OpenZeppelin libraries and immutable variables for core addresses. The primary risk identified is the inherent dependency on the security and integrity of the external bridge contract, which controls the token's supply.

> **Final Recommendation:** Ensure the `BRIDGE` contract, which has exclusive control over minting and burning, undergoes rigorous security audits and maintains robust operational security. Given the non-upgradeable nature of this token, any identified vulnerabilities in the future would necessitate a new deployment and asset migration, emphasizing the importance of thorough initial review. Consider documenting the implications of the non-upgradeable design for long-term maintenance and potential future changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits good technical quality, inheriting from OpenZeppelin's robust ERC20 implementation and utilizing Solidity 0.8.15 for built-in overflow/underflow protection (7.2 Code Security).… |
| **Governance / Economics** | 3/10 | High | The economic model of the OptimismMintableERC20 token is straightforward: it functions as a bridged representation of a token on another chain. Its economic security and peg stability are entirely… |
| **Upgrades** | 3/10 | High | The OptimismMintableERC20 contract is designed as an immutable, non-upgradeable contract, with key addresses set in the constructor (7.7 Upgrades). This design choice simplifies its security model by… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 47.5% |
| **Top-3 Unlocked** | ⚠️ 90.0% |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Critical Dependency on Bridge Contract Security  *(Severity: Medium · Status: Unresolved)*

The `OptimismMintableERC20` contract's core functionality, specifically the ability to `mint` and `burn` tokens, is exclusively controlled by the `BRIDGE` contract. This makes the token's supply mechanism and overall economic integrity entirely dependent on the security and operational robustness of the external `BRIDGE` contract. A compromise or malfunction of the `BRIDGE` contract would directly lead to unauthorized token issuance or destruction, severely impacting the token's peg and trust (7.6 External).

**Recommendation:** While this dependency is inherent to the bridged token design, it is crucial to ensure the `BRIDGE` contract itself is subject to the highest security standards, including comprehensive audits, formal verification, and robust operational controls. Implement continuous monitoring for the `BRIDGE` contract's activities.


### `I-01` — Inclusion of Legacy Interface Functions  *(Severity: Informational · Status: Unresolved)*

The contract includes several legacy getter functions (`l1Token`, `l2Bridge`, `remoteToken`, `bridge`) for backward compatibility with older interfaces. While these functions do not introduce direct vulnerabilities, they add to the contract's bytecode size and interface complexity, potentially making the contract harder to reason about for new integrations (7.1 Architecture).

**Recommendation:** Ensure that documentation clearly distinguishes between current and legacy functions. For future iterations, consider whether the maintenance of extensive legacy interfaces is necessary, or if a cleaner, more streamlined interface could be adopted.


### `I-02` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

The `OptimismMintableERC20` contract is designed as an immutable contract, with key parameters like `REMOTE_TOKEN` and `BRIDGE` set as `immutable` in the constructor. This means the contract cannot be upgraded or modified after deployment (7.7 Upgrades). While this simplifies the security model by removing upgrade-related risks, it implies that any discovered vulnerabilities or desired feature changes would necessitate a new deployment and a potentially complex migration process for token holders.

**Recommendation:** Acknowledge the implications of a non-upgradeable design. Ensure that the initial deployment is exceptionally robust due to the inability to patch. Plan for potential future migration strategies in case a critical issue or necessary feature update arises.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfbb7...f7e1`](https://basescan.org/address/0xfbb75a59193a3525a8825bebe7d4b56899e2f7e1) |
| **Network** | Base |
| **Price** | $0.09392 |
| **24h Volume** | $54.1K |
| **Liquidity** | $94.1K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 56.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 433 buys / 268 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6cda37ddb9e099bb49495a9ca7df9cd445a6965f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/researchcoin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
