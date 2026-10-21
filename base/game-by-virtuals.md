---
token: GAME by Virtuals
ticker: GAME
network: base
risk_score: 71
status: high
date: 2026-08-30
---

# GAME by Virtuals (GAME) — Smart Contract Security Analysis | Base

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/game-by-virtuals-base)

---

## Audit Summary

The AgentToken contract implements a custom ERC20-like token with tax mechanisms, bot protection, and Uniswap V2 integration. The contract uses OpenZeppelin's upgradeable patterns and 2-step ownership. A critical issue was identified regarding the absence of core ERC20 transfer functions in the provided code, rendering it non-functional as a standard token. Additionally, significant centralization risks exist due to the `onlyOwnerOrFactory` modifier.

> **Final Recommendation:** Address the critical issue of missing ERC20 core functions to ensure the token is functional and compliant with the standard. Review the extent of centralized control granted by the `onlyOwnerOrFactory` modifier and consider implementing a more decentralized governance model or multi-signature wallet for critical operations to mitigate single points of failure. Implement robust testing for all token functionalities, especially the tax and bot protection mechanisms, once the full code is available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages OpenZeppelin's upgradeable patterns and `EnumerableSet` for efficient management of liquidity pools and valid callers (7.1 Architecture). However, a critical functional flaw… |
| **Governance / Economics** | 1/10 | High | The contract's economic model includes buy and sell taxes, and an auto-swap mechanism for tax collection, which are common in DeFi (7.4 Economic). However, the `onlyOwnerOrFactory` modifier grants… |
| **Upgrades** | 1/10 | High | The contract correctly implements OpenZeppelin's `Initializable` pattern, including `_disableInitializers()` in the constructor and an `initialize` function, ensuring proper upgrade safety (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 67.3% |
| **Top-3 Unlocked** | ⚠️ 92.9% |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Incomplete ERC20 Implementation (Missing Core Functions)  *(Severity: Critical · Status: Unresolved)*

The `AgentToken` contract defines private state variables for `_balances`, `_allowances`, `_totalSupply`, `_name`, and `_symbol`, which are typical for an ERC20 token. However, the public ERC20 interface functions such as `transfer`, `transferFrom`, `approve`, `allowance`, `balanceOf`, and `decimals` are not present in the provided code snippet. While `IAgentToken` is imported, its interface is not shown, and the implementation of these critical functions is absent, rendering the token non-functional as a standard ERC20.

**Recommendation:** Implement all standard ERC20 functions (`transfer`, `transferFrom`, `approve`, `allowance`, `balanceOf`, `decimals`, `totalSupply`) to ensure the token is fully functional and compliant with the ERC20 standard. Ensure these implementations correctly interact with the private state variables.


### `M-01` — Centralization Risk with `onlyOwnerOrFactory` Modifier  *(Severity: Medium · Status: Unresolved)*

The `onlyOwnerOrFactory` modifier grants significant control to the contract owner and the `_factory` contract. Functions such as `addLiquidityPool`, `removeLiquidityPool`, `addValidCaller`, `removeValidCaller`, `setProjectTaxRecipient`, and `setSwapThresholdBasisPoints` can be modified by these entities. This centralizes control over key operational parameters, including liquidity management, tax recipients, and auto-swap thresholds, posing a single point of failure and potential for misuse.

**Recommendation:** Consider decentralizing control for critical functions by implementing a multi-signature wallet for the owner address or integrating a governance mechanism. For less critical functions, evaluate if the `_factory` contract's role can be limited or if a time-lock mechanism should be introduced for sensitive parameter changes.


### `L-01` — Potential for Slippage and MEV in Initial Liquidity Provision  *(Severity: Low · Status: Unresolved)*

The `_addInitialLiquidity` function adds liquidity to Uniswap V2 using `_uniswapRouter.addLiquidity`. While protected by `onlyOwnerOrFactory`, the `minAmountA` and `minAmountB` parameters are set to 0. This allows for arbitrary slippage during the liquidity addition. If the transaction is public, a sophisticated attacker could potentially front-run or sandwich this transaction, especially if the `pairToken` is volatile or the initial liquidity provision is substantial, leading to unfavorable exchange rates for the liquidity provider.

**Recommendation:** Set reasonable minimum amounts for `minAmountA` and `minAmountB` in the `addLiquidity` call to protect against excessive slippage. Consider using a private transaction relay or a trusted third party for initial liquidity provision to mitigate MEV risks.


### `I-01` — Truncated Code Prevents Full Audit  *(Severity: Informational · Status: Unresolved)*

The provided contract text for `AgentToken` is truncated. Critical sections of the contract, including the full implementation of ERC20 transfer functions, tax calculation and auto-swap logic (`_swapAndSendTax`), and bot protection mechanisms, are missing. This prevents a comprehensive security analysis of the entire contract's functionality and potential interactions.

**Recommendation:** Provide the complete and unabridged source code for all contracts intended for audit to enable a thorough and accurate security assessment.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1c4c...63a3`](https://basescan.org/address/0x1c4cca7c5db003824208adda61bd749e55f463a3) |
| **Network** | Base |
| **Price** | $0.007092 |
| **24h Volume** | $134.5K |
| **Liquidity** | $2.64M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 48.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 49 buys / 100 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd418dfe7670c21f682e041f34250c114db5d7789)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/game-by-virtuals-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
