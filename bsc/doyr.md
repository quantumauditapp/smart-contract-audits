---
token: DOYR
ticker: DOYR
network: bsc
risk_score: 0
status: low
date: 2026-07-24
---

# DOYR (DOYR) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doyr-bsc)

---

## Audit Summary

The FourERC20 contract is a standard ERC-20 token implementation, largely based on OpenZeppelin Contracts. It provides core token functionalities like transfers and allowances. The contract exhibits high code quality and adheres to established security practices. No critical or high-severity vulnerabilities were identified. The primary observations relate to its foundational nature, requiring derived contracts for administrative features like minting or burning.

> **Final Recommendation:** The FourERC20 contract is a well-implemented and secure ERC-20 token. Developers extending this contract should carefully consider the implementation of administrative functions (e.g., minting, burning, pausing) in derived contracts, ensuring robust access control and proper initialization logic. Thorough testing of any added functionality and integration points is crucial to maintain the high security standard established by the base contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture (7.1) of the FourERC20 contract is robust, leveraging battle-tested OpenZeppelin libraries for its ERC-20 implementation. This foundation significantly reduces the… |
| **Governance / Economics** | 9/10 | Low | The FourERC20 contract, as a basic ERC-20 implementation, does not incorporate complex economic models (7.4 Economic) or governance mechanisms (7.5 Governance). Its design as a foundational token… |
| **Upgrades** | 10/10 | Low | The FourERC20 contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard, non-upgradeable implementation, which eliminates all risks associated with upgrade mechanisms, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 2 Informational_

### `I-01` — Limited Functionality in Base ERC-20 Implementation  *(Severity: Informational · Status: Unresolved)*

The `FourERC20` contract provides a foundational ERC-20 token without direct public functions for minting, burning, or pausing. While internal `_mint` and `_burn` functions exist, they are not exposed externally by this contract. This design choice means the token's supply is fixed unless extended by a derived contract that implements these administrative capabilities.

**Recommendation:** This is a design choice. If administrative functions like minting, burning, or pausing are desired, they must be implemented in a derived contract. Ensure that any such added functionality includes appropriate access control mechanisms (e.g., `Ownable`, `AccessControl`) and adheres to secure coding practices.


### `I-02` — Internal Initialization Function Design  *(Severity: Informational · Status: Unresolved)*

The `_init` function is an internal helper designed to be called once within a derived contract's constructor to set the token's name and symbol. While `FourERC20` itself cannot be re-initialized, improper usage in a derived contract (e.g., calling it outside the constructor, calling it multiple times, or exposing it publicly) could lead to unexpected state changes or re-initialization issues in the derived contract.

**Recommendation:** Developers extending `FourERC20` should ensure that `_init` is called only once, exclusively within the constructor of the derived contract. Avoid exposing any public functions that could trigger `_init` again, and implement appropriate checks if re-initialization is a concern for the derived contract's specific logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x925c...4444`](https://bscscan.com/address/0x925c8ab7a9a8a148e87cd7f1ec7ecc3625864444) |
| **Network** | BNB Chain |
| **Price** | $0.0002948 |
| **24h Volume** | $67.3K |
| **Liquidity** | $118.9K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 73.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4580 buys / 5048 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Frequently Asked Questions

### Is DOYR a scam?

Based on automated analysis, DOYR scores 67/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is DOYR safe to buy?

Our scanner flagged a risk score of 67/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has DOYR been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x9b487fe6c7f4d62df0a63dbfb0b56b60e55c55f5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doyr-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
