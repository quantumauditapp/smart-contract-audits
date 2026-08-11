---
token: ICP
ticker: ICP
network: ethereum
risk_score: 59
status: high
date: 2026-08-11
---

# ICP (ICP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/icp-eth)

---

## Audit Summary

The Token contract implements a standard ERC20 token with Ownable and ERC20Permit extensions. It includes custom burn and mint functionalities. The audit identified a High severity issue related to incorrect ETH withdrawal logic, and several Medium severity issues concerning unchecked external calls and inconsistent ETH handling in batch minting. Owner privileges are significant, allowing for centralized control over token supply and contract funds.

> **Final Recommendation:** It is crucial to immediately address the `withdrawEth` function's logic to prevent funds from being permanently locked. Implement robust error handling for all external calls, specifically checking the `success` boolean and considering higher gas limits where appropriate. Review the `batchMint` function's ETH handling to ensure consistency and prevent stuck funds. Consider the implications of centralized owner control and explore options for multi-signature ownership or time-locks for critical operations if decentralization is a future goal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin libraries for ERC20, Ownable, and ERC20Permit functionalities (7.2 Code Security). However, a critical flaw exists in the `withdrawEth` function… |
| **Governance / Economics** | 1/10 | High | The contract utilizes the Ownable pattern, granting the deployer significant control over key functions such as minting, updating `minAmount`, and withdrawing ETH (7.3 Access Control). This… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism (e.g., proxy pattern), which inherently avoids the complexities and potential security risks associated with upgradeable contracts (7.7… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Incorrect `withdrawEth` Logic Leads to Locked Funds  *(Severity: High · Status: Unresolved)*

The `withdrawEth` function contains an inverted `require` condition: `require(amount >= address(this).balance, "Balance too low");`. This condition incorrectly checks if the requested `amount` is greater than or equal to the contract's balance. As a result, the function will only succeed if `amount` is exactly equal to `address(this).balance`, or it will revert if `amount` is less than the balance. If `amount` is greater than the balance, the `require` passes, but the subsequent `transfer` call will revert due to insufficient funds. This effectively prevents the owner from withdrawing partial amounts of ETH and can lead to funds being locked in the contract if the owner attempts to withdraw…

**Recommendation:** Correct the `require` condition to `require(amount <= address(this).balance, "Amount exceeds contract balance");` to allow the owner to withdraw any amount up to the contract's current ETH balance.


### `M-01` — Unchecked `call` Return Values and Low Gas Limit in Mint Functions  *(Severity: Medium · Status: Unresolved)*

The `mint` and `batchMint` functions perform external ETH transfers using `to.call{value: msg.value, gas: 2300}("")` and `recipients[i].call{value: ethAmounts[i], gas: 2300}("")` respectively. The `success` boolean returned by these `call` operations is not checked. If an external call fails (e.g., due to the recipient being a contract that reverts, or running out of gas), the transaction will still proceed, leading to a situation where the ETH was not transferred but the caller believes it was. Additionally, the fixed gas limit of 2300 is very low and might be insufficient for complex recipient contracts, causing legitimate transfers to fail.

**Recommendation:** Always check the `success` boolean returned by external `call` operations and revert if `success` is false. Consider increasing the gas limit for external calls if the recipient is expected to be a contract with complex fallback logic, or remove the gas limit entirely if reentrancy is not a concern (which it is not here, as ETH is sent out after internal state changes). For example: `(bool success,) = to.call{value: msg.value}(''); require(success, 'ETH transfer failed');`


### `M-02` — Inconsistent ETH Handling in `batchMint` Function  *(Severity: Medium · Status: Unresolved)*

The `batchMint` function's logic for handling `msg.value` and `ethAmounts` is inconsistent. If `msg.value > 0`, the function iterates through `ethAmounts` to transfer ETH to recipients. However, there is no check to ensure that `msg.value` matches the sum of `ethAmounts`. If `msg.value` is greater than the sum of `ethAmounts`, the excess ETH will remain stuck in the contract. If `msg.value` is less than the sum of `ethAmounts`, some `call` operations will revert due to insufficient balance, leading to partial failures and an inconsistent state where some recipients receive ETH and others do not, while all tokens might still be minted.

**Recommendation:** Implement a clear strategy for `msg.value` in `batchMint`. Either require `msg.value` to be exactly equal to the sum of `ethAmounts` (e.g., by calculating the sum and comparing), or explicitly define how excess or insufficient `msg.value` should be handled (e.g., refund excess, revert on insufficient).


### `L-01` — High Centralization of Owner Privileges  *(Severity: Low · Status: Unresolved)*

The contract grants significant power to the `owner` address, including the ability to mint an unlimited supply of tokens to any address, update the `minAmount` for burning, and withdraw all ETH from the contract. While this is a common pattern for `Ownable` contracts, it introduces a high degree of centralization and reliance on the owner's integrity. A compromised owner key could lead to severe consequences, such as arbitrary token minting or draining of contract funds.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to reduce the risk of a single point of failure. For critical operations like minting or updating core parameters, explore adding time-locks or a governance mechanism to introduce delays and community oversight.


### `I-01` — Redundant Burn Functions  *(Severity: Informational · Status: Unresolved)*

The contract defines four separate `burn` functions (`burn1`, `burn2`, `burn3`, `burn4`) that are identical in functionality except for the number of `bytes32` data parameters they accept. This design choice leads to code duplication and unnecessary complexity without providing distinct functional benefits that couldn't be achieved with a single, more flexible `burn` function (e.g., accepting a `bytes` array or a single `bytes` parameter).

**Recommendation:** Consolidate the multiple `burn` functions into a single function that accepts a dynamic `bytes` array or a single `bytes` parameter for arbitrary data. This would reduce code duplication, improve readability, and simplify maintenance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x00f3...8917`](https://etherscan.io/address/0x00f3c42833c3170159af4e92dbb451fb3f708917) |
| **Network** | Ethereum |
| **Price** | $2.3000 |
| **24h Volume** | $764.6K |
| **Liquidity** | $460.9K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 59.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 565 buys / 526 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4068038ab5490063a3ead93b3712ed082e62bd59)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/icp-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
