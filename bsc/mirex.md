---
token: Mirex
ticker: MRX
network: bsc
risk_score: 44
status: medium
date: 2026-09-02
---

# Mirex (MRX) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mirex-bsc)

---

## Audit Summary

The MRXToken contract implements an ERC-20 token with custom tokenomics features including transaction fees, maximum transaction/holding limits, cooldowns, and a swap-back mechanism for collected fees. The contract utilizes OpenZeppelin's AccessControl for role-based permissions and SafeMath for arithmetic safety. While core ERC-20 functionality appears sound, the audit identified a high degree of centralization in the admin role, inconsistencies in the fee swap mechanism, and a lack of slippage protection, leading to a Medium overall risk level.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement a multi-signature wallet for the `admin` role to decentralize control and enhance security. Critical parameter changes should ideally be subject to a time-lock mechanism to provide transparency and allow for community review. Furthermore, the fee swap mechanism should be reviewed for consistency, ensuring that the intended asset (USDT or WETH) is used for both fee calculation and actual swaps, and robust slippage protection should be added to safeguard against value loss during swaps.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good practices such as using SafeMath for arithmetic operations and implementing a reentrancy guard for external swap calls (7.2 Code Security). However, the swap-back… |
| **Governance / Economics** | 2/10 | High | The contract design grants significant power to a single `admin` address, which can unilaterally modify critical tokenomics parameters such as fees, transaction/holding limits, cooldowns, and trading… |
| **Upgrades** | 7/10 | Low | The MRXToken contract is implemented as a standard, non-upgradeable contract. Therefore, there are no specific upgrade-related risks or complexities to consider (7.7 Upgrades). Any future changes to… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Inconsistent Use of USDT in Swap-Back Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constructor takes a `_usdt` address, which is used in the `calculateFee` function's `getAmountsOut` path for fee valuation. However, the actual swap-back mechanism in `_swapTokensForEth` uses `router.swapExactTokensForETHSupportingFeeOnTransferTokens` with a path of `[address(this), router.WETH()]`, effectively swapping MRX for WETH, not USDT. This inconsistency could lead to discrepancies between the calculated fee value (based on USDT) and the actual value obtained from the swap (based on WETH), impacting project treasury if price ratios diverge.

**Recommendation:** Clarify the intended stablecoin for fee conversion. If USDT is intended, modify `_swapTokensForEth` to swap for USDT. If WETH is intended, ensure `calculateFee` accurately reflects WETH-based valuation or remove the `_usdt` parameter if it's not used for actual swaps.


### `M-02` — Lack of Slippage Protection in Swap-Back  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_swapTokensForEth` function calls `router.swapExactTokensForETHSupportingFeeOnTransferTokens` without specifying an `amountOutMin` parameter. This means the swap operation has no slippage protection. In scenarios of low liquidity, high market volatility, or large swap amounts, the transaction could suffer from significant slippage, resulting in fewer ETH being received than expected for the collected fees, directly impacting the project's treasury.

**Recommendation:** Implement slippage protection by calculating a reasonable `amountOutMin` based on current market conditions and a predefined acceptable slippage tolerance. This can be achieved by querying `getAmountsOut` with the desired path and applying a slippage factor.


### `M-03` — Potential for Abuse of Exclusion Lists  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `admin` role has the ability to add or remove any address from `isFeeExempt`, `_isExcludedFromMaxTxn`, `_isExcludedMaxHolding`, and `isExcludedFromCooldown` lists. While intended for legitimate operational purposes, this power could be abused to grant unfair advantages to specific users or wallets, bypassing tokenomics rules and potentially leading to market manipulation or a perception of unfairness.

**Recommendation:** Clearly document the intended use cases for these exclusion lists. Consider implementing a governance mechanism or a multi-signature approval process for adding/removing addresses from these critical lists, especially for non-protocol-owned addresses.


### `M-04` — High Centralization of Control in Admin Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `admin` role, controlled by a single address, possesses extensive authority over critical contract parameters and functionalities. This includes the ability to set buy/sell fees, max transaction/holding limits, cooldown timers, enable/disable trading, enable/disable the swap-back mechanism, and exempt any address from these rules. This high degree of centralization introduces a single point of failure and potential for malicious action or compromise.

**Recommendation:** Implement a multi-signature wallet for the `admin` role to distribute control and reduce the risk of a single point of compromise or malicious action. Consider a time-lock for critical parameter changes to allow for community review and reaction time.


### `L-01` — Fixed `feeDenominator`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `feeDenominator` is hardcoded to `100_00` (10000), implying fees are calculated in basis points. While this is a common practice, the contract does not provide a mechanism to change this denominator. If future tokenomics require a different fee granularity (e.g., per mille), this would necessitate a new contract deployment.

**Recommendation:** If flexibility in fee granularity is desired, consider making `feeDenominator` a configurable parameter by the admin, similar to other fee-related settings. Otherwise, ensure the current basis point system is sufficient for all foreseeable tokenomics.


### `I-01` — Unused `usdt` parameter in `_swapTokensForEth` context  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `usdt` address is passed in the constructor and used in `calculateFee` for `getAmountsOut` path. However, the `_swapTokensForEth` function, which performs the actual swap, hardcodes the path to `[address(this), router.WETH()]`, effectively ignoring the `usdt` address for the swap. This creates a discrepancy where the fee calculation might be based on a USDT path, but the actual swap is for WETH.

**Recommendation:** Review the intended functionality. If the goal is to swap for USDT, the `_swapTokensForEth` function should use `usdt` in its path and call the appropriate router function. If the goal is to swap for WETH, the `usdt` parameter's role in `calculateFee` should be re-evaluated for consistency.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa605...d89e`](https://bscscan.com/address/0xa605d1b98f3f26eed3267bade68cb8382136d89e) |
| **Network** | BNB Chain |
| **Price** | $1.4500 |
| **24h Volume** | $9.1K |
| **Liquidity** | $104.8K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 20h |
| **Top-10 Holders** | 11.2% of supply |
| **Buy / Sell Tax** | 1.5% / 3.5% |
| **24h Transactions** | 464 buys / 163 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x2bf6c9c9bd7ac448ab3d524653eed7b4297a9c26)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mirex-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
