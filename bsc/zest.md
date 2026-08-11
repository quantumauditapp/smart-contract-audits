---
token: Zest
ticker: ZEST
network: bsc
risk_score: 42
status: medium
date: 2026-08-11
---

# Zest (ZEST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zest-bsc)

---

## Audit Summary

The ZestToken contract is a standard ERC20 token implementation, inheriting from well-audited OpenZeppelin contracts. It includes ERC20Permit functionality for gasless approvals. The contract exhibits a low overall risk profile due to its simplicity, reliance on battle-tested libraries, and lack of complex external interactions or upgradeability features.

> **Final Recommendation:** The ZestToken contract is a well-implemented and low-risk ERC20 token. Users should be aware of the general front-running risks associated with the `permit` function, which is inherent to the EIP-2612 standard. For future development, consider implementing a multi-signature wallet for the initial deployer address if it holds a significant portion of the token supply, to enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ZestToken contract is built upon the robust and extensively audited OpenZeppelin ERC20 and ERC20Permit libraries, ensuring a high degree of code security and adherence to ERC standards (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The ZestToken contract is a simple, non-governable ERC20 token (7.5 Governance). Its economic model (7.4 Economic) involves a fixed total supply minted entirely to the deployer at creation, with no… |
| **Upgrades** | 5/10 | Medium | The ZestToken contract is not designed to be upgradeable (7.7 Upgrades), which simplifies its architecture and eliminates the risks associated with proxy patterns, upgradeability mechanisms, and… |

## Security Findings

_🟢 1 Low · ⚪ 2 Informational_

### `L-01` — Front-running Risk in ERC20Permit Function  *(Severity: Low · Status: Unresolved)*

The `permit` function, part of the ERC20Permit standard, allows for gasless approvals by signing a message off-chain. However, transactions calling `permit` are susceptible to front-running. A malicious actor observing a `permit` transaction in the mempool could submit their own transaction with a higher gas price, potentially causing the original transaction to fail or be executed in an undesirable order, especially if the `deadline` is far in the future. This is an inherent characteristic of the EIP-2612 standard and not a flaw in the contract's implementation.

**Recommendation:** Users should be advised to set a reasonable and short `deadline` for `permit` signatures to minimize the window for front-running. While the contract implementation is correct, educating users on this risk is important for safe interaction.


### `I-01` — Reliance on OpenZeppelin Contracts  *(Severity: Informational · Status: Unresolved)*

The ZestToken contract heavily relies on OpenZeppelin's battle-tested ERC20 and ERC20Permit implementations. This significantly reduces the risk of common vulnerabilities and ensures adherence to established standards. While OpenZeppelin contracts are highly audited, any future vulnerabilities discovered in these libraries could potentially affect ZestToken.

**Recommendation:** Continue to monitor OpenZeppelin's security advisories and updates. No direct action is required as this is a standard and recommended practice.


### `I-02` — Fixed Total Supply and Initial Distribution  *(Severity: Informational · Status: Unresolved)*

The ZestToken contract mints a fixed total supply of 1,000,000,000 ZEST tokens (with 18 decimals) to the `msg.sender` (deployer) during construction. There are no further minting or burning functionalities available to any address after deployment. This establishes a fixed supply token where the initial distribution is entirely controlled by the deployer.

**Recommendation:** Ensure that the deployer address is a secure, controlled entity (e.g., a multi-signature wallet) to manage the initial token supply effectively and securely. This is a design choice and not a vulnerability, but transparency regarding the initial distribution is crucial for token holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5506...54a1`](https://bscscan.com/address/0x5506599c722389a60580b5213ea1da60d64754a1) |
| **Network** | BNB Chain |
| **Price** | $0.1663 |
| **24h Volume** | $53.0K |
| **Liquidity** | $14.2K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1185 buys / 1193 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6d299f4bad5392af1e55e3e86a0339399543032b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zest-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
