---
token: Dust
ticker: DUST
network: bsc
risk_score: 0
status: low
date: 2026-09-06
---

# Dust (DUST) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dust-bsc)

---

## Audit Summary

The FourERC20 contract is an ERC-20 token implementation based on OpenZeppelin. A critical architectural flaw prevents the token from being initialized or having any supply, rendering it unusable. The contract lacks a constructor, meaning its name, symbol, and initial supply cannot be set, resulting in a permanent zero total supply.

> **Final Recommendation:** The current `FourERC20` contract is fundamentally flawed due to the absence of a constructor, which prevents proper initialization and token minting. It is strongly recommended to redeploy a corrected version. The new contract must include a constructor that calls `_init` with desired name and symbol, and also calls `_mint` to establish an initial token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is a basic ERC-20 implementation leveraging OpenZeppelin's `Context` library. It correctly implements standard ERC-20 functions and includes mitigations for allowance race conditions… |
| **Governance / Economics** | 9/10 | Low | The economic model is severely impacted by the critical technical flaw (7.4 Economic). With no constructor to initialize `_name`, `_symbol`, or mint an initial supply, the token will have a permanent… |
| **Upgrades** | 9/10 | Low | The contract is not designed to be upgradeable (7.7 Upgrades). This simplifies its architecture by avoiding proxy-related complexities and potential upgrade safety issues. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 98.7% (≈ permanent lock) |
| **LP Locked** | 98.7% |

## Security Findings

_🔴 1 Critical · ⚪ 2 Informational_

### `C-01` — Missing Constructor and Unmintable Token  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract, which inherits from `Context` and implements `IERC20`, lacks a constructor. The internal `_init` function, responsible for setting the token's `_name` and `_symbol`, is never called. More critically, the `_totalSupply` remains at its default value of zero, and since the internal `_mint` function is not exposed or called by any public function, no tokens can ever be created. This renders the token completely non-functional and unusable, as it will always have a zero supply and no identifiable name or symbol. (7.1 Architecture, 7.2 Code Security, 7.4 Economic)

**Recommendation:** A constructor must be added to the `FourERC20` contract (or its derived contract) that calls `_init(string memory name_, string memory symbol_)` to set the token's metadata. Additionally, the constructor or a controlled public function should call `_mint(address account, uint256 amount)` to establish an initial token supply.


### `I-01` — Base ERC-20 Implementation Lacks Public Minting/Burning  *(Severity: Informational · Status: Unresolved)*

The `FourERC20` contract provides the core ERC-20 logic but keeps the `_mint` and `_burn` functions internal. This design implies that `FourERC20` is intended as a base contract for inheritance, where a derived contract would implement specific supply mechanisms (e.g., a fixed supply, minter role, pauser role). As a standalone contract, it lacks the ability to create or destroy tokens after deployment (assuming a constructor would handle initial minting). (7.1 Architecture)

**Recommendation:** If this contract is intended to be a standalone, deployable token, consider adding public or role-based functions to manage token supply (e.g., `mint(address to, uint256 amount)` with an `onlyOwner` or `onlyMinter` modifier). If it's strictly a base, ensure the derived contract correctly implements supply management.


### `I-02` — `_init` Function Usage  *(Severity: Informational · Status: Unresolved)*

The `_init` function is designed to set the `_name` and `_symbol` of the token. Being an `internal` function, it must be explicitly called by a constructor of the contract itself or a derived contract. If not called, `_name` and `_symbol` will remain empty strings, which is not standard for an ERC-20 token and can cause issues with interfaces displaying token information. (7.1 Architecture)

**Recommendation:** Ensure that any contract inheriting `FourERC20` or `FourERC20` itself, includes a constructor that calls `_init` with appropriate `name_` and `symbol_` parameters.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x932f...4444`](https://bscscan.com/address/0x932fb7f52adbc34ff81b4342b8c036b7b8ac4444) |
| **Network** | BNB Chain |
| **Price** | $0.0002596 |
| **24h Volume** | $404.5K |
| **Liquidity** | $126.0K |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 43.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1173 buys / 921 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x19b2caf222446d28906d0f3e66c877379951cbcb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dust-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-06*
