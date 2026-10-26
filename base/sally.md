---
token: Sally
ticker: A1C
network: base
risk_score: 3
status: low
date: 2026-08-30
---

# Sally (A1C) — Smart Contract Security Analysis | Base

> **Risk Score: 3/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sally-base)

---

## Audit Summary

The AgentKey contract, an upgradeable ERC20 token with staking and fee distribution mechanisms, leverages OpenZeppelin's secure libraries and reentrancy guards. However, a critical vulnerability was identified where the `_approve` function is called with an incorrect signature, preventing the core fee-swapping functionality. Additionally, the fee distribution logic is susceptible to reentrancy, and Uniswap swaps lack slippage protection, exposing the protocol to significant financial risks. Centralized control points and immutable configuration parameters also present operational and governance considerations.

> **Final Recommendation:** Immediate attention is required to rectify the critical `_approve` function signature error, as this issue fundamentally breaks the contract's fee-swapping mechanism. Furthermore, the reentrancy vulnerability in the fee distribution logic and the absence of slippage protection in Uniswap swaps must be addressed to safeguard against potential financial exploits and value erosion. Consider implementing controlled setter functions for critical parameters to enhance operational adaptability without compromising security, and strengthen the security protocols surrounding the centralized control addresses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's `ERC20BurnableUpgradeable` and `ReentrancyGuard` for foundational security, and uses a specific Solidity version (0.8.27). However, a critical bug exists in the… |
| **Governance / Economics** | 6/10 | Medium | The contract's economic model includes a subscription/cooldown mechanism and a fee distribution system. Key parameters like fee percentages (`adminSellFeePercent`, `creatorSellFeePercent`) and the… |
| **Upgrades** | 2/10 | High | The contract is designed as an upgradeable implementation using OpenZeppelin's `ERC20BurnableUpgradeable` and the `initializer` modifier, following standard proxy patterns. Immutable variables are… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 5 Medium · 🟢 1 Low_

### `M-01` — Immutability of Critical Configuration Parameters  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several key operational parameters, including `adminSellFeePercent`, `creatorSellFeePercent`, `treasury`, `router`, and `ansTokenID`, are set during the `initialize` function and declared as `public` but without setter functions. This makes them immutable after deployment. While immutability can reduce governance attack surface, it also removes the flexibility to adjust fees in response to market changes, update the treasury address, or change the Uniswap router if a vulnerability or better alternative emerges. This could lead to operational rigidity or necessitate a full contract upgrade for minor parameter adjustment

**Recommendation:** Evaluate whether these parameters truly need to be immutable. For parameters that might require future adjustments (e.g., fee percentages, treasury address, router address), consider implementing controlled setter functions, possibly with a timelock, to allow for secure updates.


### `M-02` — Centralized Control and Potential Single Points of Failure  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_factory` and `bondingCurve` addresses hold significant control over the contract's lifecycle and initial operations. `initialize` is restricted to `_factory`, while `launch` and `setPair` are restricted to `bondingCurve`. Additionally, pre-launch `transferFrom` is restricted to `bondingCurve`. If these controlling addresses are compromised, it could lead to unauthorized contract initialization, manipulation of the trading pair, or unauthorized token transfers before launch.

**Recommendation:** Ensure that the private keys or multi-signature wallets controlling `_factory` and `bondingCurve` are secured with the highest standards. Consider implementing a multi-signature wallet for these critical roles to distribute control and reduce the risk associated with a single point of failure.


### `M-03` — Critical Vulnerability: Incorrect `_approve` Function Signature  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `_swapToETH` function, the call `_approve(address(this), address(router), _amount, false)` attempts to approve tokens for the Uniswap router. However, the standard OpenZeppelin `ERC20Upgradeable._approve` function, which this contract inherits, only accepts three arguments (`owner`, `spender`, `value`). The inclusion of a fourth `false` argument results in an incorrect function signature. This will cause a compilation error or, if a custom `_approve` with this signature exists (which is not provided in the standard imports), it would lead to an unintended and potentially insecure behavior. This is a fundamental

**Recommendation:** Correct the `_approve` call to match the standard OpenZeppelin `ERC20Upgradeable._approve` signature: `_approve(address(this), address(router), _amount)`. If a custom `_approve` is intended, its implementation must be provided and thoroughly reviewed.


### `M-04` — Reentrancy Vulnerability in Fee Distribution  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_update` function, which is called by `transfer` and `transferFrom`, is not protected by a reentrancy guard. Inside `_update`, if `_to == pair`, it performs a `super._update` call, then calls `_handleFee`, and then another `super._update`. The `_handleFee` function itself is protected by `nonReentrant`, but it makes external calls (`_feeHandler.pay`, `_safeETHTransfer`, `router.swapExactTokensForETH`) between internal state updates. An attacker could re-enter the `transfer` or `transferFrom` function during these external calls, potentially manipulating balances or fees before the full `_update` sequence is comple

**Recommendation:** Apply the `nonReentrant` modifier to the `_update` function or ensure that all external calls are made after all state changes are finalized within the `_update` and `_handleFee` logic. A common pattern is to use a 'checks-effects-interactions' approach.


### `M-05` — Lack of Slippage Protection in Uniswap Swaps  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_swapToETH` function executes `router.swapExactTokensForETH` with `minAmountOut` set to `0`. This means the contract accepts any amount of ETH in return for the swapped tokens, regardless of the current market price. This vulnerability exposes the contract to sandwich attacks, front-running, and general price manipulation, where malicious actors can exploit the lack of slippage protection to extract value from the fee collection mechanism, leading to significant financial losses for the protocol.

**Recommendation:** Implement robust slippage protection by calculating a reasonable `minAmountOut` based on the expected exchange rate and a predefined slippage tolerance. This value should be passed to `swapExactTokensForETH` to ensure that swaps only execute if the received amount of ETH is above a certain threshold.


### `L-01` — Potential Denial of Service in Fee Distribution  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_handleFee` function attempts to pay the `adminAmount` to `_feeHandler` via `_feeHandler.pay{value: adminAmount}()`. If the `_feeHandler` contract is malicious, incorrectly implemented, or enters a state where its `pay()` function consistently reverts (e.g., due to an internal error or a block on receiving ETH), it could cause all transfers to the `pair` to fail, effectively halting the fee collection mechanism and disrupting normal token operations.

**Recommendation:** Implement robust error handling for external calls. Consider using a `try/catch` block around the `_feeHandler.pay()` call to gracefully handle reverts, perhaps by logging the failure and attempting to send the funds to a fallback address or accumulating them for later manual recovery. Alternatively, ensure `_feeHandler` is a trusted and audited contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1f1c...ad69`](https://basescan.org/address/0x1f1c695f6b4a3f8b05f2492cef9474afb6d6ad69) |
| **Network** | Base |
| **Price** | $0.1805 |
| **24h Volume** | $88.6K |
| **Liquidity** | $316.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 56.1% of supply |
| **Buy / Sell Tax** | 0.0% / 3.0% |
| **24h Transactions** | 498 buys / 845 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x7dc3662f4c2c41c5752652e8b417a9024c2b1f63)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sally-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
