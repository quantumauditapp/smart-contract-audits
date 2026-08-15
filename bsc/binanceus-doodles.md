---
token: binanceus doodles
ticker: BOODLES
network: bsc
risk_score: 17
status: low
date: 2026-08-15
---

# binanceus doodles (BOODLES) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binanceus-doodles-bsc)

---

## Audit Summary

This audit covers a partial implementation of an ERC-20 token contract, `FourERC20`, which is based on OpenZeppelin standards. The primary concern is the critical lack of a defined token supply mechanism (e.g., minting/burning functions) within the provided code, which is stated to be implemented in a derived contract. Additionally, a significant portion of the `_transfer` function is truncated, preventing a complete security analysis of core token logic. The contract lacks an emergency pausing mechanism.

> **Final Recommendation:** It is critical to provide the complete source code, especially for the derived contract that implements the token supply mechanism, to allow for a comprehensive security assessment. The design of the minting and burning functions, including their access control, must be thoroughly reviewed to prevent economic manipulation. Additionally, consider implementing an emergency pausing mechanism to mitigate risks during unforeseen events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's robust ERC-20 implementation, providing standard token functionalities like `transfer`, `approve`, and `allowance` (7.2 Code Security). The use of `unchecked`… |
| **Governance / Economics** | 7/10 | Low | The most significant economic risk stems from the explicitly stated absence of a token supply mechanism (e.g., `_mint` or `_burn`) within the `FourERC20` contract itself, deferring it to a derived… |
| **Upgrades** | 9/10 | Low | The contract is explicitly marked as `is_proxy: false`, indicating it is not intended to be upgradeable in its current deployment (7.7 Upgrades). The use of an `_init` function, typically found in… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Undefined Token Supply Mechanism  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract explicitly states that a supply mechanism (e.g., `_mint`) must be added in a derived contract. Without the full implementation of the derived contract, the total supply, minting, and burning capabilities of the token are unknown. This prevents a complete economic and security analysis of the token's fundamental properties, leaving it vulnerable to potential uncontrolled inflation or deflation if the derived contract's implementation is flawed or malicious (7.4 Economic).

**Recommendation:** Provide the complete source code for the derived contract that implements the token supply mechanism. Ensure that minting and burning functions have robust access control (e.g., only callable by a trusted multisig or governance) and clear, auditable logic to prevent unauthorized supply manipulation.


### `M-01` — Truncated Code Snippet for Critical Functions  *(Severity: Medium · Status: Unresolved)*

The provided source code for the `_transfer` function, a core component of ERC-20 token movement, is truncated. This prevents a full and accurate security analysis of the token's transfer logic, including checks for zero addresses, sufficient balances, and potential reentrancy vectors if external calls were introduced (7.2 Code Security).

**Recommendation:** Provide the complete and untruncated source code for all contracts, especially critical internal functions like `_transfer`, to enable a thorough security audit.


### `L-01` — Lack of Emergency Pausing Mechanism  *(Severity: Low · Status: Unresolved)*

The `FourERC20` contract does not include a mechanism to pause token transfers or other critical operations. In the event of a critical vulnerability, exploit, or market manipulation, the absence of a pausing mechanism could lead to irreversible damage or loss of funds (7.8 Operations).

**Recommendation:** Consider integrating OpenZeppelin's `Pausable` module or a similar custom pausing mechanism. This would allow a designated role (e.g., an owner or multisig) to temporarily halt critical functions during emergencies, providing time to address issues.


### `I-01` — `_init` Function in Non-Proxy Context  *(Severity: Informational · Status: Unresolved)*

The contract utilizes an `_init` function for setting `_name` and `_symbol`, which is a common pattern in upgradeable proxy contracts for initialization after deployment. However, the contract is marked as `is_proxy: false`. While the `_init` function is `internal` in the provided snippet, if this contract were later used as an implementation contract for a proxy without an `initializer` modifier, it could lead to reinitialization vulnerabilities (7.7 Upgrades).

**Recommendation:** If this contract is not intended for use as an upgradeable proxy implementation, ensure that any constructor or external function calling `_init` is properly secured. If it is intended for proxy use, ensure the `_init` function is protected by an `initializer` modifier to prevent multiple calls.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc708...4444`](https://bscscan.com/address/0xc708c48944600c03227895abda42ca7f38c64444) |
| **Network** | BNB Chain |
| **Price** | $0.00002709 |
| **24h Volume** | $123.9K |
| **Liquidity** | $28.8K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 104.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 991 buys / 1134 sells |

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

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xad79fce045bcca625e9b5aec77cdac942b262bd5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binanceus-doodles-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
