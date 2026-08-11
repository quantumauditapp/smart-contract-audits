---
token: Pepes Dog
ticker: ZEUS
network: ethereum
risk_score: 13
status: low
date: 2026-08-11
---

# Pepes Dog (ZEUS) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepes-dog-eth)

---

## Audit Summary

The ZEUS token contract implements an ERC-20 standard with taxation and automated liquidity features. However, the provided code is incomplete, critically lacking owner-controlled functions for managing key operational parameters. Furthermore, with ownership renounced, the contract's dynamic features are entirely unmanageable, severely impacting its operability and security posture. The absence of the `sendETHToFee` function also poses a significant risk of collected funds being locked.

> **Final Recommendation:** It is strongly recommended to complete the contract code by implementing all missing owner-controlled functions for critical parameters such as taxes, transaction limits, transfer enablement, and Uniswap router/pair configuration. The `sendETHToFee` function must be fully implemented and thoroughly audited to ensure proper distribution of collected ETH and prevent funds from being locked. Given that ownership has been renounced, any missing administrative functions cannot be called, rendering the contract unmanageable. Future deployments should ensure all necessary administrative functions are present and tested before renouncing ownership.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes `SafeMath` for arithmetic safety and includes a `lockTheSwap` modifier to prevent reentrancy during liquidity operations (7.2 Code Security). However, the provided code is… |
| **Governance / Economics** | 8/10 | Low | The tokenomics include high buy (23%) and sell (25%) taxes, along with max transaction and wallet size limits, which are common anti-whale mechanisms (7.4 Economic). However, the inability to modify… |
| **Upgrades** | 9/10 | Low | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-related risks but also means any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `C-01` — Missing Critical Owner Functions and Renounced Ownership  *(Severity: Critical · Status: Unresolved)*

The contract lacks essential `onlyOwner` functions to manage critical parameters such as `_buyTax`, `_sellTax`, `_maxTxAmount`, `_maxWalletSize`, `_taxSwapThreshold`, `_maxTaxSwap`, `enableTransfers`, `swapEnabled`, `uniswapV2Router`, `uniswapV2Pair`, and the `_isExcludedFromFee` list. Given that `ownership_renounced` is true, the `owner()` address is `address(0)`. This means even if these functions were present, they could not be called, rendering the contract's dynamic features completely unmanageable and immutable. This severely limits operational flexibility and makes it impossible to adapt to market conditions or fix misconfigurations, effectively bricking the contract's administrative…

**Recommendation:** Before deployment, ensure all necessary administrative functions are implemented with `onlyOwner` access control. These functions should allow the owner to configure and update critical parameters. If ownership is to be renounced, it must only occur after all parameters are correctly set and verified, and the contract is fully operational as intended. For this deployed contract, this issue is unresolvable due to renounced ownership.


### `H-01` — Centralization Risk in Fee Distribution (Missing `sendETHToFee` Implementation)  *(Severity: High · Status: Unresolved)*

The `_transfer` function calls `sendETHToFee(address(this).balance)` after a token swap to distribute collected ETH. However, the implementation of the `sendETHToFee` function is not provided in the contract code. If this function is missing or incorrectly implemented, any ETH collected from token swaps will become permanently stuck in the contract, leading to a loss of funds intended for the dev, marketing, and airdrop wallets.

**Recommendation:** Implement the `sendETHToFee` function to securely transfer collected ETH to the designated fee wallets (`_devWallet`, `_marketingWallet`, `_airdropWallet`). Ensure proper checks and error handling are in place. The function should use `call` with a gas limit to prevent reentrancy issues from recipient contracts.


### `M-01` — Unused State Variables  *(Severity: Medium · Status: Unresolved)*

The state variables `transferDelayEnabled` and `tradingOpen` are declared as public but are never referenced or used within the contract's logic. This indicates either dead code, incomplete feature implementation, or a misunderstanding of the contract's intended functionality, potentially misleading users about its capabilities.

**Recommendation:** Remove unused state variables to reduce contract size and improve clarity. If these variables are intended for future features, ensure they are fully implemented and integrated into the contract's logic, or explicitly mark them as reserved for future use.


### `L-01` — Hardcoded and Shared Fee Wallets  *(Severity: Low · Status: Unresolved)*

The `_marketingWallet` and `_airdropWallet` addresses are hardcoded to the same address (`0xBA896c1094ac4A3f61725F62f9092F934cB26515`). This means funds intended for two potentially distinct purposes (marketing and airdrops) will be directed to a single entity. Additionally, these addresses are hardcoded and cannot be changed post-deployment, limiting flexibility for future operational adjustments.

**Recommendation:** If marketing and airdrop funds are intended for separate management, use distinct wallet addresses. Consider implementing `onlyOwner` functions to allow the owner to update these wallet addresses, providing greater flexibility and adaptability for long-term project management.


### `L-02` — Complex Tax Logic in `_transfer`  *(Severity: Low · Status: Unresolved)*

The `_transfer` function contains multiple nested `if` conditions for calculating `taxAmount` and applying exclusions. While the logic appears to correctly handle tax exemptions for excluded addresses and internal transfers, the complexity increases the cognitive load and potential for subtle bugs or unexpected behavior during future modifications or audits.

**Recommendation:** Refactor the tax calculation logic to improve readability and maintainability. Consider using a helper function or a more structured approach to determine the final `taxAmount` based on transfer conditions and exclusion status. Thoroughly test all tax scenarios to ensure correct behavior.


### `I-01` — Unnecessary `unicode` Prefix for String Literals  *(Severity: Informational · Status: Unresolved)*

The `_name` and `_symbol` string literals use the `unicode` prefix (e.g., `unicode"Pepes Dog"`). This prefix is typically used for strings containing non-ASCII characters. For standard ASCII strings, the `unicode` prefix is unnecessary and can be omitted without affecting functionality.

**Recommendation:** Remove the `unicode` prefix from string literals that only contain ASCII characters to adhere to common Solidity coding practices and slightly reduce bytecode size.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f7d...ccc8`](https://etherscan.io/address/0x0f7dc5d02cc1e1f5ee47854d534d332a1081ccc8) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $196.8K |
| **Liquidity** | $170.2K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 42.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 312 buys / 235 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf97503af8230a7e72909d6614f45e88168ff3c10)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepes-dog-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
