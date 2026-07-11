---
token: ZygoSwap
ticker: ZSWAP
network: bsc
risk_score: 16
status: low
date: 2026-06-10
---

# ZygoSwap (ZSWAP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zygoswap-bsc)

---

## Audit Summary

The `FourERC20` contract, intended as an ERC20 token, is critically flawed. It lacks any mechanism to mint or burn tokens, resulting in a permanent zero `totalSupply`. Additionally, its name and symbol metadata are uninitialized. These issues render the token completely non-functional and unusable, making it unsuitable for deployment.

> **Final Recommendation:** The `FourERC20` contract, in its current form, is not suitable for deployment. It suffers from critical functional flaws, including the complete absence of token minting/burning capabilities and uninitialized metadata. A comprehensive redesign and re-implementation are required to make it a functional ERC20 token. We recommend engaging for a Premium Deploy option, which includes a full re-audit of the corrected and completed token contract, along with deployment assistance and post-deployment monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical analysis of the `FourERC20` contract reveals severe functional deficiencies (7.2 Code Security). The contract, as provided, does not implement any public or external functions to mint… |
| **Governance / Economics** | 8/10 | Low | The economic model of the `FourERC20` token is non-existent due to the inability to mint or burn tokens (7.4 Economic). This means no supply can ever be created, and thus no economic value can be… |
| **Upgrades** | 8/10 | Low | The contract does not implement any upgradeability pattern (7.7 Upgrades). This means that once deployed, its logic cannot be modified. While this eliminates upgrade-related risks like proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 2 Critical · ⚪ 1 Informational_

### `C-01` — Non-functional ERC20 Token (No Supply Mechanism)  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract, despite inheriting from `IERC20`, does not provide any public or external functions to mint or burn tokens. The `_mint` and `_burn` functions are declared as `internal virtual`, requiring a derived contract to implement and expose them. As a standalone deployment, the `_totalSupply` will always remain zero, making the token completely non-functional and unusable (7.2 Code Security, 7.4 Economic).

**Recommendation:** Implement a constructor or a controlled public function in `FourERC20` or a derived contract that calls `_mint` to initialize the token supply. Ensure appropriate access control (e.g., `Ownable`) is applied to any minting/burning functions.


### `C-02` — Uninitialized Token Metadata  *(Severity: Critical · Status: Unresolved)*

The `_init` function, responsible for setting the token's `_name` and `_symbol`, is declared as `internal` but is not called by any constructor within the `FourERC20` contract. If `FourERC20` is deployed directly, the `name()` and `symbol()` functions will return empty strings, severely impacting the token's usability and display across wallets and exchanges (7.2 Code Security).

**Recommendation:** Add a constructor to the `FourERC20` contract that takes `name_` and `symbol_` as arguments and calls `_init(name_, symbol_)` to ensure proper initialization upon deployment.


### `I-01` — Broad OpenZeppelin Version and Pragma  *(Severity: Informational · Status: Unresolved)*

The `Context.sol` contract indicates `(last updated v4.9.4)` while the `pragma solidity ^0.8.0;` is broad. While `^0.8.0` allows for minor version updates, it's generally recommended to pin the Solidity compiler version to a specific one (e.g., `0.8.20`) to ensure consistent compilation behavior and avoid potential issues with future compiler changes (7.2 Code Security).

**Recommendation:** Pin the Solidity compiler version to the specific version used for testing and deployment (e.g., `pragma solidity 0.8.20;`). Consider upgrading OpenZeppelin contracts to the latest stable version if not already using it.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2e44...4444`](https://bscscan.com/address/0x2e44ab95549b8a12afdb970bde5a6a78365e4444) |
| **Network** | BNB Chain |
| **Price** | $0.002788 |
| **24h Volume** | $1.02M |
| **Liquidity** | $185.9K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 26.6% of supply |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd367e7ea6d26f408b1ccdaafdb251dda6dced821)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zygoswap-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
