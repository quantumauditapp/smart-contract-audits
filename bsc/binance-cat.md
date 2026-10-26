---
token: Binance Cat
ticker: BNBCAT
network: bsc
risk_score: 0
status: low
date: 2026-08-30
---

# Binance Cat (BNBCAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/binance-cat-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with dynamic tax mechanisms and a liquidation process for collected taxes. It leverages OpenZeppelin's upgradeable contracts for a solid foundation. While a reentrancy guard is present for the liquidation process, a critical external call to an unaudited `ITaxProcessor` within a frequently executed function introduces significant risk. Additionally, a failure in this external call could permanently disable the liquidation mechanism. The contract exhibits a high degree of owner centralization for critical operations and parameter changes.

> **Final Recommendation:** Prioritize a comprehensive security audit of all external contracts interacting with FlapTaxTokenV3, especially `ITaxProcessor` and `IDividend`, to mitigate risks associated with external calls. Implement robust error handling for external calls to prevent critical contract functionality from being permanently disabled. Consider implementing multi-signature control for owner-privileged functions to reduce centralization risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes OpenZeppelin's upgradeable standards for ERC20 and Ownable, providing a robust foundation (7.1). A reentrancy guard (`notLiquidating` flag) is implemented for the tax… |
| **Governance / Economics** | 10/10 | Low | The contract's economic parameters, such as buy/sell tax rates and liquidation thresholds, are well-defined and managed through a multi-state pool system (7.4). The owner has significant control over… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's `Initializable` and `Upgradeable` contracts, ensuring future upgradeability (7.7). The `_disableInitializers()` call in… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Incomplete State Reversion on `_processTax` Failure  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `_liquidateTax` function, the `notLiquidating` flag is set to `false` before the external call to `_processTax`. If the `_processTax` call reverts for any reason (e.g., due to an issue in the `taxProcessor` or `dividendContract`), the `notLiquidating` flag will remain `false`. This would permanently prevent any future liquidations from occurring, effectively bricking the tax collection mechanism and requiring a contract upgrade to resolve.

**Recommendation:** Ensure that the `notLiquidating` flag is reset to `true` even if `_processTax` reverts. This can be achieved by wrapping the external call in a try-catch block or by ensuring the flag is reset in a `finally` block if Solidity supported it. A simpler approach is to reset the flag immediately after the external call, and if the external call reverts, the entire transaction would revert, thus reverting the flag change as well. However, if the intent is to allow the transaction to continue while ma…


### `M-02` — External Call to Untrusted `ITaxProcessor` (Truncated Code)  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, which is called on every token transfer, makes an external call to `_processTax` via the `ITaxProcessor` interface. The implementation of `_processTax` and the `ITaxProcessor` contract itself are not provided for audit. While a `notLiquidating` flag is used as a reentrancy guard for the liquidation process, the external call to an unaudited contract introduces a significant security risk. A malicious or vulnerable `ITaxProcessor` could exploit the `FlapTaxTokenV3` contract, potentially leading to unauthorized fund transfers, state manipulation, or denial of service.

**Recommendation:** Conduct a thorough security audit of the `ITaxProcessor` and `IDividend` contracts. Ensure they adhere to secure coding practices, implement necessary reentrancy guards, and handle funds and state transitions securely. Consider implementing a timelock for critical changes to external contract addresses.


### `L-01` — Unused `initialLiquidationThreshold` Variable  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialLiquidationThreshold` state variable is set during the `initialize` function but is never read or used anywhere else in the provided contract code. This variable represents dead code.

**Recommendation:** Remove the `initialLiquidationThreshold` state variable to reduce contract size, save gas on deployment, and improve code clarity. If it is intended for future use, ensure it is properly documented and integrated into the contract's logic.


### `L-02` — Potential Truncation for `liquidationThreshold`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MIN_LIQ_THRESHOLD` and `START_LIQ_THRESHOLD` are defined as `uint256`, but `poolState.liquidationThreshold` is a `uint96`. In the `initialize` function, `poolState.liquidationThreshold` is set by casting `START_LIQ_THRESHOLD` to `uint96`. While `START_LIQ_THRESHOLD` is likely to be within the `uint96` range, if a value exceeding `2^96 - 1` were ever passed, it would be truncated without warning, potentially leading to unexpected behavior or a lower-than-intended liquidation threshold.

**Recommendation:** Ensure that `START_LIQ_THRESHOLD` and `MIN_LIQ_THRESHOLD` are explicitly constrained to fit within `uint96` during initialization or parameter setting. Alternatively, consider making `poolState.liquidationThreshold` a `uint256` for consistency and to avoid potential truncation issues.


### `I-01` — Centralization Risk with Owner Privileges  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `owner` address has significant control over critical contract functions, including `startMigration`, `finalizeMigration`, and setting key external contract addresses (`v2Router`, `taxProcessor`, `dividendContract`, `pools`) during initialization. This centralization introduces a single point of failure, as a compromised owner key could lead to malicious state changes, manipulation of tax parameters, or redirection of funds.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` address to distribute control and reduce the risk associated with a single point of failure. For highly sensitive operations, a timelock mechanism could be introduced to provide a delay before changes take effect, allowing for community review or emergency intervention.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3efb...7777`](https://bscscan.com/address/0x3efbfff95576e1d23cf6ead0acd2e73f4d6a7777) |
| **Network** | BNB Chain |
| **Price** | $0.002749 |
| **24h Volume** | $1.27M |
| **Liquidity** | $217.7K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 7d |
| **Top-10 Holders** | 17.7% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 2865 buys / 2234 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x8650e3ede7c2d45f89dbbe108bd6568f414167cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/binance-cat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
