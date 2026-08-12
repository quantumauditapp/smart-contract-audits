---
token: TrenchesStarterPack
ticker: 战壕入门包
network: bsc
risk_score: 43
status: medium
date: 2026-08-12
---

# TrenchesStarterPack (战壕入门包) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trenchesstarterpack-bsc)

---

## Audit Summary

The `FourERC20` contract is a basic ERC-20 token implementation based on OpenZeppelin's battle-tested libraries. However, a critical functional flaw exists: the contract, as provided, lacks any mechanism to mint new tokens, rendering the token non-functional as its total supply will always be zero. This fundamental issue prevents the token from being used for any economic purpose.

> **Final Recommendation:** To make the `FourERC20` token functional, it is critically important to implement a token minting mechanism. This should be done in a derived contract that inherits from `FourERC20` and includes a function to call `_mint` (or a similar supply creation method) to establish an initial supply and allow for future token issuance if desired. Additionally, ensure the derived contract's constructor properly calls the `_init` function to set the token's name and symbol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin libraries (v4.9.4) for its ERC-20 implementation, providing a solid foundation for security and adherence to standards (7.2 Code Security). Standard… |
| **Governance / Economics** | 3/10 | High | The economic model is severely impacted by the absence of a token minting mechanism (7.4 Economic). As designed, the token cannot have any supply, making it economically non-viable and preventing any… |
| **Upgrades** | 7/10 | Low | The contract is not designed with upgradeability in mind (7.7 Upgrades), which eliminates risks associated with proxy patterns or upgrade logic. This simplifies the deployment and reduces the attack… |

## Security Findings

_🔴 1 Critical · ⚪ 2 Informational_

### `C-01` — Missing Token Minting Mechanism  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract, as implemented, does not include any function (public or internal) to mint new tokens. The `_totalSupply` variable will therefore always remain zero, and no tokens can ever be created or distributed. The contract comments explicitly state that a supply mechanism must be added in a derived contract using `_mint`, but without such a derived contract, the token is non-functional and cannot be used for any purpose.

**Recommendation:** A derived contract must be created that inherits from `FourERC20` and implements a `_mint` function (or similar mechanism) to create and distribute tokens, updating `_totalSupply` and `_balances`. This derived contract should also call `_init` in its constructor to properly initialize the token's metadata.


### `I-01` — `_init` Function Not Called in Base Contract  *(Severity: Informational · Status: Unresolved)*

The `_init(string memory name_, string memory symbol_)` function is internal and intended to set the token's name and symbol. However, `FourERC20` itself does not have a constructor that calls this function. This means that if `FourERC20` is deployed directly (without a derived contract calling `_init`), its `name()` and `symbol()` functions will return empty strings, leading to improper token metadata.

**Recommendation:** Any contract deriving from `FourERC20` must implement a constructor that calls `_init` with the desired name and symbol to ensure proper token metadata is set upon deployment.


### `I-02` — Truncated `_transfer` Function in Provided Code  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `_transfer` function in `FourERC20.sol` is truncated. While it is likely intended to be the standard OpenZeppelin implementation, the full code is not available for a complete review. Assuming it's the standard implementation, it should include checks for zero addresses and sufficient balances.

**Recommendation:** Ensure the full and correct OpenZeppelin `_transfer` implementation is used, including all necessary checks (e.g., `to` not zero address, `from` having sufficient balance) to prevent potential issues. Provide the complete source code for all contracts for a thorough audit.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x99f5...4444`](https://bscscan.com/address/0x99f5054f1d9799f901df533fbfe5d9b3f25b4444) |
| **Network** | BNB Chain |
| **Price** | $0.00006247 |
| **24h Volume** | $74.5K |
| **Liquidity** | $25.1K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 493 buys / 387 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x851b02b3b782b05aad9d0e2be1c3ba0a3292158f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trenchesstarterpack-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
