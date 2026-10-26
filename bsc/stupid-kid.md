---
token: Stupid Kid
ticker: 傻孩子
network: bsc
risk_score: 29
status: low
date: 2026-09-03
---

# Stupid Kid (傻孩子) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stupid-kid-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract is an upgradeable ERC20 token designed with a dynamic tax mechanism, multiple pool states, and anti-farmer features. It utilizes OpenZeppelin's upgradeable contracts for security and maintainability. The contract implements a system where transfers can incur taxes, which are then collected and processed by external `ITaxProcessor` or `IDividend` contracts. While the architecture is well-structured, significant centralization of control by the owner and potential reentrancy vectors in the tax liquidation mechanism introduce notable risks. Gas efficiency for transfers could also be a concern due to the `_liquidateTax` call on every transfer.

> **Final Recommendation:** It is highly recommended to implement robust multi-signature or time-locked mechanisms for critical owner-controlled functions to mitigate the risks associated with centralized control. Thoroughly review and secure the external `ITaxProcessor` and `IDividend` contracts, as their security directly impacts the token. Consider implementing a reentrancy guard on the `_liquidateTax` function or re-architecting the external calls to prevent potential reentrancy attacks. Evaluate the gas costs associated with `_liquidateTax` under various scenarios to ensure user experience is not negatively impacted.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good technical practices, leveraging OpenZeppelin's upgradeable standards for ERC20 functionality and proxy patterns (7.1 Architecture). The use of `PackedPoolState` for… |
| **Governance / Economics** | 6/10 | Medium | The contract's economic model includes dynamic tax rates and pool states, managed through owner-controlled functions, which allows for flexibility in adapting to market conditions (7.4 Economic). The… |
| **Upgrades** | 4/10 | Medium | The contract correctly implements the upgradeable pattern using OpenZeppelin's `Initializable` and `ERC20Upgradeable` contracts (7.7 Upgrades). The constructor disables initializers, and the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Reentrancy Risk in `_liquidateTax` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, which is called on every `_transfer`, makes external calls to `ITaxProcessor(taxProcessor).processTax()` or `IDividend(dividendContract).processDividend()`. While the `balanceOf(address(this))` check occurs before the external call, the `poolState` variable is updated *after* the external call if a state transition is triggered by `block.timestamp`. A malicious `taxProcessor` or `dividendContract` could potentially reenter the `FlapTaxTokenV3` contract, triggering `_transfer` and subsequently `_liquidateTax` again. This could lead to `processTax` being called multiple times with the same `

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function or ensure that all state changes related to the tax balance and pool state are completed *before* any external calls are made. Follow the 'Checks-Effects-Interactions' pattern strictly.


### `M-02` — Potential for High Gas Costs on Transfers  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is invoked on every `_transfer` operation. This function includes logic for checking `block.timestamp` for state transitions and potentially making external calls to `ITaxProcessor` or `IDividend` contracts. If these external contracts perform complex operations, or if the conditions for processing tax/dividends are frequently met, the gas cost for standard token transfers could become unexpectedly high. This might negatively impact user experience and could lead to transaction failures during periods of high network congestion (7.8 Operations).

**Recommendation:** Evaluate the gas consumption of `_liquidateTax` and its external calls under various scenarios. Consider optimizing the logic within `_liquidateTax` or the external contracts to minimize gas usage. Alternatively, explore alternative mechanisms for triggering tax processing (e.g., a dedicated `processTax` function that users or a bot can call, rather than on every transfer) to decouple it from basic token transfers.


### `M-03` — Excessive Centralization of Control by Owner  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract grants extensive control to the `owner` over critical parameters and state transitions. Functions such as `setTaxProcessor`, `setDividendContract`, `setPoolState`, `startMigration`, `finalizeMigration`, and `setLiquidationThreshold` are all protected by the `onlyOwner` modifier. A compromised or malicious owner could manipulate tax rates, block transfers, change the operational state of the token, or redirect accumulated tax funds to a malicious address, leading to significant financial loss or protocol disruption. This introduces a single point of failure for the protocol (7.3 Access Control, 7.5 Governan

**Recommendation:** Implement a multi-signature wallet for ownership or introduce a time-lock mechanism for critical administrative actions. This would require multiple approvals or a delay period before changes take effect, reducing the risk of a single point of compromise. Consider decentralizing some parameters or introducing a governance mechanism for key decisions.


### `L-01` — Fixed `liqExpectedOutputAmount` for Tax Processing  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `liqExpectedOutputAmount` parameter, used in the `ITaxProcessor(taxProcessor).processTax(taxAmount, liqExpectedOutputAmount)` call, is set as an immutable value during initialization. This fixed value might not always be optimal or realistic for the actual output of the tax processing, especially in volatile market conditions or if the `taxProcessor`'s logic changes over time. This could lead to slippage or inefficient tax processing if the `ITaxProcessor` relies heavily on this parameter for its operations (7.4 Economic).

**Recommendation:** Consider making `liqExpectedOutputAmount` configurable by the owner (with appropriate access control and perhaps a time-lock) or allowing the `ITaxProcessor` to determine its own expected output based on current market conditions. This would provide greater flexibility and potentially improve the efficiency of the tax processing mechanism.


### `I-01` — Heavy Reliance on External Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FlapTaxTokenV3` contract heavily relies on external contracts, specifically `ITaxProcessor` and `IDividend`, for critical tax and dividend processing. The security, correctness, and availability of these external contracts are paramount to the overall functionality and security of the token. Any vulnerabilities, malicious behavior, or operational failures in these external contracts could directly impact the `FlapTaxTokenV3` token and its users (7.6 External).

**Recommendation:** Ensure that the `ITaxProcessor` and `IDividend` contracts undergo rigorous security audits and are maintained to the highest security standards. Implement robust monitoring for these external contracts. Consider adding mechanisms to pause or change these external contract addresses in case of an emergency, protected by multi-signature or time-lock.


### `I-02` — Dividend Processing in `TaxFree` State  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `_liquidateTax` function, if the `PoolState` transitions to `TaxFree`, any accumulated `taxAmount` (balance of `address(this)`) is sent to `IDividend(dividendContract).processDividend()`. While this is likely intended as a cleanup mechanism for previously collected taxes, the term 'TaxFree' might be misleading to users if funds are still being processed as 'dividends' from past taxes. This could lead to a slight misunderstanding of the contract's current operational state (7.4 Economic).

**Recommendation:** Clarify the documentation or comments within the code to explicitly state that 'TaxFree' refers to new transfers not incurring tax, but previously collected taxes may still be processed as dividends. This improves transparency and user understanding of the contract's behavior.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4062...7777`](https://bscscan.com/address/0x4062083510f67d28844df9371244e6f191b97777) |
| **Network** | BNB Chain |
| **Price** | $0.0002357 |
| **24h Volume** | $683.8K |
| **Liquidity** | $53.2K |
| **Volume / Liquidity** | 12.8× |
| **Token Age** | 3d |
| **Top-10 Holders** | 29.2% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1830 buys / 1452 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf5ae54c4e622e12717ff8b12a8af6e3be1c83334)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stupid-kid-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-03*
