---
token: Alaya Governance Token
ticker: AGT
network: bsc
risk_score: 31
status: medium
date: 2026-08-11
---

# Alaya Governance Token (AGT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 31/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/alaya-governance-token-bsc)

---

## Audit Summary

The AlayaGovernanceToken contract is a standard ERC20 token implementation, primarily leveraging battle-tested OpenZeppelin Contracts. The technical risk is low due to the use of well-audited libraries and minimal custom logic. Key design decisions include a centralized initial token distribution and the absence of emergency administrative controls.

> **Final Recommendation:** The AlayaGovernanceToken contract is a solid implementation of the ERC20 standard, benefiting from the security and reliability of OpenZeppelin Contracts. It is recommended to thoroughly review the implications of the centralized initial token distribution and the absence of emergency controls, ensuring these design choices align with the project's long-term vision and risk tolerance. For future developments, consider implementing a multi-signature wallet for the deployer address if it retains significant control, and conduct comprehensive testing of any external integrations involving this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture is robust, built upon the latest OpenZeppelin ERC20 implementation (v5.1.0), which includes modern features like ERC-6093 custom errors and correct `unchecked` arithmetic.… |
| **Governance / Economics** | 1/10 | High | The economic model is that of a standard ERC20 token, with a fixed initial supply minted entirely to the deployer (7.4 Economic). This centralizes initial control over the token supply. There are no… |
| **Upgrades** | 6/10 | Medium | The contract is implemented as a standard, non-upgradeable ERC20 token. There are no proxy patterns (e.g., UUPS, Transparent) or beacon proxies used, meaning the contract's logic cannot be modified… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Absence of Emergency Pause/Blacklist Functionality  *(Severity: Low · Status: Unresolved)*

The ERC20 contract does not include any administrative functions for emergency control, such as pausing transfers or blacklisting malicious addresses. While this enhances decentralization by removing single points of control, it also means there is no mechanism to mitigate severe exploits, respond to regulatory demands, or freeze funds in case of theft (7.3 Access Control, 7.8 Operations).

**Recommendation:** Evaluate the project's risk tolerance and operational needs. If emergency intervention capabilities are desired, consider integrating OpenZeppelin's `Pausable` or `AccessControl` contracts. If not, ensure the project's off-chain incident response plan accounts for the immutable nature of the token's operations.


### `I-01` — Centralized Initial Supply Distribution  *(Severity: Informational · Status: Unresolved)*

The constructor of the ERC20 contract mints the entire initial supply of 5,000,000,000 * 10^18 tokens directly to `msg.sender`. This design choice results in a highly centralized initial distribution, where the deployer address holds the entire token supply at launch. While a common pattern for initial token deployment, it implies significant control by a single entity over the token's early circulation (7.4 Economic).

**Recommendation:** Acknowledge and accept this centralized distribution as a design decision. If decentralization is a long-term goal, consider a phased distribution strategy or a multi-signature wallet for managing the initial supply.


### `I-02` — Immutability of Token Parameters  *(Severity: Informational · Status: Unresolved)*

The token's name, symbol, decimals (fixed at 18), and initial total supply are set immutably within the constructor. These parameters cannot be modified after deployment. This ensures consistency and predictability for users and integrated protocols (7.1 Architecture).

**Recommendation:** No action required. This is a standard and often desired characteristic for ERC20 tokens, providing clarity and preventing unexpected changes to fundamental token properties.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5dbd...e274`](https://bscscan.com/address/0x5dbde81fce337ff4bcaaee4ca3466c00aecae274) |
| **Network** | BNB Chain |
| **Price** | $0.01546 |
| **24h Volume** | $1.98M |
| **Liquidity** | $1.19M |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 58.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6819 buys / 7532 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xd3cffc6b02a34dfc72f1350339031043a854599f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/alaya-governance-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
