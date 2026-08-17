---
token: Superform
ticker: UP
network: base
risk_score: 45
status: medium
date: 2026-08-17
---

# Superform (UP) — Smart Contract Security Analysis | Base

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superform-base)

---

## Audit Summary

The audit of the UpOFT contract, an Omni-chain Fungible Token (OFT) implementation by Superform, reveals a well-structured and generally secure codebase. The contract inherits from LayerZero's OFT and OpenZeppelin's Ownable, providing standard cross-chain token functionality and access control. Key functions like `sweepNative` are properly secured with `onlyOwner` and robust error handling. The primary risks identified are inherent to centralized ownership (mitigated by a multisig) and reliance on external protocols like LayerZero. The contract is not upgradeable, which implies a higher operational risk for bug fixes or feature enhancements.

> **Final Recommendation:** It is recommended to ensure the multisig wallet controlling the contract's ownership is robustly secured, with geographically distributed and trusted signers. Continuous monitoring of the LayerZero v2 protocol for security updates and announcements is crucial due to the contract's inherent dependency. For future contracts, consider the trade-offs of upgradeability versus immutability, especially for core components that may require long-term maintenance or feature evolution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The UpOFT contract demonstrates strong technical security. It correctly inherits from LayerZero's OFT and OpenZeppelin's Ownable, ensuring standard and audited base functionalities (7.1… |
| **Governance / Economics** | 1/10 | High | The contract's governance model relies on the `Ownable` pattern, where a single address (the `_delegate` from the constructor) holds administrative control (7.5 Governance). This centralized control… |
| **Upgrades** | 7/10 | Low | The UpOFT contract is not designed to be upgradeable (7.7 Upgrades). This design choice simplifies the contract's architecture and reduces the attack surface associated with proxy patterns. However… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 58.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Centralized Ownership (Mitigated by Multisig)  *(Severity: Low · Status: Unresolved)*

The `UpOFT` contract utilizes the `Ownable` pattern, granting a single address (the `_delegate` passed in the constructor) exclusive control over sensitive functions such as `sweepNative` and potentially other administrative functions inherited from the `OFT` base contract. While this pattern is common, it introduces a single point of failure if the owner's private key is compromised.

**Recommendation:** The provided information indicates the owner address is a multisig with a 2/4 threshold. This significantly mitigates the risk of a single point of failure. Ensure the multisig signers are distinct, trusted individuals and that the multisig itself is securely managed through robust operational security practices.


### `I-01` — Reliance on LayerZero Protocol Security  *(Severity: Informational · Status: Unresolved)*

The `UpOFT` contract heavily relies on the security and correct functioning of the LayerZero v2 protocol and its endpoint. As an Omni-chain Fungible Token (OFT), its core cross-chain transfer capabilities are entirely dependent on the LayerZero infrastructure. Any vulnerabilities, misconfigurations, or operational issues within the LayerZero protocol could directly impact the `UpOFT` token's cross-chain functionality, integrity, and overall economic stability.

**Recommendation:** It is crucial to continuously monitor LayerZero security announcements, audits, and operational status. Ensure that the configured `_lzEndpoint` address is the official, verified, and most secure endpoint for the respective network. Maintain a robust incident response plan for potential issues originating from external dependencies.


### `I-02` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

The `UpOFT` contract is deployed as a standard, non-upgradeable contract. This design choice means that once deployed, its code cannot be modified. While this simplifies the contract's architecture and eliminates risks associated with upgrade mechanisms (e.g., proxy vulnerabilities), it also implies that any discovered bugs, security vulnerabilities, or desired feature enhancements would necessitate a complete redeployment of the contract. Such a redeployment would require users to migrate their tokens to the new contract, which can be a complex, costly, and disruptive process.

**Recommendation:** For contracts intended for long-term use or those with evolving feature sets, consider implementing an upgradeable proxy pattern (e.g., UUPS, Transparent). If immutability is a deliberate design choice, ensure thorough testing and auditing to minimize the likelihood of critical bugs, and have a clear migration strategy in place should a redeployment become necessary.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5b21...c86b`](https://basescan.org/address/0x5b2193fdc451c1f847be09ca9d13a4bf60f8c86b) |
| **Network** | Base |
| **Price** | $0.05476 |
| **24h Volume** | $189.4K |
| **Liquidity** | $660.0K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 83.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 213 buys / 343 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x37e1490f7f6f98d263f826e1244c7e7f128632f2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superform-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-17*
