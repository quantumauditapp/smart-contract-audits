---
token: ICP
ticker: ICP
network: base
risk_score: 58
status: high
date: 2026-08-15
---

# ICP (ICP) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/icp-base)

---

## Audit Summary

The Token contract implements an ERC20 token with custom burning, minting, and ETH withdrawal functionalities, leveraging OpenZeppelin's ERC20, Ownable, and ERC20Permit standards. While the contract benefits from well-tested OpenZeppelin components and clear access control for critical operations, a significant logical error in the `withdrawEth` function severely restricts the owner's ability to manage contract ETH. Additionally, unchecked external call results in minting functions pose a risk of silent failures, and several code redundancies were identified.

> **Final Recommendation:** It is highly recommended to address the critical logical error in the `withdrawEth` function to ensure proper management of contract funds. Implement robust error handling for all external calls, particularly for ETH transfers, to prevent silent failures and ensure transaction integrity. Review and refactor redundant code, such as the multiple `burn` functions, to improve efficiency and maintainability. Consider the implications of the low gas limit on external calls for potential future interactions with complex smart contract recipients.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust OpenZeppelin libraries for ERC20, Ownable, and ERC20Permit, providing a solid foundation for token functionality (7.2 Code Security). Access control for minting, ETH… |
| **Governance / Economics** | 1/10 | High | The contract's economic model is straightforward, with an owner-controlled `minAmount` for burning and owner-only minting capabilities (7.4 Economic). The `Ownable` pattern provides clear… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), meaning its logic is immutable once deployed (7.7 Upgrades). This eliminates upgrade-specific risks such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 51.2% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Critical Logic Error in `withdrawEth` Function  *(Severity: High · Status: Unresolved)*

The `withdrawEth` function contains a logical error in its `require` statement: `require(amount >= address(this).balance, "Balance too low");`. This condition incorrectly checks if the requested `amount` is greater than or equal to the contract's total ETH balance. As a result, the owner can only successfully withdraw the *exact total balance* of the contract, or attempts to withdraw more will revert due to insufficient funds during the `transfer` call. This prevents the owner from withdrawing partial amounts of ETH, severely hindering fund management.

**Recommendation:** Change the `require` statement to `require(amount <= address(this).balance, "Amount exceeds contract balance");` to allow the owner to withdraw any amount up to the contract's current ETH balance.


### `M-01` — Unchecked Return Value from External Calls  *(Severity: Medium · Status: Unresolved)*

The `mint` and `batchMint` functions perform external ETH transfers using `to.call{value: msg.value, gas: 2300}("")` and `recipients[i].call{value: ethAmounts[i], gas: 2300}("")` respectively. While the `success` boolean is assigned, it is not checked (`success;`). If the external call fails (e.g., the recipient contract reverts or runs out of the provided gas), the transaction will continue without reverting, potentially leading to a loss of ETH or an inconsistent state where tokens are minted but ETH is not transferred.

**Recommendation:** Always check the `success` boolean returned by low-level `call` functions and revert if the call was unsuccessful. For example: `(bool success,) = to.call{value: msg.value, gas: 2300}(""); require(success, "ETH transfer failed");`


### `L-01` — Redundant `burn` Functions  *(Severity: Low · Status: Unresolved)*

The contract includes four separate `burn` functions (`burn1`, `burn2`, `burn3`, `burn4`) that differ only by the number of `bytes32` data parameters they accept. The core logic within each function (checking `minAmount`, calling `_burn`, and emitting an event) is identical. This redundancy increases contract size, deployment costs, and reduces code maintainability without adding unique functionality.

**Recommendation:** Consolidate these functions into a single `burn` function that accepts a dynamic array of `bytes32` or a single `bytes` parameter for the data, allowing for more flexible and efficient burning operations. For example: `function burn(uint256 amount, bytes calldata data) public { ... emit Burn(msg.sender, amount, data); }`


### `I-01` — Low Gas Limit for External ETH Transfers  *(Severity: Informational · Status: Unresolved)*

The `mint` and `batchMint` functions use a fixed `gas: 2300` limit for external ETH transfers via `call`. While this low gas limit helps prevent reentrancy attacks, it also severely restricts the amount of computation a recipient smart contract can perform in its `receive` or `fallback` function. If a recipient contract requires more than 2300 gas to process the incoming ETH, the transfer will fail.

**Recommendation:** Ensure that all intended recipients of ETH transfers are either EOAs or simple smart contracts that can handle incoming ETH with minimal gas. If interaction with complex smart contracts is expected, consider increasing the gas limit or using a different transfer mechanism, while carefully mitigating reentrancy risks.


### `I-02` — Redundant `_decimals` Storage Variable  *(Severity: Informational · Status: Unresolved)*

The contract declares a `uint8 _decimals;` storage variable and sets it in the constructor. It then overrides the `decimals()` function to return this custom `_decimals`. While functional, the `ERC20` base contract from OpenZeppelin already manages an internal `_decimals` variable (defaulting to 18 if not specified). This creates a slight redundancy where the base contract's `_decimals` might be initialized but then ignored in favor of the custom one.

**Recommendation:** To avoid potential confusion or redundancy, consider if the custom `_decimals` variable is strictly necessary. If the intent is to simply set the decimals for the ERC20 token, it can often be done by passing the desired decimals to the `ERC20` constructor directly if it supports it, or by ensuring the overridden `decimals()` function correctly interacts with the inherited `_decimals` if it's exposed or intended to be used.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x00f3...8917`](https://basescan.org/address/0x00f3c42833c3170159af4e92dbb451fb3f708917) |
| **Network** | Base |
| **Price** | $2.2700 |
| **24h Volume** | $315.1K |
| **Liquidity** | $418.6K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 73.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 914 buys / 960 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xbe762d548f8ca86a78e9da6e3ddc87f91457e398)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/icp-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
