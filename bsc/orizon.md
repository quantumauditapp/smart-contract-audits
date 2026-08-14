---
token: Orizon
ticker: ORI
network: bsc
risk_score: 66
status: high
date: 2026-08-14
---

# Orizon (ORI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orizon-bsc)

---

## Audit Summary

This audit covers an abstract ERC20 token implementation, including SafeMath and ERC20Permit functionalities. The core ERC20 logic is generally sound, utilizing SafeMath for arithmetic safety. However, a significant design concern is the lack of explicit access control for internal minting and burning functions, which could lead to critical vulnerabilities if not properly secured by inheriting contracts. Additionally, a custom square root function in SafeMath introduces potential complexity and precision risks.

> **Final Recommendation:** It is crucial for any contract inheriting this abstract ERC20 implementation to implement robust access control mechanisms for functions that call `_mint` or `_burn`. This will prevent unauthorized token supply manipulation. Additionally, thoroughly review and test any custom mathematical functions, such as `sqrrt`, for precision and edge cases before deployment, or consider using battle-tested libraries for such operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture provides a standard ERC20 token implementation, leveraging the SafeMath library for robust arithmetic operations, which is a strong security practice (7.2 Code Security).… |
| **Governance / Economics** | 2/10 | High | The provided abstract ERC20 contract defines a standard token without specific governance or complex economic mechanisms (7.4 Economic, 7.5 Governance). Its economic behavior is limited to basic… |
| **Upgrades** | 4/10 | Medium | The provided contracts are not designed with upgradeability patterns (e.g., proxy contracts) (7.7 Upgrades). Therefore, there are no upgrade-specific risks associated with this codebase. Any future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Missing Access Control for Mint/Burn Functions (Design Flaw for Implementers)  *(Severity: High · Status: Unresolved)*

The `_mint` and `_burn` functions are declared as `internal virtual` within the abstract ERC20 contract. While internal, any concrete contract inheriting this ERC20 would likely expose these functionalities via public or external functions to manage token supply. The current design does not enforce any access control (e.g., `onlyOwner` or `onlyRole`) on these internal functions, making it a critical design flaw for implementers. If an inheriting contract exposes these functions without proper access control, it could allow any caller to mint or burn tokens, leading to arbitrary supply manipulation and severe economic damage.

**Recommendation:** Implementers of this abstract ERC20 contract MUST ensure that any public or external functions that call `_mint` or `_burn` are protected by strong access control mechanisms. For example, integrate `AccessControl` (which is imported but unused) or `Ownable` to restrict these operations to authorized roles or addresses.


### `M-01` — Custom SafeMath `sqrrt` Function Complexity and Potential Precision Issues  *(Severity: Medium · Status: Unresolved)*

The `SafeMath` library includes a custom implementation of an integer square root function (`sqrrt`). Custom mathematical functions, especially for complex operations like square root, are prone to subtle bugs, edge case failures, or precision issues when dealing with integer arithmetic. While not directly used in the core ERC20 logic, its presence in a foundational library means it could be utilized by other parts of the system, introducing potential vulnerabilities or unexpected behavior.

**Recommendation:** Thoroughly test the `sqrrt` function with a comprehensive suite of test cases, including edge cases (0, 1, large numbers, numbers just above/below perfect squares). Consider using a battle-tested library for complex mathematical operations if high precision and robustness are critical, or simplify the logic if possible.


### `L-01` — Unused OpenZeppelin `AccessControl` Import  *(Severity: Low · Status: Unresolved)*

The `AccessControl` contract from OpenZeppelin is imported at the top of `ERC20.sol` but is not utilized within the provided `ERC20` or `ERC20Permit` abstract contracts. This indicates either an incomplete design where access control was planned but not implemented, or an unnecessary import.

**Recommendation:** Remove unused imports to reduce contract bytecode size, improve readability, and avoid potential confusion. If access control is intended for future implementations, ensure it is properly integrated.


### `I-01` — Use of Older Solidity Version (0.7.5)  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version 0.7.5. While functional, newer Solidity versions (e.g., 0.8.x and above) introduce native overflow/underflow checks for `uint256` arithmetic operations, removing the explicit need for `SafeMath` for basic operations and simplifying code. Newer versions also include various optimizations, bug fixes, and language features.

**Recommendation:** Consider upgrading to a more recent Solidity compiler version (e.g., 0.8.x) to benefit from native overflow checks, improved security features, and language enhancements. This would also allow for removal of `SafeMath` for basic arithmetic, making the code cleaner.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xda03...092e`](https://bscscan.com/address/0xda033999bb6165e64db01bd9be14b40f5653092e) |
| **Network** | BNB Chain |
| **Price** | $51.4900 |
| **24h Volume** | $100.6K |
| **Liquidity** | $2.18M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 99.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.1% |
| **24h Transactions** | 590 buys / 1436 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xf4fbb2fe149e0903e5bda44ee16f2b83ec64fe76)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orizon-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
