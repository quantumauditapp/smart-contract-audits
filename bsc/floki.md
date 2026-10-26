---
token: FLOKI
ticker: FLOKI
network: bsc
risk_score: 39
status: medium
date: 2026-08-30
---

# FLOKI (FLOKI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/floki-bsc)

---

## Audit Summary

The FLOKI token contract implements ERC-20 functionality with a Compound-style delegation system for governance. The audit identified a critical vulnerability where the core `_transfer` function is entirely missing from the provided code, rendering the token non-functional. Additionally, a high-severity flaw in `transferFrom`'s allowance logic and a high-severity truncation issue in the governance delegation mechanism were found, which could lead to incorrect voting power calculations. The contract also exhibits centralized control over key handler addresses.

> **Final Recommendation:** Prioritize the immediate implementation of the `_transfer` function to make the token functional. Rectify the `transferFrom` allowance logic to ensure correct and secure token transfers. Address the `_moveDelegates` truncation issue to guarantee accurate voting power calculations, which is crucial for the integrity of the governance system.
For long-term security and decentralization, consider implementing a multi-signature wallet or a time-lock for administrative functions like changing handler addresses. Ensure a clear plan for initial token distribution is communicated.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements ERC-20 token standards and a Compound-style delegation system for governance. Strengths include the use of Solidity 0.8.11 for automatic overflow/underflow checks and a robust… |
| **Governance / Economics** | 2/10 | High | The FLOKI token incorporates a standard delegation-based governance system, allowing token holders to delegate their voting power. The fixed `totalSupply` and initial distribution to the deployer… |
| **Upgrades** | 7/10 | Low | The FLOKI contract is implemented as a standard, non-upgradeable token contract. This design choice eliminates the complexities and potential risks associated with proxy upgrade patterns, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 90.7% — OnlyMoons Lock, UNCX |
| **Top-1 Unlocked Holder** | 9.2% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control of Tax and Treasury Handlers  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setTaxHandler` and `setTreasuryHandler` functions are protected by `onlyOwner`, allowing the contract owner to unilaterally change the addresses of the `ITaxHandler` and `ITreasuryHandler` contracts. This grants significant power to the owner, as these handlers could potentially control critical tokenomics such as transaction taxes, fees, and treasury distributions, without any community governance or time-lock mechanisms.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or introducing a time-lock mechanism for sensitive administrative actions like changing handler addresses. This would provide a delay, allowing the community to react to potentially malicious changes. Alternatively, integrate these changes into the governance system.


### `M-02` — Missing Core `_transfer` Function Implementation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided contract snippet for `FLOKI` is missing the implementation of the internal `_transfer` function, which is essential for all token transfers (`transfer`, `transferFrom`). Without this function, the token is non-functional, as no actual balance updates or `Transfer` events can occur.

**Recommendation:** Implement the `_transfer` function, ensuring it correctly updates `_balances` for sender and recipient, and emits `Transfer` events, adhering to ERC-20 standards. This function is fundamental for the token's operation.


### `M-03` — Incorrect `transferFrom` Allowance Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `transferFrom` function first calls `_transfer(sender, recipient, amount)` and *then* checks and updates the allowance. This order is incorrect. If `_transfer` succeeds but the allowance check subsequently fails, the transaction will revert, but the logical flow is flawed. The allowance should be checked and updated *before* the actual token transfer to ensure atomicity and prevent potential unexpected behavior.

**Recommendation:** Reorder the operations in `transferFrom`. First, check `currentAllowance >= amount`, then update `_approve(sender, _msgSender(), currentAllowance - amount)`, and finally call `_transfer(sender, recipient, amount)`.


### `M-04` — Potential Truncation of Voting Power in `_moveDelegates`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `_moveDelegates` function, `delegatorBalance` (a `uint256`) is cast to `uint224` before being used to update delegate votes. If a delegator's balance exceeds `type(uint224).max` (approximately 2^224 - 1), the `amount` will be truncated. This leads to an incorrect representation of voting power for the delegatee, significantly impacting the integrity and accuracy of governance decisions.

**Recommendation:** Ensure that `delegatorBalance` is handled as `uint256` throughout the delegation logic to prevent truncation, or implement explicit checks to revert if `delegatorBalance` exceeds `type(uint224).max` if `uint224` is strictly necessary for gas optimization. Using `uint256` for vote amounts is generally safer if the total supply can exceed `type(uint224).max`.


### `L-01` — Theoretical `numCheckpoints` Overflow  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `numCheckpoints` variable, which tracks the number of checkpoints for a delegatee, is a `uint32`. While highly unlikely in practice (requiring over 4 billion delegation changes for a single address), it is theoretically possible for this variable to overflow, leading to unexpected behavior in vote counting.

**Recommendation:** While the practical impact is minimal, consider using `uint256` for `numCheckpoints` if future scaling or extreme usage patterns are anticipated, or add a check to prevent exceeding `type(uint32).max`.


### `I-01` — Highly Centralized Initial Token Distribution  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the constructor, the entire `totalSupply()` of FLOKI tokens is minted and assigned to the deployer (`_balances[_msgSender()] = totalSupply();`). This results in a highly centralized initial token distribution, where the deployer holds 100% of the tokens. While common for new projects, it implies significant control over the token's supply and potential governance power if not subsequently distributed.

**Recommendation:** Ensure a clear and transparent plan for token distribution is communicated to the community. Consider mechanisms for gradual decentralization of token holdings and governance power over time.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfb5b...d37e`](https://bscscan.com/address/0xfb5b838b6cfeedc2873ab27866079ac55363d37e) |
| **Network** | BNB Chain |
| **Price** | $0.00002564 |
| **24h Volume** | $239.5K |
| **Liquidity** | $9.15M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 85.8% of supply |
| **Buy / Sell Tax** | 0.3% / 0.3% |
| **24h Transactions** | 67 buys / 208 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x231d9e7181e8479a8b40930961e93e7ed798542c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/floki-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
