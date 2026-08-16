---
token: Ethy AI by Virtuals
ticker: ETHY
network: base
risk_score: 60
status: high
date: 2026-08-16
---

# Ethy AI by Virtuals (ETHY) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ethy-ai-by-virtuals-base)

---

## Audit Summary

The AgentToken contract implements an ERC20-like token with custom tax mechanisms, bot protection, and Uniswap V2 integration. It utilizes OpenZeppelin's upgradeable patterns and a centralized access control model via an owner and a factory address. The provided code snippet is incomplete, lacking core ERC20 transfer logic and the full implementation of tax and bot protection mechanisms, which limits a comprehensive security assessment.

> **Final Recommendation:** It is crucial to complete the ERC20 implementation and thoroughly review the `_beforeTokenTransfer` function, especially concerning reentrancy prevention and the bot protection mechanism. Ensure the deployment process for `initialize` is secure, particularly for setting the `_factory` address. Consider implementing a multi-signature wallet for the owner address to mitigate centralized control risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good practices in using OpenZeppelin upgradeable components and `EnumerableSet` for managing dynamic lists (7.1 Architecture). Access control is robustly implemented with… |
| **Governance / Economics** | 2/10 | High | The contract centralizes significant control over economic parameters (tax rates, recipient, swap threshold) to the owner and a factory address via the `onlyOwnerOrFactory` modifier (7.4 Economic… |
| **Upgrades** | 6/10 | Medium | The contract is designed for upgradeability, correctly using `Initializable` and `_disableInitializers()` in the constructor (7.7 Upgrades). It also employs `Ownable2StepUpgradeable` for secure… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by Owner/Factory  *(Severity: High · Status: Unresolved)*

The `onlyOwnerOrFactory` modifier grants significant control over critical contract parameters to a single owner address and a single factory address. This includes setting tax rates (`setProjectTaxRecipient`, `setSwapThresholdBasisPoints`), managing liquidity pools (`addLiquidityPool`, `removeLiquidityPool`), and controlling valid callers (`addValidCaller`, `removeValidCaller`). This high degree of centralization introduces a single point of failure, making the protocol vulnerable to a compromised or malicious owner/factory.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to distribute control and require multiple approvals for critical operations. For the factory role, ensure the factory contract itself has robust security and access controls. Explore options for progressive decentralization over time, if aligned with the project's roadmap.


### `M-01` — Incomplete ERC20 Implementation in Provided Snippet  *(Severity: Medium · Status: Unresolved)*

The provided code snippet defines private storage variables for ERC20 (`_balances`, `_totalSupply`, `_allowances`, `_name`, `_symbol`) and an internal `_mint` function, but lacks the public `transfer`, `transferFrom`, `approve`, `allowance`, `balanceOf`, and `decimals` functions. While the contract implements `IAgentToken`, the actual implementation of these core ERC20 functionalities is not visible. This prevents a comprehensive security assessment of the token's fundamental transfer and approval mechanisms, which are critical for any ERC20 token.

**Recommendation:** Provide the complete contract code, including all inherited interfaces and their implementations, especially the core ERC20 functions. A thorough review of these functions is essential to ensure they adhere to ERC20 standards and are free from vulnerabilities like reentrancy, integer overflows, or incorrect access controls.


### `M-02` — Potential Reentrancy in `_addInitialLiquidity` (Mitigation Unknown)  *(Severity: Medium · Status: Unresolved)*

The `_addInitialLiquidity` function performs external calls to `_uniswapRouter.addLiquidity` and `IERC20(uniswapV2Pair).transfer`. External calls, especially to unknown or potentially malicious contracts, can introduce reentrancy vulnerabilities if not properly guarded. While the `_autoSwapInProgress` flag is set to `true` at the start of `initialize` and `false` at the end of `_addInitialLiquidity`, its specific usage in preventing reentrancy during these external calls (e.g., within a `_beforeTokenTransfer` hook) is not visible in the provided snippet. Without the full context, a reentrancy vulnerability cannot be definitively ruled out.

**Recommendation:** Ensure that all external calls are protected against reentrancy. Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on functions that make external calls, or ensure that state changes occur before external calls (Checks-Effects-Interactions pattern). Clearly document how `_autoSwapInProgress` prevents reentrancy in the relevant transfer hooks.


### `L-01` — Critical Initialization Parameter `_factory` Setup  *(Severity: Low · Status: Unresolved)*

The `_factory` address, which holds significant control via the `onlyOwnerOrFactory` modifier, is set to `_msgSender()` during the `initialize` function call. If the `initialize` call is made by an untrusted, incorrect, or compromised address, that address will gain broad control over the contract's critical parameters. This is a critical setup risk that could lead to unauthorized control.

**Recommendation:** Implement stringent controls around the `initialize` function call. Ensure that only a trusted and secure entity (e.g., a deployer script controlled by a multi-sig wallet) is authorized to call `initialize`, and that the `_msgSender()` at that time is the intended factory address. Consider adding an explicit parameter for the factory address in `initialize` rather than relying solely on `_msgSender()` to prevent accidental misconfiguration.


### `L-02` — Unverified `MAX_SWAP_THRESHOLD_MULTIPLE` Usage  *(Severity: Low · Status: Unresolved)*

The constant `MAX_SWAP_THRESHOLD_MULTIPLE` is defined, likely intended to cap the `swapThresholdBasisPoints` to prevent excessively high swap thresholds. However, the `setSwapThresholdBasisPoints` function, which would enforce this cap, is truncated in the provided code snippet. Without the full implementation, it's impossible to verify if this constant is correctly utilized to prevent setting an arbitrarily high swap threshold, which could negatively impact token liquidity or user experience.

**Recommendation:** Ensure that the `setSwapThresholdBasisPoints` function correctly uses `MAX_SWAP_THRESHOLD_MULTIPLE` to enforce a reasonable upper limit on the `swapThresholdBasisPoints`. Add a `require` statement to validate that `swapThresholdBasisPoints_` does not exceed the maximum allowed value derived from `MAX_SWAP_THRESHOLD_MULTIPLE`.


### `I-01` — Bot Protection Mechanism Not Fully Visible  *(Severity: Informational · Status: Unresolved)*

The contract defines `botProtectionDurationInSeconds` and `fundedDate`, implying a mechanism to protect against bots, likely during the initial launch phase. However, the actual logic that enforces this protection (e.g., preventing transfers from non-liquidity pool addresses or limiting transaction sizes for a certain duration) is not provided in the snippet. This makes it impossible to assess the effectiveness, scope, or potential bypasses of the bot protection.

**Recommendation:** Provide the complete implementation of the bot protection mechanism, typically found within the `_beforeTokenTransfer` function. Clearly document the specific rules and conditions enforced by this mechanism, including how it interacts with different types of transfers and addresses.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc441...8643`](https://basescan.org/address/0xc44141a684f6aa4e36cd9264ab55550b03c88643) |
| **Network** | Base |
| **Price** | $0.0007626 |
| **24h Volume** | $53.4K |
| **Liquidity** | $163.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 35.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 124 buys / 97 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x47006dcfc5aa14b577d3d2a0e39f72046bf4c054)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ethy-ai-by-virtuals-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
