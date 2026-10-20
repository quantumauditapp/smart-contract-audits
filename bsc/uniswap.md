---
token: Uniswap
ticker: UNI
network: bsc
risk_score: 68
status: high
date: 2026-09-23
---

# Uniswap (UNI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uniswap-bsc)

---

## Audit Summary

The audited contract is a BEP20 token implementation designed for upgradeability via a proxy. It correctly utilizes `SafeMath` for arithmetic safety and adheres to standard patterns for upgradeable contracts. The primary risk identified is the centralized control over token minting, which allows the owner to increase the total supply, posing a significant economic and governance risk. Other findings include the use of an older Solidity version and the standard ERC-20 `approve` front-running vulnerability.

> **Final Recommendation:** It is crucial to thoroughly review and clearly communicate the token's economic model, especially regarding the minting capability. If a fixed supply is desired, ensure the `_mintable` flag is permanently set to `false` during initialization and consider removing the `mint` function to prevent future supply manipulation. If minting is intended, implement robust governance mechanisms, such as a multi-signature wallet or a DAO, to control the `owner` address and the minting process, thereby distributing control and reducing single-point-of-failure risks. Additionally, consider upgrading the contract to a more recent Solidity version (e.g., 0.8.x) to leverage built-in overflow checks and other compiler improvements, enhancing overall code security and maintainability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates good technical practices, including the consistent use of `SafeMath` (7.2 Code Security) to prevent integer overflows/underflows. It correctly implements the `Initializable`… |
| **Governance / Economics** | 3/10 | High | The contract features a centralized ownership model where a single `_owner` address controls critical functions (7.3 Access Control). Specifically, the `mint` function allows the owner to create an… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for an upgradeable proxy, correctly inheriting from `Initializable` and having an empty constructor (7.7 Upgrades). The state variables are declared in a… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 49.1% |
| **Top-3 Unlocked** | 74.9% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Minting Capability  *(Severity: High · Status: Unresolved)*

The `mint` function, protected by the `onlyOwner` modifier and an `_mintable` flag, allows the contract owner to create an arbitrary amount of new tokens. If `_mintable` is true, this capability grants the owner significant power to inflate the token supply, leading to potential devaluation for existing token holders. This introduces a high economic risk and centralizes control over the token's monetary policy.

**Recommendation:** Clearly define and communicate the token's minting policy. If a fixed supply is intended, ensure the `_mintable` flag is set to `false` during initialization and consider removing or disabling the `mint` function permanently. If minting is a desired feature, implement robust governance mechanisms (e.g., a multi-signature wallet or DAO) to control the `owner` address and the minting process, distributing control and increasing transparency.


### `M-01` — Older Solidity Compiler Version  *(Severity: Medium · Status: Unresolved)*

The contract uses `pragma solidity ^0.6.0`. While `SafeMath` is used to mitigate integer overflow/underflow, using an older compiler version means the contract does not benefit from security enhancements, optimizations, and built-in safety features (like default overflow checks for `uint256` in 0.8.x) present in newer Solidity versions. This can lead to increased technical debt and potentially missed security improvements.

**Recommendation:** Consider upgrading the contract to a more recent and actively maintained Solidity version (e.g., 0.8.x). This would allow the contract to leverage modern compiler features, potentially simplify code by removing explicit `SafeMath` calls, and benefit from ongoing security improvements in the language.


### `L-01` — Standard ERC-20 `approve` Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

The `approve` function, as implemented in the ERC-20 standard, is susceptible to a known front-running attack. If a user attempts to change an allowance from a non-zero value to another non-zero value, a malicious spender could front-run the transaction, spend the original allowance, and then allow the new allowance to be set, effectively spending more than intended. While `increaseAllowance` and `decreaseAllowance` functions are provided to mitigate this, the base `approve` function remains.

**Recommendation:** Advise users and integrated protocols to prefer using `increaseAllowance` and `decreaseAllowance` over direct `approve` calls when modifying existing allowances. If `approve` must be used, recommend setting the allowance to zero first, then to the desired new value, in two separate transactions.


### `I-01` — Truncated Internal Function `_burnFrom`  *(Severity: Informational · Status: Unresolved)*

The provided source code for the internal function `_burnFrom` is truncated. While this function is internal and not directly exposed via the public interface, a complete security assessment would ideally require the full and untruncated code to ensure its logic is sound and free of vulnerabilities.

**Recommendation:** Ensure that all source code, including internal helper functions, is fully available and verified for comprehensive auditing and transparency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbf51...e9b1`](https://bscscan.com/address/0xbf5140a22578168fd562dccf235e5d43a02ce9b1) |
| **Network** | BNB Chain |
| **Price** | $10.1900 |
| **24h Volume** | $112.7K |
| **Liquidity** | $1.56M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 53.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1037 buys / 472 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x03cff636346c653a5a5a24595e21f4da8010237e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uniswap-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
