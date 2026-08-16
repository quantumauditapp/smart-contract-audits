---
token: Post-Quantum Coin
ticker: PQC
network: bsc
risk_score: 0
status: low
date: 2026-08-16
---

# Post-Quantum Coin (PQC) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/post-quantum-coin-bsc)

---

## Audit Summary

The `FourERC20` contract is a standard ERC-20 token implementation, largely based on battle-tested OpenZeppelin Contracts. It provides core token functionalities without custom logic for minting, burning, or advanced features. The code adheres to common security practices for ERC-20 tokens, with identified risks primarily related to proper initialization and understanding of its base functionality rather than critical vulnerabilities.

> **Final Recommendation:** It is crucial to ensure that any contract inheriting from `FourERC20` properly calls the internal `_init` function in its constructor to set the token's name and symbol, preventing uninitialized metadata. If dynamic supply management (minting or burning) is desired, a derived contract must be implemented to expose and secure these functionalities with appropriate access control. Thorough testing of the deployment process and any custom logic in derived contracts is recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The technical architecture is robust, leveraging well-audited OpenZeppelin ERC-20 implementations, ensuring a strong foundation (7.1 Architecture). Code security is high, with no apparent reentrancy… |
| **Governance / Economics** | 8/10 | Low | The contract implements a basic ERC-20 token with no inherent governance mechanisms or complex economic models (7.5 Governance, 7.4 Economic). Its economic stability relies solely on its utility and… |
| **Upgrades** | 10/10 | Low | The contract is not designed to be upgradable, as indicated by the absence of proxy patterns or upgrade-specific logic (7.7 Upgrades). This design choice eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 1 Low · ⚪ 1 Informational_

### `L-01` — Potential for Uninitialized Token Metadata  *(Severity: Low · Status: Unresolved)*

The `FourERC20` contract includes an internal `_init` function intended to set the token's `_name` and `_symbol`. However, this function is not called within the `FourERC20` contract itself. If a derived contract fails to call `_init` in its constructor, the `name()` and `symbol()` functions will return empty strings, leading to a poor user experience and potential integration issues with platforms expecting valid metadata.

**Recommendation:** Ensure that any contract inheriting from `FourERC20` explicitly calls the `_init(string memory name_, string memory symbol_)` function within its constructor to properly initialize the token's metadata.


### `I-01` — Absence of Public Supply Control  *(Severity: Informational · Status: Unresolved)*

The `FourERC20` contract provides internal `_mint` and `_burn` functions, but it does not expose any public functions for minting or burning tokens. This means that the total supply of the token is fixed at deployment unless a derived contract explicitly implements and exposes these functionalities. This is a design choice for a base ERC-20 contract but should be noted for deployment planning (7.8 Operations).

**Recommendation:** If dynamic supply management (minting or burning) is required, a new contract inheriting from `FourERC20` must be created to implement and secure these functionalities with appropriate access control. Otherwise, the token's supply will be immutable after initial deployment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x887e...4444`](https://bscscan.com/address/0x887ee6d7cba3d342530d5defbeb13a7409d34444) |
| **Network** | BNB Chain |
| **Price** | $0.00002046 |
| **24h Volume** | $70.2K |
| **Liquidity** | $15.5K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 58.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 831 buys / 486 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x53f85fcfc19ad7b73aa1ace19c63036f27d9726e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/post-quantum-coin-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
