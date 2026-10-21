---
token: Telcoin
ticker: TEL
network: ethereum
risk_score: 26
status: low
date: 2026-09-01
---

# Telcoin (TEL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/telcoin-eth)

---

## Audit Summary

The Telcoin contract is an ERC-20 compliant token implemented in Solidity 0.4.18. It utilizes the SafeMath library to prevent integer overflows/underflows. The contract includes standard ERC-20 functionalities along with `increaseApproval` and `decreaseApproval` to mitigate the common `approve` race condition. While the core logic is sound, the use of an older Solidity compiler version and the inherent `approve` race condition in the base ERC-20 standard present some medium and low-level risks.

> **Final Recommendation:** It is recommended to consider deploying new contracts with a more recent and supported Solidity compiler version to benefit from the latest security features and optimizations. For the existing contract, users should be strongly advised to utilize the `increaseApproval` and `decreaseApproval` functions instead of the standard `approve` function to prevent potential front-running attacks related to allowance changes. Regular security reviews and adherence to best practices for user interaction with ERC-20 tokens are also advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Telcoin contract demonstrates a solid foundation for an ERC-20 token (7.1 Architecture). It correctly implements standard token functionalities and uses the SafeMath library to prevent common… |
| **Governance / Economics** | 3/10 | High | The economic model is straightforward: a fixed supply ERC-20 token (7.4 Economic). All tokens are initially minted to a single distributor address, which represents a point of centralization for… |
| **Upgrades** | 6/10 | Medium | The Telcoin contract is not designed to be upgradeable (7.7 Upgrades). This simplifies its architecture by removing the complexities and potential risks associated with proxy patterns. Consequently… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 2 Low · ⚪ 2 Informational_

### `M-01` — ERC-20 `approve` Race Condition Vulnerability  *(Severity: Medium · Status: Unresolved)*

The `approve` function in the ERC-20 standard is susceptible to a race condition. If a user approves an amount for a spender, and then attempts to change that approved amount to a different value, a malicious actor could front-run the second transaction. This could result in the spender being able to spend both the original and the new approved amounts, leading to an unintended transfer of funds. While `increaseApproval` and `decreaseApproval` functions are provided to mitigate this, the base `approve` function remains vulnerable.

**Recommendation:** Educate users to exclusively use `increaseApproval` and `decreaseApproval` functions when modifying allowances. If `approve` must be used, advise users to first set the allowance to zero before setting a new non-zero allowance, though this still involves two transactions and potential race conditions.


### `L-01` — Outdated Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract is compiled with Solidity version 0.4.18. This version is significantly outdated and lacks numerous security improvements, bug fixes, and gas optimizations introduced in later compiler versions (e.g., 0.5.x, 0.6.x, 0.8.x). While the contract is simple and uses SafeMath, relying on an old compiler can expose the contract to known compiler-level bugs or make it harder to integrate with modern tooling.

**Recommendation:** For any new deployments or significant updates, consider migrating the contract to a more recent and actively supported Solidity compiler version (e.g., 0.8.x) to leverage enhanced security features, better error handling, and gas efficiency.


### `L-02` — SafeMath `div` Function Lacks Division-by-Zero Check  *(Severity: Low · Status: Unresolved)*

The `div` function in the SafeMath library, as implemented, does not explicitly check for division by zero. While Solidity's default behavior for division by zero would revert the transaction, an explicit `require(b != 0)` check would provide clearer error messages and prevent potential unexpected behavior or gas consumption in certain edge cases. In this specific contract, the `div` function is not used, mitigating its direct impact.

**Recommendation:** If the `div` function were to be used in the future, consider adding an explicit `require(b != 0, "SafeMath: division by zero")` check at the beginning of the function for robustness and clarity.


### `I-01` — Centralized Initial Token Distribution  *(Severity: Informational · Status: Unresolved)*

All `totalSupply` tokens are minted and assigned to a single `_distributor` address during contract deployment. This design choice centralizes the initial distribution of tokens to one entity. While common for initial token launches, it means the entire supply is controlled by a single address at genesis.

**Recommendation:** This is a design decision. Ensure the `_distributor` address is secured with robust multi-signature or hardware wallet solutions to prevent unauthorized access and control over the initial token supply.


### `I-02` — Use of `assert` in SafeMath Library  *(Severity: Informational · Status: Unresolved)*

The SafeMath library uses `assert` statements for overflow/underflow checks. In Solidity versions 0.8.0 and later, `assert` failures consume all remaining gas, which can be costly. While this behavior is standard for Solidity 0.4.18 and `assert` is typically used for internal invariants, it's a pattern that has evolved towards `require` for input validation and `revert` for internal errors in newer Solidity versions.

**Recommendation:** For future contracts or if migrating to newer Solidity versions, consider using `require` statements for all validation checks, including arithmetic safety, as they refund unused gas on failure. For this contract, the current implementation is standard for its Solidity version.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x467b...790f`](https://etherscan.io/address/0x467bccd9d29f223bce8043b84e8c8b282827790f) |
| **Network** | Ethereum |
| **Price** | $0.001772 |
| **24h Volume** | $48.6K |
| **Liquidity** | $194.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 52.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 96 buys / 130 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xf359492d26764481002ed88bd2acae83ca50b5c9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/telcoin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
