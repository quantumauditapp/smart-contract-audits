---
token: Quant
ticker: QNT
network: ethereum
risk_score: 55
status: medium
date: 2026-09-01
---

# Quant (QNT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quant-eth)

---

## Audit Summary

The audit of the StandardToken contract revealed a critical flaw where the `totalSupply()` function does not accurately reflect the actual circulating supply due to the `mint` function failing to update the `totalSupply_` variable. Additionally, the contract uses an outdated Solidity compiler version, which may expose it to known vulnerabilities. Access control for minting is centralized and immutable, and the ERC-20 `approve` function is susceptible to a race condition.

> **Final Recommendation:** It is imperative to address the critical `totalSupply` calculation error by ensuring the `mint` function correctly updates the `totalSupply_` variable. The contract should be recompiled with a modern, stable Solidity compiler version (e.g., 0.8.x) to benefit from recent security patches and gas optimizations. Consider implementing a multi-signature wallet for the `crowdsale` address to enhance security and decentralization of minting control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract implements the ERC-20 standard using the `SafeMath` library to prevent integer overflows/underflows, which is a strength (7.2 Code Security). However, a critical issue exists where the… |
| **Governance / Economics** | 1/10 | High | The economic model is severely impacted by the `totalSupply` misrepresentation, which can lead to incorrect market valuations and user confusion (7.4 Economic). Access control for the `mint` function… |
| **Upgrades** | 2/10 | High | The contract does not implement any upgradeability patterns, meaning its logic is immutable once deployed (7.7 Upgrades). While this eliminates risks associated with faulty upgrade mechanisms, it… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 76.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Inaccurate `totalSupply` Calculation  *(Severity: Critical · Status: Unresolved)*

The `totalSupply_` variable is initialized to a fixed value (45,467,000 QNT with 18 decimals) and never updated by the `mint` function. This means `totalSupply()` will always return the initial hardcoded value, not the actual sum of all token balances, leading to a critical misrepresentation of the token's circulating supply. This can severely impact market perception, integrations, and overall token economics.

**Recommendation:** Modify the `mint` function to increment `totalSupply_` by `_value` whenever new tokens are minted. Ensure `totalSupply_` accurately reflects the sum of all token balances. Alternatively, remove `totalSupply_` and calculate `totalSupply()` by summing all balances, though this is less gas efficient.


### `H-01` — Outdated Solidity Compiler Version  *(Severity: High · Status: Unresolved)*

The contract uses `pragma solidity ^0.4.21`. This version range is significantly outdated and may be susceptible to known compiler bugs and security vulnerabilities that have been patched in newer versions (e.g., 0.8.x). Deploying with an old compiler version increases the risk of undiscovered or known exploits.

**Recommendation:** Upgrade the Solidity compiler version to a recent, stable release (e.g., `^0.8.0`). Thoroughly test the contract after upgrading, as syntax and behavior may have changed, particularly regarding `assert` vs `require` and default overflow checks.


### `M-01` — ERC-20 `approve` Race Condition  *(Severity: Medium · Status: Unresolved)*

The `approve` function is vulnerable to the known ERC-20 race condition. If a user calls `approve` to change an allowance from `X` to `Y`, and the spender front-runs this transaction by spending `X` tokens, the spender could then spend `Y` tokens, effectively spending `X+Y` tokens. While `increaseApproval` and `decreaseApproval` are provided to mitigate this, the `approve` function itself remains vulnerable.

**Recommendation:** While `increaseApproval` and `decreaseApproval` are good additions, users should be educated to use these functions instead of `approve` when modifying an existing allowance. For `approve` itself, consider adding a check that `_value` is 0 if `allowed[msg.sender][_spender]` is not 0, forcing a two-step approval process (set to 0, then set to new value).


### `M-02` — Immutable Crowdsale Address and Centralized Minting  *(Severity: Medium · Status: Unresolved)*

The `crowdsale` address, which has exclusive permission to call the `mint` function, is set in the constructor and cannot be changed. This creates a single point of control for token minting without any mechanism for transferability or multi-signature protection. If the `crowdsale` key is compromised or lost, it could lead to unauthorized minting or a permanent inability to mint new tokens.

**Recommendation:** Consider implementing a mechanism to transfer ownership of the `crowdsale` role, possibly through a time-locked or multi-signature process. Ideally, the `crowdsale` address itself should be a multi-signature wallet to reduce the risk of a single point of failure.


### `L-01` — Gas Inefficiency with `assert` in SafeMath  *(Severity: Low · Status: Unresolved)*

The `SafeMath` library uses `assert` for overflow/underflow checks. In Solidity versions prior to 0.8.0, `assert` consumes all remaining gas upon failure, whereas `require` refunds unused gas. While functionally correct for preventing arithmetic errors, this can lead to higher gas costs for failed transactions compared to modern `require`-based checks.

**Recommendation:** If upgrading to Solidity 0.8.0+, `SafeMath` might not be strictly necessary due to built-in overflow checks. If remaining in 0.4.x, consider replacing `assert` with `require` in `SafeMath` functions for better gas efficiency on reverts, though this would require careful re-evaluation of the `SafeMath` library's design.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4a22...4675`](https://etherscan.io/address/0x4a220e6096b25eadb88358cb44068a3248254675) |
| **Network** | Ethereum |
| **Price** | $65.4300 |
| **24h Volume** | $103.0K |
| **Liquidity** | $459.8K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 28.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 115 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x24ee2c6b9597f035088cda8575e9d5e15a84b9df)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quant-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
