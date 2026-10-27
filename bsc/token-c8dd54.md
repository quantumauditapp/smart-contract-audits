---
token: 全新托底+销毁分红+强大生态
ticker: 招财猫
network: bsc
risk_score: 6
status: low
date: 2026-09-15
---

# 全新托底+销毁分红+强大生态 (招财猫) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-c8dd54-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and multiple pool states. The audit identified a potential critical reentrancy vulnerability within the `_liquidateTax` function, which is called on every transfer, due to incomplete code. Other findings include centralized owner control, reliance on `block.timestamp` for critical state transitions, and potential issues with unhandled external contract failures. The contract utilizes OpenZeppelin's upgradeable standards, which is a strong foundation, but the custom logic introduces specific risks.

> **Final Recommendation:** Prioritize a comprehensive review and completion of the `_liquidateTax` function's logic, specifically focusing on implementing robust reentrancy protection before any external calls. Consider adding a reentrancy guard to this function to prevent potential fund drains. Evaluate the impact of `block.timestamp` reliance for critical state changes and consider alternative mechanisms if miner manipulation poses a significant threat to the protocol's economics. Finally, ensure that all external calls to `ITaxProcessor` and `IDividend` are handled with appropriate error checking and gas considerations to maintain system stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20 and access control modules, providing a robust and well-tested foundation (7.2 Code Security). State management through the `PoolState` enum… |
| **Governance / Economics** | 5/10 | Medium | The contract's economic model includes dynamic buy/sell taxes and multiple pool states (7.4 Economic), which are clearly defined and managed. Critical state transitions, such as `startMigration` and… |
| **Upgrades** | 10/10 | Low | The contract is designed as an upgradeable proxy, correctly inheriting from `Initializable` and using OpenZeppelin's upgradeable contracts (7.7 Upgrades). The constructor correctly calls… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `onlyOwner` modifier grants significant control over critical functions such as `startMigration` and `finalizeMigration`, which directly change the `PoolState` and affect tax enforcement. While common for initial contract phases, this centralizes power and introduces a single point of failure or attack vector if the owner's private key is compromised. This level of control could also be a governance risk in the long term.

**Recommendation:** Consider implementing a multi-signature wallet for ownership or transitioning to a more decentralized governance model as the protocol matures. If a single owner remains, ensure robust security practices for the owner's private key.


### `M-02` — Reliance on `block.timestamp` for Critical State Transitions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function uses `block.timestamp` to determine `taxExpirationTime` and `antiFarmerExpirationTime`, which trigger changes in the `PoolState` (e.g., to `TaxFree` or `TaxEnforced`). While `block.timestamp` is generally suitable for expiration checks, miners can manipulate it within a certain range (e.g., up to 900 seconds on Ethereum, similar on BSC). This could allow a miner to prematurely trigger or delay state transitions, potentially affecting tax collection or anti-farmer mechanisms.

**Recommendation:** For time-sensitive operations where miner manipulation could have significant economic impact, consider using `block.number` in conjunction with an average block time, or an oracle for time if higher precision and resistance to manipulation are required. For simple expiration checks, `block.timestamp` is often acceptable, but the impact of potential manipulation should be thoroughly assessed.


### `M-03` — Reentrancy Risk in `_liquidateTax` (Incomplete Logic)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called on every `_transfer` and is responsible for handling accumulated tax tokens. While the provided code is truncated, the function's name and the presence of `taxProcessor` and `dividendContract` strongly suggest it performs external token transfers to these addresses. If these external calls are made before updating the contract's internal state (e.g., zeroing out the accumulated tax balance or setting a reentrancy guard), a malicious `taxProcessor` or `dividendContract` (or a contract that receives tokens from them) could re-enter the `_transfer` function. This could lead to multip

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on `_liquidateTax` or ensure that all state updates related to tax liquidation are completed *before* any external calls are made. Additionally, consider using a 'checks-effects-interactions' pattern. A full review of the complete `_liquidateTax` logic is required to confirm and mitigate this risk.


### `L-01` — Unhandled External Contract Failures in `_liquidateTax`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The truncated `_liquidateTax` function likely interacts with `ITaxProcessor` and `IDividend` for distributing accumulated tax. If these external calls revert or fail silently (e.g., due to gas limits, unexpected logic in the external contract, or reentrancy guards in the recipient), the `_liquidateTax` function might not complete its intended operations. This could leave accumulated tax funds stuck in the contract or lead to an inconsistent state regarding tax distribution, even though `SafeERC20` is used for token transfers.

**Recommendation:** Implement explicit error handling for external calls within `_liquidateTax` using `try/catch` blocks. This allows the contract to gracefully handle failures, log events, or revert the transaction if the tax distribution is critical for state consistency. Ensure sufficient gas is forwarded for external calls.


### `I-01` — Potential Gas Limit Issues for `_transfer`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called on every `_transfer` and involves multiple state updates and potentially external calls (to `taxProcessor` and `dividendContract`). If the liquidation logic is complex or involves many operations, there's a risk that a `_transfer` operation could exceed the block gas limit under certain conditions, especially if the accumulated `taxAmount` is large and requires many operations for distribution. This could lead to failed transactions for users.

**Recommendation:** Monitor gas usage of `_transfer` and `_liquidateTax` functions under various scenarios, especially with large tax amounts and multiple external recipients. Optimize the liquidation logic to minimize gas consumption. Consider implementing a separate, owner-triggered function for liquidation if the complexity or gas cost becomes prohibitive for regular transfers, or batching liquidation operations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x59cd...7777`](https://bscscan.com/address/0x59cd31a3607055e6e2d635f6c17a59d789a17777) |
| **Network** | BNB Chain |
| **Price** | $0.005048 |
| **24h Volume** | $803.7K |
| **Liquidity** | $217.3K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 93.8% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 2963 buys / 1686 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x75edf59891509fcf12bd90243c6a531acf89c5cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-c8dd54-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
