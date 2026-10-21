---
token: SIBYL by Virtuals
ticker: SIBYL
network: base
risk_score: 74
status: high
date: 2026-09-12
---

# SIBYL by Virtuals (SIBYL) — Smart Contract Security Analysis | Base

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sibyl-by-virtuals-base)

---

## Audit Summary

The AgentToken contract implements an ERC20-like token with custom tax mechanisms, bot protection, and Uniswap V2 integration for liquidity. It utilizes OpenZeppelin's upgradeable patterns for robust architecture. The audit identified high-severity issues related to slippage control in tax-swapping mechanisms and significant centralization risk in critical administrative functions. Medium-severity concerns include the complexity of bot protection logic and the use of unlimited approvals. Several informational findings were also noted.

> **Final Recommendation:** Prioritize addressing the high-severity findings by implementing robust slippage control for the automated tax swap and strengthening access control for critical administrative functions like `setUniswapRouter`. For the `setUniswapRouter` function, consider a multi-signature wallet and a time-lock mechanism. Review and simplify the bot protection logic, ensuring it is resilient against bypasses. Additionally, enhance transparency by emitting events for all administrative actions that modify critical contract parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates a solid architectural foundation by leveraging OpenZeppelin's upgradeable contracts (7.1 Architecture). Code security (7.2 Code Security) benefits from standard ERC20… |
| **Governance / Economics** | 1/10 | High | The contract includes economic mechanisms for project taxes on buys and sells, with an automated swap-and-liquify feature (7.4 Economic). This design aims to sustain the project's treasury. However… |
| **Upgrades** | 6/10 | Medium | The contract is designed as an upgradeable proxy using OpenZeppelin's `Initializable` and `Ownable2StepUpgradeable` patterns (7.7 Upgrades). The `_disableInitializers()` in the constructor and the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 2 Medium · ⚪ 2 Informational_

### `H-01` — Lack of Slippage Control in `_swapAndLiquify`  *(Severity: High · Status: Unresolved)*

The `_swapAndLiquify` function, responsible for swapping collected tax tokens for ETH, uses `IUniswapV2Router02.swapExactTokensForETHSupportingFeeOnTransferTokens` without specifying a `minAmountOut` parameter. This omission exposes the swap to significant slippage, front-running, and sandwich attacks, potentially leading to a substantial loss of value for the protocol's collected taxes.

**Recommendation:** Implement a `minAmountOut` parameter for the `swapExactTokensForETHSupportingFeeOnTransferTokens` call. This value should be calculated based on a reasonable slippage tolerance (e.g., 0.5% - 1%) at the time of the transaction. Consider using a price oracle or a time-weighted average price (TWAP) to determine a safe `minAmountOut` if precise control is needed, or allow the owner to set a dynamic slippage tolerance.


### `H-02` — Centralization Risk with `setUniswapRouter`  *(Severity: High · Status: Unresolved)*

The `setUniswapRouter` function allows the contract `owner` to change the `_uniswapRouter` address to any arbitrary address. If the owner's private key is compromised or the owner acts maliciously, they could set a rogue router contract. This rogue router could then be used to drain tokens from the `AgentToken` contract during subsequent `_swapAndLiquify` operations or other interactions, leading to a complete loss of funds.

**Recommendation:** Implement a multi-signature wallet for the `owner` address to control critical functions like `setUniswapRouter`. Additionally, consider a time-lock mechanism for such sensitive changes, allowing users to react to a potentially malicious update. Restrict the `_uniswapRouter` to a whitelist of trusted router addresses if possible.


### `M-01` — Complex Bot Protection Logic with `keccak256(address.code)`  *(Severity: Medium · Status: Unresolved)*

The `_checkBotProtection` function utilizes `keccak256(address.code)` to identify valid callers. While `addLiquidityPool` checks for `code.length`, `addValidCaller` does not. If `keccak256("")` (the hash for an empty code, typical of an EOA) is added to `_validCallerCodeHashes`, EOAs could potentially bypass bot protection. Furthermore, relying on `address.code` can be complex and potentially lead to unexpected behavior, especially with contracts deployed within the same transaction or during specific contract lifecycle stages.

**Recommendation:** Review the bot protection logic carefully. Ensure that `_validCallerCodeHashes` cannot contain `keccak256("")` unless EOAs are explicitly intended to bypass protection. Consider alternative, more robust methods for bot detection or whitelisting, such as role-based access control or specific contract interfaces, rather than relying solely on code hashes, which can be brittle.


### `M-02` — `type(uint256).max` Approvals for Uniswap Router  *(Severity: Medium · Status: Unresolved)*

The `_addInitialLiquidity` and `_swapAndLiquify` functions grant `type(uint256).max` (unlimited) approval to the `_uniswapRouter` for `AgentToken` and `pairToken`. While `_uniswapRouter` is expected to be a trusted Uniswap V2 router, unlimited approvals are generally discouraged as a security best practice. If the `_uniswapRouter` contract were ever compromised or replaced with a malicious one (as per H-02), it could potentially drain all approved tokens from the `AgentToken` contract.

**Recommendation:** Where possible, use specific, limited approvals instead of `type(uint256).max`. For `_swapAndLiquify`, approve only the exact `amountToSwap`. For initial liquidity, if `type(uint256).max` is deemed necessary for ongoing operations, ensure robust access control and monitoring for the `_uniswapRouter` address.


### `I-01` — Missing Events for Critical State Changes  *(Severity: Informational · Status: Unresolved)*

Several administrative functions that modify critical contract parameters, such as `setProjectTaxRecipient`, `setProjectBuyTaxBasisPoints`, `setProjectSellTaxBasisPoints`, `setSwapThresholdBasisPoints`, `setUniswapRouter`, and `setBotProtectionDurationInSeconds`, do not emit corresponding events. This lack of event emission hinders transparency, makes off-chain monitoring and auditing of administrative actions difficult, and can obscure important changes to the contract's behavior.

**Recommendation:** Emit events for all administrative actions that modify critical state variables. This provides a clear, immutable log of changes, improving transparency and enabling better monitoring and accountability.


### `I-02` — Unused `CALL_GAS_LIMIT` Constant  *(Severity: Informational · Status: Unresolved)*

The constant `CALL_GAS_LIMIT` is declared in the contract but is not utilized anywhere within the provided source code. This might indicate leftover code from previous iterations, a planned feature that was not implemented, or an oversight.

**Recommendation:** Remove unused code to reduce contract size and improve readability. If it's intended for a future feature, consider adding a comment explaining its purpose.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x797f...4714`](https://basescan.org/address/0x797f214a2cd64a4963a91fa21c8c55ec3eba4714) |
| **Network** | Base |
| **Price** | $0.002647 |
| **24h Volume** | $74.1K |
| **Liquidity** | $226.9K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 52.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 157 buys / 107 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x43447f02ada550929f1f0619471a8f8dba173243)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sibyl-by-virtuals-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
