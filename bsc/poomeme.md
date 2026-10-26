---
token: POO.MEME
ticker: POO
network: bsc
risk_score: 39
status: medium
date: 2026-09-29
---

# POO.MEME (POO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/poomeme-bsc)

---

## Audit Summary

The PooToken contract implements a complex ERC-20 token with integrated tax, swap-back, and modular hook functionalities. The contract demonstrates robust reentrancy protection and uses OpenZeppelin libraries. Key areas of concern include a potential denial of service in fee distribution, oracle manipulation risks associated with the TWAP mechanism, and front-running opportunities during critical launch and processing phases.

> **Final Recommendation:** It is highly recommended to address the potential denial of service in the `pushOwed` function by implementing a strict limit on the number of tax payees or by introducing a pull-based mechanism for fund distribution. Review the parameters for the TWAP oracle to ensure sufficient robustness against manipulation, potentially by extending the observation window or incorporating additional price validation. While front-running for `open()` and `process()` is inherent to public functions, consider if any mitigations are feasible to reduce potential economic impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical foundations with robust reentrancy protection through `_inTransfer`, `_inSwap`, and `_running` flags, and utilizes checked arithmetic in Solidity 0.8+.… |
| **Governance / Economics** | 3/10 | High | The contract's economic model is sophisticated, incorporating platform fees, token taxes, and a swap-back mechanism to manage liquidity. The launch process is structured, requiring seeding and a… |
| **Upgrades** | 7/10 | Low | The contract is not designed to be upgradeable. This eliminates risks associated with upgradeability patterns (e.g., proxy implementation bugs, improper initialization, or storage collisions).… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `M-01` — Oracle Manipulation Risk for `_windowPrice`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_windowPrice` function calculates a time-weighted average price (TWAP) from Uniswap V2 reserves. While TWAPs are generally more resilient than spot prices, their robustness depends on the length of the observation window (`block.timestamp - _engine.priceAt`) and the liquidity of the pair. If the price window is short or the liquidity is low, a sophisticated attacker could manipulate the TWAP with a flash loan or large capital, potentially influencing the `_swap` function's execution and leading to unfavorable swaps for the protocol, resulting in economic loss.

**Recommendation:** Ensure that the `_engine.priceAt` is updated with a sufficiently long interval to create a robust TWAP. Consider implementing additional safeguards such as volume checks, deviation checks, or integrating with a more robust oracle solution (e.g., Chainlink) if the economic impact of price manipulation is significant.


### `M-02` — Front-running Opportunities in `open()` and `process()`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `open()` function, which initializes trading parameters like `_lpSupplyMark` and `_priceCumulative`, and the `process()` function, which triggers swap-backs and distributions, are publicly callable. An attacker could front-run the `open()` transaction by performing a large swap just before it, manipulating the initial state for price calculations. Similarly, `process()` can be front-run to execute profitable swaps or distributions, allowing an attacker to gain an unfair advantage or cause the original transaction to revert if the state changes.

**Recommendation:** For `open()`, consider if a commit-reveal scheme or a small, fixed delay after scheduling could mitigate manipulation of initial state. For `process()`, acknowledge the inherent front-running risk of public functions that trigger profitable actions. Ensure that the economic impact of such front-running is minimal and does not lead to significant losses for the protocol or its users.


### `M-03` — Potential Denial of Service in `pushOwed` due to Unbounded Loop  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `pushOwed` function iterates through `_tax.payeeCount + 1` recipients to distribute accumulated quote tokens. Each iteration involves an external call to `TaxLib.pushQuote`, which itself can perform external transfers. If the number of tax payees (`_tax.payeeCount`) is not strictly limited to a small number, this loop could consume excessive gas, causing the transaction to exceed the block gas limit and revert. This would prevent the distribution of owed funds to all payees, leading to a denial of service for fund distribution and potentially locking funds for some recipients.

**Recommendation:** Implement a hard limit on the number of tax payees (`p.taxPayees.length`) during contract construction to ensure `_tax.payeeCount` remains within safe gas limits. Alternatively, refactor the `pushOwed` function to allow payees to pull their owed funds individually, or implement a pagination mechanism for distribution.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $37K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `L-01` — High Complexity of External Module Interactions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PooToken` contract extensively uses external modules (`_tokenModules`) for various hooks (gate, track, operate on sell/buy). While the `runOperate` function includes a `_undoes` check to prevent modules from draining liquidity, the overall complexity introduced by arbitrary external code execution increases the attack surface. A subtle bug or unexpected behavior in a module, even with the `_undoes` safeguard, could lead to unintended consequences or denial of service for specific module functionalities.

**Recommendation:** Thoroughly audit all deployed token modules. Implement strict validation and whitelisting for module addresses. Consider adding circuit breakers or pause mechanisms for individual modules if a vulnerability is discovered post-deployment to limit potential damage.


### `I-01` — Use of Non-Standard `transient` Keyword  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `bool private transient _inTransfer;` and similar declarations. The `transient` keyword is not a standard Solidity keyword and is treated as a comment by the compiler. While the variables are correctly declared as `private` and function as expected (not stored in state), this non-standard notation could be confusing for developers unfamiliar with this specific convention.

**Recommendation:** Remove the `transient` keyword or replace it with a standard comment (e.g., `// transient`) to improve code clarity and adherence to Solidity best practices.


### `I-02` — Unused Compile-Time Assertion Function  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The function `_assertTokenModulesFitRunsDueWidth(uint8[8 - TOKEN_MODULE_LIMIT] memory)` is a clever pattern for a compile-time assertion. However, it is declared `private pure` and is never called within the contract. While this pattern often works by causing a compilation error if the condition is not met, explicitly calling it (even in a dummy way) or ensuring the compiler's behavior is understood for unused functions would guarantee the check is always enforced.

**Recommendation:** Verify that the compiler enforces this compile-time check even if the function is unused. If not, consider calling this function in the constructor or another appropriate place to ensure the assertion is always active. Alternatively, if its purpose is purely documentation, clarify this intent.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.4% of supply. Of that, 30.0% burned, 8.0% locked, 25.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.3% in wallets, 14.5% in other contracts. 2,161 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,161 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 27 Mar 2027 (179 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (meme). Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x372e...8888`](https://bscscan.com/address/0x372ef131b69068ea774a3540c704db2b0bb38888) |
| **Network** | BNB Chain |
| **Price** | $0.00001775 |
| **24h Volume** | $36.8K |
| **Liquidity** | $9.1K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | 82.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2278 buys / 207 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x251dc0cfac08d3352561d84802e3b8ddbc1d6de5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/poomeme-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
