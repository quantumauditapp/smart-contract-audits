---
token: 龙虾
ticker: 龙虾
network: bsc
risk_score: 24
status: medium
date: 2026-08-12
---

# 龙虾 (龙虾) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 24/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-41fa71-bsc)

---

## Audit Summary

The audited contract, FourERC20, is an implementation of the ERC-20 token standard, largely based on OpenZeppelin Contracts. It provides core token functionalities such as transfers, allowances, minting, and burning. The contract itself is a base implementation, meaning it relies on derived contracts to expose administrative functions like minting and burning with appropriate access control. While the core logic is robust, the absence of built-in access control for these critical functions in the base contract necessitates careful implementation in any inheriting contract to prevent severe vulnerabilities.

> **Final Recommendation:** It is crucial for any contract inheriting from FourERC20 to implement robust access control mechanisms for administrative functions, particularly `_mint` and `_burn`. Consider using established patterns like OpenZeppelin's `Ownable` or `AccessControl` to restrict who can perform these sensitive operations. Thoroughly test the derived contract's constructor to ensure `_init` is called correctly and that the token's name and symbol are properly set. Additionally, review the `unchecked` blocks for `_totalSupply` updates to ensure they align with the intended security model of the derived contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The FourERC20 contract leverages OpenZeppelin's battle-tested ERC-20 implementation, ensuring a high standard of code security for core token operations (7.2 Code Security). Solidity 0.8+ provides… |
| **Governance / Economics** | 4/10 | Medium | The FourERC20 contract, as a base ERC-20 implementation, does not include any inherent governance or economic mechanisms (7.5 Governance, 7.4 Economic). Its economic model, including total supply… |
| **Upgrades** | 9/10 | Low | The FourERC20 contract is not designed as an upgradeable proxy contract (7.7 Upgrades). It is intended to be deployed as a standalone token or as an implementation contract for a proxy pattern… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 33.6% |
| **Top-3 Unlocked** | 64.2% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing Access Control for Supply Management Functions  *(Severity: High · Status: Unresolved)*

The `_mint` and `_burn` functions, which control the total supply of the token, are implemented as `internal` functions in the FourERC20 base contract. However, the contract does not provide any built-in access control mechanisms (e.g., `onlyOwner`, `onlyRole`) to restrict who can call these functions when they are exposed by a derived contract. If a derived contract exposes `mint()` or `burn()` functions without proper authorization checks, any external caller could potentially mint an arbitrary amount of tokens or burn existing tokens, leading to a complete loss of token value and integrity (7.3 Access Control, 7.4 Economic).

**Recommendation:** Any contract inheriting from FourERC20 and exposing `_mint` or `_burn` functionality must implement strong access control. Utilize established patterns like OpenZeppelin's `Ownable` or `AccessControl` to ensure that only authorized addresses or roles can execute these critical supply-altering functions. For example, add an `onlyOwner` modifier to the public `mint` and `burn` functions in the derived contract.


### `L-01` — Reliance on Derived Contract for Initialization  *(Severity: Low · Status: Unresolved)*

The `_init` function, responsible for setting the token's `_name` and `_symbol`, is an `internal` function. This design requires any contract inheriting from FourERC20 to explicitly call `_init` in its constructor. Failure to call `_init` in the derived contract's constructor would result in the token having empty strings for its name and symbol, which could lead to display issues in wallets and interfaces (7.1 Architecture).

**Recommendation:** Ensure that any derived contract explicitly calls `_init(string memory name_, string memory symbol_)` in its constructor to properly set the token's metadata. For example: `constructor(string memory name_, string memory symbol_) { _init(name_, symbol_); }`.


### `I-01` — Unchecked Arithmetic for `_totalSupply`  *(Severity: Informational · Status: Unresolved)*

The `_totalSupply` variable is updated within `unchecked` blocks in both the `_mint` and `_burn` functions. While Solidity 0.8.0 and later versions automatically include overflow/underflow checks by default, `unchecked` blocks explicitly disable these checks. Although `_balances` updates are not in `unchecked` blocks and are protected, `_totalSupply` could theoretically overflow or underflow if an extremely large `amount` is passed to `_mint` or `_burn` without prior validation, potentially leading to an inconsistent state between `_totalSupply` and the sum of `_balances` (7.2 Code Security).

**Recommendation:** While the risk is low given the typical use of `_mint` and `_burn` with controlled `amount`s and the protection on individual balances, consider whether the `unchecked` block for `_totalSupply` is strictly necessary. If `_totalSupply` is intended to always reflect the sum of balances, ensuring it also benefits from default overflow/underflow checks could provide an additional layer of safety, or ensure robust validation of `amount` before calling `_mint`/`_burn`.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xeccb...4444`](https://bscscan.com/address/0xeccbb861c0dda7efd964010085488b69317e4444) |
| **Network** | BNB Chain |
| **Price** | $0.01927 |
| **24h Volume** | $3.24M |
| **Liquidity** | $981.0K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 88.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12309 buys / 12842 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x22af7297243c4eef12e2d5a4f888b92e56bf127c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-41fa71-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
