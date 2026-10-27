---
token: UnifAI
ticker: UAI
network: bsc
risk_score: 41
status: medium
date: 2026-09-02
---

# UnifAI (UAI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unifai-bsc)

---

## Audit Summary

The UaiToken contract implements a standard ERC20 token with ERC20Permit functionality, leveraging battle-tested OpenZeppelin libraries. The contract is simple, with no complex logic or external integrations beyond its core token features. Identified risks are primarily informational or low-severity, related to inherent ERC20Permit characteristics and operational considerations for initial token distribution and emergency controls.

> **Final Recommendation:** Ensure the initial recipient address for the token supply is secured with robust multi-signature controls and cold storage practices to mitigate the risk of centralized asset control. While the lack of emergency controls promotes decentralization, consider the implications for potential future integrations within complex DeFi ecosystems. Thoroughly test any external protocols integrating with UaiToken to ensure compatibility and security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The UaiToken contract (7.1 Architecture, 7.2 Code Security) is a straightforward ERC20 implementation, inheriting extensively from OpenZeppelin's audited contracts for ERC20 and ERC20Permit. This… |
| **Governance / Economics** | 1/10 | High | The UaiToken contract (7.4 Economic, 7.5 Governance) implements a fixed-supply model, minting all tokens to a single recipient during deployment, which is a common initial distribution strategy.… |
| **Upgrades** | 6/10 | Medium | The UaiToken contract (7.7 Upgrades) is not designed as an upgradeable proxy. It is a standard, immutable contract. Therefore, there are no upgrade-related risks or complexities to consider, ensuring… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 2 Low · ⚪ 2 Informational_

### `L-01` — Centralized Initial Token Distribution  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The entire token supply (1,000,000,000 UAI with 18 decimals) is minted to a single `recipient` address during contract deployment. This makes the security of the entire token supply highly dependent on the security of this single address. A compromise of this address would lead to the loss of all tokens, representing a significant operational risk (7.8 Operations).

**Recommendation:** The `recipient` address should be a highly secured multi-signature wallet or a cold storage address. Consider distributing the initial supply across multiple secure addresses or a vesting contract to reduce single points of failure and enhance overall security posture.


### `L-02` — Lack of Emergency Control Mechanisms  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The UaiToken contract does not include any emergency control mechanisms such as a `pause` function or an `onlyOwner` modifier for critical operations. While this promotes decentralization and immutability, it means there is no way to halt transfers or other token operations in the event of a critical vulnerability or exploit in an integrated DeFi protocol (7.3 Access Control, 7.8 Operations).

**Recommendation:** For a simple, fixed-supply token, this might be an intentional design choice. However, if the token is intended for use in complex DeFi ecosystems, consider implementing a well-designed, time-locked, and multi-sig controlled emergency pause mechanism to mitigate unforeseen risks. This should be balanced against the desire for decentralization and immutability.


### `I-01` — Reliance on Third-Party Libraries  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The UaiToken contract heavily relies on battle-tested OpenZeppelin contracts (ERC20, ERC20Permit, ECDSA, EIP712, Nonces). This significantly reduces the likelihood of common vulnerabilities like reentrancy or integer overflows within the core token logic, as these libraries are extensively audited.

**Recommendation:** While OpenZeppelin contracts are highly audited, it is crucial to ensure the specific versions used are free from known vulnerabilities. Regularly monitor OpenZeppelin security advisories and community updates for any potential issues in the dependencies.


### `I-02` — Inherent Front-Running Risk in ERC20Permit  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `permit` function, while providing gasless approvals, is susceptible to front-running. An attacker observing a signed `permit` message off-chain could submit their own transaction with a higher gas price, effectively 'stealing' the approval before the legitimate user's transaction is confirmed. This is an inherent characteristic of the `permit` mechanism and not a flaw in the contract's implementation.

**Recommendation:** Users should be aware of this risk when using `permit`. Projects integrating `permit` should consider mechanisms to mitigate front-running, such as using a relayer network that can submit transactions privately or educating users on best practices for transaction submission.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3e5d...9ea0`](https://bscscan.com/address/0x3e5d4f8aee0d9b3082d5f6da5d6e225d17ba9ea0) |
| **Network** | BNB Chain |
| **Price** | $0.3568 |
| **24h Volume** | $11.6K |
| **Liquidity** | $7.5K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 92.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 757 buys / 668 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x82ed13117144344b39e5ec74d614d54465897a24)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unifai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
