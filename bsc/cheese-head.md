---
token: Cheese Head
ticker: CHEESE
network: bsc
risk_score: 22
status: medium
date: 2026-08-14
---

# Cheese Head (CHEESE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 22/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cheese-head-bsc)

---

## Audit Summary

The CHEESE Token contract implements a standard ERC20 token with Ownable access control. A critical architectural flaw prevents any tokens from being minted, rendering the contract non-functional and unusable. Other minor issues include non-standard decimal configuration and an unused library.

> **Final Recommendation:** Address the critical issue of the unmintable token by implementing a public or owner-controlled minting function, or by calling `_mint` in the constructor to establish an initial supply. This is essential for the token to have any utility. Consider making the `decimals()` function configurable or adhering to the common ERC20 standard of 18 decimals for broader compatibility. Review the necessity of the `Address` library if its functions are not utilized within the contract to reduce bytecode size.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a standard ERC20 token with an Ownable access control pattern. It utilizes Solidity 0.8.26, benefiting from built-in overflow/underflow checks, with `unchecked` blocks… |
| **Governance / Economics** | 7/10 | Low | The contract incorporates the Ownable pattern, granting a single owner control over ownership transfer and renunciation (7.3 Access Control). This centralizes administrative power. Economically, the… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgradeable proxy pattern (7.7 Upgrades). Therefore, any changes to its logic would require a redeployment and migration of assets, which is a significant… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 17.1% |
| **LP Locked** | 17.1% — Null Address |
| **Top-1 Unlocked Holder** | ⚠️ 82.3% |
| **Top-3 Unlocked** | ⚠️ 82.9% |

## Security Findings

_🔴 1 Critical · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Unmintable Token - Critical Functional Flaw  *(Severity: Critical · Status: Unresolved)*

The `_mint` function, which is responsible for increasing the total supply and assigning tokens to an account, is declared as `internal virtual`. However, there is no public or external function within the `ERC20` contract, nor is it called in the constructor, that invokes `_mint`. Consequently, the `_totalSupply` will always remain zero, and no tokens can ever be created or distributed, rendering the token completely unusable.

**Recommendation:** Implement a public or owner-restricted `mint` function that calls `_mint` to allow for token creation. Alternatively, call `_mint` within the constructor to establish an initial token supply upon deployment.


### `L-01` — Non-Standard Decimals Value  *(Severity: Low · Status: Unresolved)*

The `decimals()` function returns a fixed value of 9. While technically valid, the most common standard for ERC20 tokens is 18 decimals. Using a non-standard value like 9 can lead to display issues or misinterpretations in wallets, exchanges, and other DeFi platforms that often default to or expect 18 decimals.

**Recommendation:** Consider changing the `decimals()` function to return 18 for broader compatibility with existing infrastructure. If 9 decimals are intentionally desired, ensure all front-end applications and integrations are aware of and correctly handle this value.


### `I-01` — Unused Address Library  *(Severity: Informational · Status: Unresolved)*

The `Address` library is imported into the contract, but none of its functions (`isContract`, `sendValue`, `functionCall`, `functionStaticCall`) are called or utilized within the provided `ERC20` or `Ownable` contract logic. Including unused libraries can slightly increase bytecode size and deployment costs without providing functional benefits.

**Recommendation:** Remove the import and usage of the `Address` library if its functions are not required by the contract. This will optimize the contract's bytecode size.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x696b...6666`](https://bscscan.com/address/0x696b057564c6b5251a1fd9b90fbf20c454e96666) |
| **Network** | BNB Chain |
| **Price** | $0.00000026 |
| **24h Volume** | $49.6K |
| **Liquidity** | $51.9K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 9d |
| **Top-10 Holders** | 36.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 440 buys / 348 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8533b10e0b0796d5a03102618061778341208758)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cheese-head-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
