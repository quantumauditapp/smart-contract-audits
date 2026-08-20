---
token: 牛来
ticker: NIULAI
network: bsc
risk_score: 39
status: medium
date: 2026-08-20
---

# 牛来 (NIULAI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/niulai-bsc-aba9)

---

## Audit Summary

The `FourERC20` contract is a custom implementation of the ERC-20 standard. A critical vulnerability exists where the token is not initialized, resulting in zero total supply, name, and symbol upon deployment. There are no public functions to mint tokens or set metadata, rendering the token completely unusable. This fundamental flaw makes the contract non-functional as an ERC-20 token.

> **Final Recommendation:** Implement a constructor to properly initialize the token's name, symbol, and initial total supply using the `_mint` function. If the token is intended to be mintable or burnable after deployment, add controlled public functions for these operations, typically restricted to an owner or minter role. Ensure all critical state variables are correctly set upon deployment to make the token functional.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The `FourERC20` contract attempts to implement the ERC-20 standard, leveraging OpenZeppelin interfaces for compliance (7.1 Architecture). However, it suffers from a critical initialization flaw where… |
| **Governance / Economics** | 4/10 | Medium | The contract does not implement any specific governance mechanisms (7.5 Governance). However, its economic viability is critically compromised due to the lack of initialization and minting… |
| **Upgrades** | 8/10 | Low | The contract is not designed to be upgradeable, as indicated by `is_proxy: false` in the prefill (7.7 Upgrades). Therefore, there are no upgrade-specific risks or considerations. Any changes would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized Token State  *(Severity: Critical · Status: Unresolved)*

The `FourERC20` contract lacks a constructor or any public initialization function to set the token's `_name`, `_symbol`, and `_totalSupply`. As a result, upon deployment, the token will have an empty name, empty symbol, and a total supply of zero. This renders the token completely unusable and non-functional as an ERC-20 asset.

**Recommendation:** Add a constructor to the `FourERC20` contract that takes `name_` and `symbol_` as arguments and calls `_init(name_, symbol_)`. Additionally, if an initial supply is desired, call `_mint(msg.sender, initialSupply)` within the constructor to set the `_totalSupply` and assign tokens to the deployer.


### `H-01` — Missing Mint/Burn Access Control  *(Severity: High · Status: Unresolved)*

The `_mint` and `_burn` functions are declared as `internal virtual`, meaning they can only be called by the contract itself or derived contracts. However, there are no public or external functions provided in `FourERC20` that call `_mint` or `_burn`. This design prevents any entity from increasing or decreasing the token's supply after deployment, making it a fixed-supply token without any initial supply, which is a critical limitation.

**Recommendation:** If the token is intended to have minting and burning capabilities, implement public functions (e.g., `mint(address to, uint256 amount)` and `burn(uint256 amount)`) that call the internal `_mint` and `_burn` functions. These public functions should incorporate robust access control mechanisms (e.g., `onlyOwner`, `onlyMinter`) to restrict who can perform these sensitive operations.


### `M-01` — Redundant `unchecked` Blocks After `require` Statements  *(Severity: Medium · Status: Unresolved)*

Several functions, such as `_transfer`, `_burn`, `decreaseAllowance`, and `_spendAllowance`, use `unchecked` blocks for arithmetic operations (e.g., `_balances[from] = fromBalance - amount;`) immediately after a `require` statement has already validated that the operation will not underflow (e.g., `require(fromBalance >= amount)`). While not a vulnerability due to the preceding `require`, the `unchecked` block is redundant and does not provide additional safety or significant gas savings in these specific contexts in Solidity 0.8+.

**Recommendation:** Remove the `unchecked` blocks where a `require` statement already guarantees the safety of the arithmetic operation. This improves code clarity and removes unnecessary constructs without compromising security in Solidity 0.8+.


### `L-01` — Standard ERC-20 `approve` Race Condition  *(Severity: Low · Status: Unresolved)*

The `approve` function, as implemented, is susceptible to a known ERC-20 front-running attack. If a user approves an amount for a spender, and then attempts to change that approval to a lower amount, a malicious spender could front-run the transaction, spend the original approved amount, and then the user's transaction would approve the lower amount, effectively allowing the spender to spend more than intended.

**Recommendation:** While not a critical vulnerability specific to this implementation, it's a known ERC-20 limitation. To mitigate, encourage users to use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` to change an existing allowance. Alternatively, a two-step approval process (approve 0, then approve new amount) can be used, though this is less user-friendly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3cc3...ffff`](https://bscscan.com/address/0x3cc3c4f12dae4908d140c342eff50cf30a56ffff) |
| **Network** | BNB Chain |
| **Price** | $0.0008601 |
| **24h Volume** | $185.2K |
| **Liquidity** | $93.4K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | 11.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1526 buys / 1210 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc1f569122caf558d40481c64c1aec280b2c71da6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/niulai-bsc-aba9)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
