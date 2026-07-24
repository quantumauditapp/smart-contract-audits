---
token: The Final Form Bull
ticker: CZ
network: bsc
risk_score: 25
status: medium
date: 2026-07-22
---

# The Final Form Bull (CZ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 25/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-final-form-bull-bsc)

---

## Audit Summary

The `FourERC20` contract is a base ERC-20 implementation utilizing OpenZeppelin standards. However, it is incomplete as a standalone token, lacking a constructor to initialize its name and symbol, and crucially, any mechanism to mint an initial supply or allow for future supply management. If deployed directly, the token would be non-functional with a zero total supply, rendering it economically inert.

> **Final Recommendation:** It is critical to implement a derived contract that inherits from `FourERC20`. This derived contract must include a constructor to properly initialize the token's `name` and `symbol` by calling `_init`. Most importantly, it needs to establish a clear supply mechanism, such as minting an initial supply to a designated address upon deployment, or providing controlled public functions for minting and burning, protected by appropriate access control. Without these additions, the token will be non-functional.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin libraries for its core ERC-20 functionality, demonstrating good code security practices (7.2 Code Security). Standard functions like `transfer`… |
| **Governance / Economics** | 5/10 | Medium | The contract, as a base ERC-20 implementation, does not include specific governance or economic mechanisms (7.5 Governance, 7.4 Economic). The primary economic risk stems from the absence of any… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgrade mechanism (7.7 Upgrades), as indicated by `is_proxy: false`. This simplifies the architecture by removing upgrade-related complexities and risks, ensuring… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Incomplete Token Implementation: No Supply Mechanism  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract, as provided, is an incomplete ERC-20 implementation. It lacks a constructor to call the internal `_init` function to set `_name` and `_symbol`. More critically, it does not implement any public minting mechanism (e.g., a `_mint` call in the constructor for initial supply, or a public `mint` function) or a burning mechanism. As a result, if deployed directly, the token would have an empty name, symbol, and a `totalSupply` of zero, making it non-functional as a standard ERC-20 token.

**Recommendation:** A derived contract must be implemented that provides a constructor to initialize the token's name and symbol via `_init`, and establish a supply mechanism (e.g., minting an initial supply to a deployer or a treasury, or implementing a controlled minting function).


### `L-01` — Missing Access Control for Future Supply Management  *(Severity: Low · Status: Unresolved)*

The `_mint` and `_burn` functions are internal. While `FourERC20` itself doesn't expose them publicly, any derived contract that does expose them would need to implement robust access control (e.g., `Ownable`, `AccessControl`) to prevent unauthorized supply manipulation. Without such controls, a derived contract could allow anyone to mint or burn tokens, leading to severe economic instability.

**Recommendation:** If a derived contract exposes minting or burning functionality, ensure strong access control mechanisms are in place to restrict these powerful functions to authorized entities only.


### `I-01` — Reliance on OpenZeppelin `Context` for `_msgSender()`  *(Severity: Informational · Status: Unresolved)*

The contract uses OpenZeppelin's `Context` contract to provide `_msgSender()` and `_msgData()`. This is a standard and generally good practice, especially for meta-transaction compatibility, as it abstracts the source of the transaction sender.

**Recommendation:** No specific recommendation, as this is a standard and secure pattern. Ensure the `Context` contract itself is from a trusted source (which OpenZeppelin is).


### `I-02` — `_init` Function Not Called in Base Contract's Constructor  *(Severity: Informational · Status: Unresolved)*

The `_init` function, intended to set `_name` and `_symbol`, is internal and not called within the `FourERC20` contract's constructor. This means if `FourERC20` is deployed directly without a derived contract calling `_init` in its constructor, the token's name and symbol will remain empty strings.

**Recommendation:** Ensure that any contract inheriting from `FourERC20` calls `_init` in its constructor to properly set the token's metadata.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7a84...4444`](https://bscscan.com/address/0x7a848a5a8169aa6a2f603d056a749f924f504444) |
| **Network** | BNB Chain |
| **Price** | $0.008201 |
| **24h Volume** | $1.01M |
| **Liquidity** | $440.8K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 18d |
| **Top-10 Holders** | 77.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4279 buys / 2994 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd55fa2c5e63ecac3a158ca3fed4c8c2185ed45b2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-final-form-bull-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
