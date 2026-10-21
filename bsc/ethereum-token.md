---
token: Ethereum Token
ticker: ETH
network: bsc
risk_score: 49
status: medium
date: 2026-08-30
---

# Ethereum Token (ETH) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ethereum-token-bsc)

---

## Audit Summary

The BEP20Ethereum contract implements a standard BEP-20 token with minting and burning capabilities, utilizing the Ownable pattern for administrative control and SafeMath for arithmetic safety. The contract demonstrates good practices in preventing common integer overflow/underflow issues and includes functions to mitigate the approve race condition. However, the centralized control over token minting by the owner introduces a significant economic risk, as the total supply can be arbitrarily increased. Additionally, the use of an older Solidity compiler version and some redundant functions are noted as informational findings.

> **Final Recommendation:** It is recommended to carefully consider the implications of centralized minting power and establish clear operational guidelines for the owner's role. For future deployments, consider migrating to a newer Solidity compiler version (e.g., 0.8.x) to leverage built-in safety features and gas optimizations. Review and remove any redundant external functions to optimize contract size and clarity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits strong technical security foundations (7.2 Code Security). It correctly implements the BEP-20 standard and uses the SafeMath library to prevent integer overflow/underflow… |
| **Governance / Economics** | 2/10 | High | The contract employs the Ownable pattern (7.3 Access Control), granting the deployer significant administrative control, including the ability to transfer or renounce ownership. A key economic risk… |
| **Upgrades** | 3/10 | High | The contract is not designed to be upgradeable (7.7 Upgrades), meaning its logic cannot be modified after deployment. This eliminates risks associated with upgrade mechanisms, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.9% |
| **Top-3 Unlocked** | ⚠️ 98.6% |

## Security Findings

_🟢 1 Low · ⚪ 4 Informational_

### `L-01` — Centralized Control over Token Minting  *(Severity: Low · Status: Unresolved)*

The `mint` function is restricted to the contract owner via the `onlyOwner` modifier. This grants the owner the ability to arbitrarily increase the total supply of tokens. While a common design pattern for some tokens, this centralized control over supply can lead to token dilution, impact token economics, and represents a significant centralization risk (7.4 Economic, 7.5 Governance).

**Recommendation:** Clearly communicate the implications of centralized minting to token holders. If decentralization is a goal, consider implementing a timelock for minting operations, a multi-signature wallet for ownership, or a community-governed mechanism for supply adjustments. Alternatively, remove minting functionality if a fixed supply is desired.


### `I-01` — Outdated Solidity Compiler Version  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version 0.5.16. While `SafeMath` is used to mitigate integer overflow/underflow, newer Solidity versions (e.g., 0.8.x and above) include built-in overflow/underflow checks by default, making `SafeMath` largely redundant and potentially reducing gas costs. Newer versions also offer various language improvements and optimizations (7.2 Code Security).

**Recommendation:** Consider upgrading the Solidity compiler version to 0.8.x or higher for future deployments. This would allow for the removal of the `SafeMath` library, potentially reducing bytecode size and gas costs, and leveraging the latest compiler features and security enhancements.


### `I-02` — Redundant External Functions  *(Severity: Informational · Status: Unresolved)*

The contract includes `getOwner()` and `decimals()` external view functions that simply return the values of `owner()` and `_decimals` respectively. These functions are redundant as the underlying state variables or `owner()` function are already publicly accessible. While not a security vulnerability, they add unnecessary bytecode and slightly increase deployment costs (7.2 Code Security).

**Recommendation:** Remove redundant external functions like `getOwner()` and `decimals()`. Users can directly query the `owner()` function or the public `_decimals` state variable.


### `I-03` — Potential `approve` Race Condition (Mitigated)  *(Severity: Informational · Status: Unresolved)*

The standard `approve` function is susceptible to a front-running attack where a malicious spender could exploit a pending `approve` transaction to drain funds if the owner first approves X, then approves Y (where Y < X). However, the contract also provides `increaseAllowance` and `decreaseAllowance` functions. These functions are the recommended way to modify allowances safely by adding or subtracting from the current allowance, thereby mitigating the race condition (7.2 Code Security).

**Recommendation:** Educate users to primarily use `increaseAllowance` and `decreaseAllowance` instead of directly calling `approve` when modifying existing allowances. This best practice helps prevent potential front-running scenarios.


### `I-04` — Confusing Token Name and Symbol  *(Severity: Informational · Status: Unresolved)*

The contract is named `BEP20Ethereum` and implements a BEP-20 token, but its internal `_name` is set to 'Ethereum Token' and `_symbol` to 'ETH'. This naming can be confusing, especially on a network like BSC, as it might be mistaken for the native Ethereum token or an official wrapped version, potentially leading to user errors or misinterpretations (7.6 External, 7.4 Economic).

**Recommendation:** Consider renaming the token's `_name` and `_symbol` to clearly distinguish it from the native Ethereum token or other established assets, especially given its deployment on the BSC network. This enhances clarity and reduces potential user confusion.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2170...33f8`](https://bscscan.com/address/0x2170ed0880ac9a755fd29b2688956bd959f933f8) |
| **Network** | BNB Chain |
| **Price** | $2,507.6500 |
| **24h Volume** | $17.87M |
| **Liquidity** | $15.84M |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 55.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1084 buys / 974 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd0e226f674bbf064f54ab47f42473ff80db98cba)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ethereum-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
