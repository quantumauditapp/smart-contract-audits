---
token: 翻身币税助力凉兮翻身
ticker: 翻身币
network: bsc
risk_score: 0
status: low
date: 2026-09-13
---

# 翻身币税助力凉兮翻身 (翻身币) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-beaa18-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and pool state transitions. The audit identified a critical reentrancy vulnerability in the tax liquidation logic and a high-severity issue where the contract fails to approve the tax processor, rendering a core function inoperable. Additionally, significant owner privileges and a hardcoded token supply were noted.

> **Final Recommendation:** It is imperative to address the critical reentrancy vulnerability by implementing a reentrancy guard or strictly adhering to the checks-effects-interactions pattern in the `_liquidateTax` function. The missing ERC20 approval for the `taxProcessor` must also be resolved to ensure the tax collection and processing mechanism functions as intended. Consider implementing a timelock for critical owner-controlled functions to mitigate centralization risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages OpenZeppelin's upgradeable standards (ERC20Upgradeable, OwnableUpgradeable, Initializable), providing a solid foundation for token functionality and upgrade safety (7.1… |
| **Governance / Economics** | 10/10 | Low | The contract grants the owner significant control over key economic parameters and state transitions (7.5 Governance). Functions like `startMigration` and `finalizeMigration` allow the owner to… |
| **Upgrades** | 10/10 | Low | The contract correctly implements the upgradeable pattern using OpenZeppelin's `Initializable` and `Upgradeable` contracts (7.7 Upgrades). The constructor calls `_disableInitializers()` and the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 1 Informational_

### `M-01` — High Centralization Risk with Owner Privileges  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `OwnableUpgradeable` pattern grants significant control to the contract owner. Specifically, the `startMigration` and `finalizeMigration` functions, which are `onlyOwner`, allow the owner to unilaterally change the `PoolState` of the token. These state changes directly impact the tax rates (`buyTaxRate`, `sellTaxRate`) and transfer restrictions, giving the owner considerable power over the token's economic behavior and user experience (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet for ownership or introducing a timelock mechanism for critical state-changing functions like `startMigration` and `finalizeMigration`. This would provide a delay for users to react to impending changes and reduce the risk of a single point of compromise.


### `M-02` — Reentrancy Vulnerability in _liquidateTax  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function, called during `_transfer` operations to the `mainPool`, performs external calls to `ITaxProcessor(taxProcessor).processTax` and `IDividend(dividendContract).distributeDividends`. These external calls occur before the `currentPoolState.notLiquidating` flag is reset (or before the state update that would prevent re-execution). A malicious `taxProcessor` or `dividendContract` could re-enter the `_transfer` function, triggering `_liquidateTax` again while the initial execution is still in progress. This could lead to repeated tax liquidation, draining the contract's collected tax tokens, or ot

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `_liquidateTax` function. Alternatively, strictly follow the 'checks-effects-interactions' pattern: update all relevant state variables (like `notLiquidating`) *before* making any external calls.


### `M-03` — Missing ERC20 Approval for Tax Processor  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function collects `FlapTaxTokenV3` tokens as tax into the contract's balance via `_plainTransfer(from, address(this), tax);`. Subsequently, it calls `ITaxProcessor(taxProcessor).processTax(taxAmount, quoteToken, v2Router, liqExpectedOutputAmount)`. For the `taxProcessor` to utilize these collected `FlapTaxTokenV3` tokens (e.g., to swap them), it would typically need to call `transferFrom` on the `FlapTaxTokenV3` contract. However, the `FlapTaxTokenV3` contract never approves the `taxProcessor` to spend its own tokens. This will cause the `processTax` function to fail if it attempts to `transferFrom`

**Recommendation:** The `FlapTaxTokenV3` contract must approve the `taxProcessor` to spend its own tokens. This can be done by calling `_approve(address(this), taxProcessor, type(uint256).max)` during initialization or by dynamically approving the exact `taxAmount` before calling `processTax`.


### `I-01` — Hardcoded Max Supply  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `maxSupply` variable is declared as a `public constant` with a value of `1e9 ether`. While this clearly defines the token's maximum supply, its constant nature means it cannot be modified in the future, even through upgrades. This design choice might limit flexibility if the project's tokenomics require adjustments to the total supply cap in the long term (7.4 Economic).

**Recommendation:** If future flexibility for supply adjustments is desired, consider making `maxSupply` a state variable that can be updated by governance or a privileged role, rather than a constant. If the fixed supply is an intentional and permanent design decision, no action is required.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x28cd...7777`](https://bscscan.com/address/0x28cd1fc7b6eebf46b59001ff49c9d14f8bb97777) |
| **Network** | BNB Chain |
| **Price** | $0.0002818 |
| **24h Volume** | $510.4K |
| **Liquidity** | $61.7K |
| **Volume / Liquidity** | 8.3× |
| **Token Age** | 24d |
| **Top-10 Holders** | 31.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3613 buys / 3177 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xc4a277116b384f14e7c2aa39e7498795a6f93ab3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-beaa18-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
