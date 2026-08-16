---
token: FinTech AI
ticker: FNA
network: bsc
risk_score: 68
status: high
date: 2026-08-16
---

# FinTech AI (FNA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fintech-ai-bsc)

---

## Audit Summary

The provided code implements a custom ERC20 token with EIP-2612 permit functionality and a custom SafeMath library. The core ERC20 logic largely follows established patterns. However, a critical issue was identified in the EIP-712 DOMAIN_SEPARATOR calculation, which could invalidate permit signatures. Additionally, the custom SafeMath library introduces complexity, and the base contract lacks explicit access control for sensitive token operations.

> **Final Recommendation:** It is strongly recommended to correct the EIP-712 DOMAIN_SEPARATOR calculation to include the 'version' string, ensuring the 'permit' function operates securely and as intended. Implement robust access control mechanisms for all sensitive functions, particularly '_mint' and '_burn', in the derived 'ERC20TokenX' contract. Thoroughly review and test the custom SafeMath functions, especially 'sqrrt' and the percentage calculations, for gas efficiency, precision, and adherence to the intended economic model. Consider upgrading to a more recent Solidity compiler version (e.g., 0.8.x) to benefit from native overflow checks and other improvements, reducing reliance on custom SafeMath for basic arithmetic.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture is based on a standard ERC20 token with EIP-2612 permit extensions. The contract utilizes a custom SafeMath library for arithmetic operations, which is appropriate for… |
| **Governance / Economics** | 2/10 | High | The economic model relies on custom arithmetic functions within SafeMath, such as 'percentageAmount' and 'quadraticPricing', which require careful validation against the intended design (7.4… |
| **Upgrades** | 4/10 | Medium | The provided contract code does not implement any proxy patterns or upgrade mechanisms, indicating it is intended to be immutable (7.7 Upgrades). This simplifies the upgrade risk profile, as there… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing 'version' in EIP-712 DOMAIN_SEPARATOR Calculation  *(Severity: High · Status: Unresolved)*

The EIP-712 `DOMAIN_SEPARATOR` typehash includes `string version`, but the constructor's `abi.encode` call for `DOMAIN_SEPARATOR` only provides `name()`, `chainID`, and `address(this)`. The `version` string is omitted. This will result in an incorrect `DOMAIN_SEPARATOR`, causing `permit` signatures to be invalid or potentially vulnerable to replay attacks if the `name` and `chainId` are identical across different deployments with varying intended versions.

**Recommendation:** Ensure the `DOMAIN_SEPARATOR` calculation in the `ERC20Permit` constructor includes a `version` string, consistent with the EIP-712 typehash. For example, add a `version_` parameter to the constructor and pass it to `abi.encode`.


### `M-01` — Complexity and Potential Precision/Gas Issues in Custom SafeMath Functions  *(Severity: Medium · Status: Unresolved)*

The custom `SafeMath` library includes several complex functions beyond basic arithmetic, such as `sqrrt`, `percentageAmount`, `substractPercentage`, `percentageOfTotal`, `quadraticPricing`, and `bondingCurve`. The `sqrrt` function uses an iterative approximation, which could be gas-intensive for very large numbers or if many iterations are required. The percentage calculations (`percentageAmount`, `substractPercentage`, `percentageOfTotal`) use a divisor of 1000 (permille), which might lead to precision loss for small amounts or if higher precision is expected (e.g., standard percentages out of 100).

**Recommendation:** Thoroughly review and test all custom `SafeMath` functions for gas efficiency, precision, and correctness against the intended mathematical and economic models. Consider using established libraries for complex mathematical operations if available. Document the expected precision and behavior of percentage calculations.


### `L-01` — Lack of Explicit Access Control for Sensitive Base Functions  *(Severity: Low · Status: Unresolved)*

The `_mint` and `_burn` functions in the `ERC20` base contract are declared as `internal virtual`. While this design allows derived contracts to implement them, the `ERC20` contract itself does not enforce any access control mechanisms (e.g., `onlyOwner`, `onlyMinterRole`) for these critical token supply management operations. Although the `AccessControl` library is imported, it is not utilized in the provided snippet.

**Recommendation:** The derived contract (e.g., `ERC20TokenX`) must implement robust access control for `_mint` and `_burn` functions to prevent unauthorized token creation or destruction. This could involve using OpenZeppelin's `AccessControl` roles or an `Ownable` pattern.


### `I-01` — Older Solidity Compiler Version (0.7.5)  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version 0.7.5. This version does not include native overflow/underflow checks, requiring the use of a custom `SafeMath` library. Newer Solidity versions (0.8.0 and above) include these checks by default, which can simplify code and reduce reliance on external libraries for basic arithmetic safety. Older compiler versions may also lack recent optimizations or security patches.

**Recommendation:** Consider upgrading the Solidity compiler version to 0.8.x or higher. This would allow for the removal of the `SafeMath` library for basic arithmetic operations, simplifying the codebase and leveraging native compiler security features. Ensure thorough testing if upgrading, as there might be minor breaking changes.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0833...114e`](https://bscscan.com/address/0x08332a515cb2a57884176e887b682e7da2eb114e) |
| **Network** | BNB Chain |
| **Price** | $3.8100 |
| **24h Volume** | $92.7K |
| **Liquidity** | $879.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 95.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.1% |
| **24h Transactions** | 1799 buys / 4964 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa0cc1bdc044554116467f866f4c320707c3eb288)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fintech-ai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
