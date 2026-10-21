---
token: ODYS
ticker: ODYS
network: arbitrum
risk_score: 64
status: medium
date: 2026-08-30
---

# ODYS (ODYS) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/odys-arb)

---

## Audit Summary

The OdysToken contract implements a standard ERC-20-like token with additional transfer restrictions based on wallet and transaction size, active during an initial period. The audit identified a critical vulnerability related to unchecked arithmetic in balance updates, which could lead to token loss. High-severity issues include potential overflows in restriction calculations. Medium and low-severity issues pertain to restriction logic clarity and standard ERC-20 front-running. Informational findings highlight centralized control and immutability of key parameters.

> **Final Recommendation:** It is imperative to address the critical unchecked arithmetic vulnerability in the `_move` function immediately to prevent potential token loss. All arithmetic operations involving token balances and restriction calculations should be thoroughly reviewed for overflow/underflow conditions, ensuring safe math practices are consistently applied. Consider re-evaluating the `maxTx` and `maxWallet` logic for clarity and consistency, and implement robust security measures for the `factory` address, such as multi-signature control, given its centralized power. Thoroughly test all restriction mechanisms under various edge cases, including maximum possible values for `totalSupply` and `maxWalletBps`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract's architecture is a straightforward ERC-20-like token with custom transfer restrictions (7.1 Architecture). However, a critical code security flaw exists in the `_move` function where… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4 Economic) includes initial transfer restrictions based on wallet and transaction size, which are active for a set `restrictionSeconds` period. The `factory` address holds… |
| **Upgrades** | 5/10 | Medium | The OdysToken contract is not designed as an upgradeable proxy (7.7 Upgrades). All logic is contained within a single, immutable contract. This eliminates upgrade-related risks but means any future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 95.0% |
| **Top-3 Unlocked** | ⚠️ 98.7% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Unchecked Arithmetic in Balance Update  *(Severity: Critical · Status: Unresolved)*

The `_move` function uses an `unchecked` block for `balanceOf[to] += value;`. If `balanceOf[to] + value` exceeds `type(uint256).max`, the sum will wrap around, leading to an incorrect (smaller) balance for the recipient. This effectively burns tokens from the recipient and represents a severe loss of funds vulnerability.

**Recommendation:** Remove the `unchecked` block around `balanceOf[to] += value;`. Solidity 0.8+ by default checks for overflows/underflows, so explicit `unchecked` should only be used for intentional wrapping with clear justification and mitigation strategies.


### `H-01` — Potential Overflow in Restriction Calculations  *(Severity: High · Status: Unresolved)*

The `maxWallet()` and `maxTx()` functions calculate limits using `(totalSupply * maxWalletBps) / BPS` and `(w * 110) / 100`. If `totalSupply` is extremely large, the intermediate multiplication `totalSupply * maxWalletBps` or `w * 110` could overflow `uint256` before the division. This would result in a wrapped-around, smaller-than-intended limit, potentially allowing users to bypass intended restrictions or causing incorrect economic behavior.

**Recommendation:** Implement safe math for these calculations. Ensure intermediate products do not exceed `type(uint256).max` by carefully reordering operations (e.g., `(totalSupply / BPS) * maxWalletBps` if `totalSupply` is divisible by `BPS`) or by explicitly checking for overflow before multiplication.


### `M-01` — Ambiguous `maxTx` and `maxWallet` Restriction Logic  *(Severity: Medium · Status: Unresolved)*

The `maxTx()` function calculates a limit that is 110% of `maxWallet()`. While the `_move` function correctly checks `value > maxTx()` and then `balanceOf[to] + value > maxWallet()`, the `maxTx` limit being greater than `maxWallet` can be confusing. This design choice might lead to unexpected user experience or misinterpretation of the actual limits, as a transaction could pass the `maxTx` check but still fail the `maxWallet` check if the recipient's current balance is non-zero.

**Recommendation:** Clarify the intended behavior of `maxTx` relative to `maxWallet`. Consider if `maxTx` should always be less than or equal to `maxWallet` to prevent scenarios where a single transaction could theoretically exceed the wallet limit if the recipient's balance was zero. Alternatively, document this behavior clearly for users and developers.


### `L-01` — Standard ERC-20 `approve` Front-Running Vulnerability  *(Severity: Low · Status: Unresolved)*

The `approve` function follows the standard ERC-20 implementation, which is susceptible to a known front-running vulnerability. If a user approves an amount `X` for a spender, and then decides to change it to `Y` (where `Y < X`), a malicious front-runner could observe the transaction changing the allowance to `Y`, quickly execute a `transferFrom` for amount `X` (or part of it), and then the user's transaction to set allowance to `Y` would still go through. The spender would then have `Y` allowance in addition to the `X` they just spent.

**Recommendation:** While this is a common ERC-20 pattern, it's best practice to mitigate it. Recommend implementing the 'approve-and-call' pattern or requiring users to set allowance to zero before approving a new non-zero amount.


### `I-01` — Immutability of Key Parameters  *(Severity: Informational · Status: Unresolved)*

Several critical parameters such as `factory`, `pairToken`, `positionManager`, `swapRouter`, `launchTime`, `maxWalletBps`, and `restrictionSeconds` are declared as `immutable`. This means they cannot be changed after contract deployment. While this provides certainty, it also means that if any of these parameters are set incorrectly or require updates due to unforeseen circumstances (e.g., a change in the `swapRouter` address), the contract would need to be redeployed.

**Recommendation:** Ensure that all immutable parameters are thoroughly reviewed and correctly configured prior to deployment. Consider if any of these parameters might require future flexibility and, if so, make them mutable with appropriate access control and upgrade mechanisms.


### `I-02` — Centralized Control by `factory` Address  *(Severity: Informational · Status: Unresolved)*

The `factory` address, set during construction, holds significant control over the contract. It is the only address authorized to call `setPool` and `setInitialBuyRecipient`. Additionally, the `factory` address is exempt from all transfer restrictions (`_exempt` function). This centralization of control means that the security of the `factory` address is paramount, as a compromise could lead to manipulation of the liquidity pool or initial buy recipient, and unrestricted token transfers.

**Recommendation:** Implement robust security measures for the `factory` address, such as multi-signature wallet control, to mitigate the risk of a single point of failure. Clearly document the responsibilities and capabilities of the `factory` address for transparency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x018d...2bd1`](https://arbiscan.io/address/0x018d6a98555686be1ca5b6896ef6c42cf67e2bd1) |
| **Network** | Arbitrum |
| **Price** | $0.002326 |
| **24h Volume** | $379.9K |
| **Liquidity** | $198.1K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 18d |
| **Top-10 Holders** | 24.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 652 buys / 362 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0x628854f0cfd7debd6e04361421ee9c06c77048c3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/odys-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
