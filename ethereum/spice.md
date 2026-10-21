---
token: Spice
ticker: SFI
network: ethereum
risk_score: 54
status: medium
date: 2026-09-05
---

# Spice (SFI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spice-eth)

---

## Audit Summary

The audit of the SFI Token (ERC20) contract identified a critical flaw where the token's total supply is not initialized, rendering the token unusable. The contract otherwise uses standard OpenZeppelin patterns, including SafeMath for arithmetic operations, which mitigates common integer vulnerabilities. Informational findings include the use of an older Solidity compiler version and the inherent ERC20 `approve` race condition.

> **Final Recommendation:** The most critical issue is the lack of initial token supply. The contract must be redeployed with a modified constructor in a derived contract that calls `_mint` to establish the initial token supply and assign it to an appropriate address. Additionally, consider upgrading to a newer Solidity compiler version (e.g., `^0.8.x`) to benefit from enhanced security features and gas efficiencies. Users should be educated on using `increaseAllowance` and `decreaseAllowance` to mitigate `approve` front-running risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements a standard ERC20 token using well-vetted OpenZeppelin libraries like SafeMath and Address, ensuring robust arithmetic operations (7.2 Code Security). However, a critical… |
| **Governance / Economics** | 2/10 | High | The economic model is severely impacted by the critical issue of an uninitialized token supply, meaning no tokens can be created or distributed (7.4 Economic). There are no explicit governance… |
| **Upgrades** | 2/10 | High | The contract is a standard, non-upgradeable ERC20 implementation. There are no proxy patterns or upgrade mechanisms present, which eliminates upgrade-related risks (7.7 Upgrades). This means the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 66.7% |
| **Top-3 Unlocked** | ⚠️ 98.1% |

## Security Findings

_🔴 1 Critical · ⚪ 2 Informational_

### `C-01` — Missing Initial Token Supply  *(Severity: Critical · Status: Unresolved)*

The `ERC20` contract's constructor initializes token metadata (`name`, `symbol`, `decimals`) but does not mint any initial supply to an owner or deployer address. The `_mint` function is `internal virtual` and is not called within the provided `ERC20` constructor. Consequently, `_totalSupply` remains 0, and no tokens can ever be created or transferred, rendering the token completely unusable upon deployment.

**Recommendation:** A derived contract must implement a constructor that calls `_mint(deployerAddress, initialSupply)` to create the initial token supply upon deployment. For example: `constructor(string memory name_, string memory symbol_, uint256 initialSupply_) ERC20(name_, symbol_) { _mint(msg.sender, initialSupply_); }`.


### `I-01` — Older Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract uses Solidity version `^0.7.1`. Newer versions (e.g., `^0.8.0` and above) include additional safety checks (like default overflow/underflow protection, removing the need for SafeMath in many cases) and compiler optimizations. While SafeMath is used, leveraging newer compiler features can further enhance security and efficiency.

**Recommendation:** Consider upgrading to a more recent stable Solidity compiler version (e.g., `^0.8.x`) to benefit from improved security features, gas efficiencies, and a more modern development environment.


### `I-02` — ERC20 `approve` Race Condition  *(Severity: Informational · Status: Unresolved)*

The standard `approve` function is susceptible to a known front-running vulnerability. If a user approves an amount `X` for a spender, and then attempts to approve a new amount `Y`, a malicious actor could front-run the second transaction, spending the original `X` amount. The `Y` approval would then still be valid, potentially allowing the spender to spend `X + Y` in total. While `increaseAllowance` and `decreaseAllowance` functions are provided to mitigate this, the base `approve` function remains.

**Recommendation:** Users should be advised to use `increaseAllowance` and `decreaseAllowance` functions instead of directly calling `approve` when modifying existing allowances, as these functions are designed to prevent this specific front-running vector.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb753...902c`](https://etherscan.io/address/0xb753428af26e81097e7fd17f40c88aaa3e04902c) |
| **Network** | Ethereum |
| **Price** | $126.7200 |
| **24h Volume** | $62.4K |
| **Liquidity** | $368.5K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 41.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 56 buys / 72 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xe71aa139ee3304c0abf9d9f9b4232326e4850ecd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spice-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*
