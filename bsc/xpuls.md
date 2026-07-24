---
token: XPULS
ticker: XPULS
network: bsc
risk_score: 49
status: high
date: 2026-07-23
---

# XPULS (XPULS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 49/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xpuls-bsc)

---

## Audit Summary

The XPLUSToken contract implements a custom ERC20 token with complex tax mechanisms for buy and sell transactions, integrating with Uniswap V2. The audit identified several medium and low-severity issues related to the custom tax logic, dynamic trading caps, and non-standard Uniswap math. A significant portion of the `_transfer` function and related logic was truncated in the provided source code, limiting the depth of the analysis and potentially concealing further vulnerabilities. The contract utilizes OpenZeppelin libraries for security and access control, but its custom logic introduces complexity and potential risks.

> **Final Recommendation:** It is highly recommended to complete and provide the full source code for a comprehensive audit, especially for the `_transfer` function and `_swapAndDistribute` logic. Simplify the complex tax calculation and distribution logic within the `_transfer` function to reduce the risk of errors and improve maintainability. Re-evaluate the dynamic `max cap buy/sell` limits to ensure they do not inadvertently hinder legitimate trading or create opportunities for liquidity manipulation. Consider aligning Uniswap V2 math functions with standard implementations or clearly documenting the deviations and their implications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's ERC20, Ownable, and ReentrancyGuard, providing a solid security baseline (7.2 Code Security). However, the overridden `_transfer` function contains highly… |
| **Governance / Economics** | 4/10 | Medium | The tokenomics involve high buy (3.5%) and sell (3.5%) tax rates, with a complex distribution mechanism to various addresses and a burn address (7.4 Economic). The `totalProfitTaxRate` is declared… |
| **Upgrades** | 7/10 | Low | The contract is not designed with upgradeability patterns (e.g., proxy contracts). Therefore, there are no upgrade-related risks (7.7 Upgrades). Any changes to the contract logic would require a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 35.3% |
| **LP Locked** | 35.3% — Null Address |
| **Top-1 Unlocked Holder** | ⚠️ 59.0% |
| **Top-3 Unlocked** | 64.7% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `H-01` — Centralization Risk via Owner Privileges and Immutable Setup  *(Severity: High · Status: Unresolved)*

The `owner` (deployer) has significant control over the token's initial operational phase. The `setPresale()` function, callable only by the owner, initiates the token's trading by calling `launch()` and `updatePoolReserve()`. This single point of control for enabling trading, combined with the immutable setting of critical fee distribution addresses (marketing, node, protection fund) during deployment, means a compromise of the owner's key could severely impact the project's launch and initial fund distribution. While `Ownable` is a standard pattern, the impact of this centralization at launch is high.

**Recommendation:** Implement a multi-signature wallet for the `owner` address to mitigate the risk of a single point of failure. Consider a time-locked or governance-controlled mechanism for critical launch parameters if applicable, rather than sole owner discretion. Ensure all critical addresses are thoroughly vetted before deployment, as they are immutable.


### `M-01` — High and Complex Tax Mechanism with Incomplete Logic  *(Severity: Medium · Status: Unresolved)*

The contract implements high buy (3.5%) and sell (3.5%) tax rates with intricate, multi-step distribution logic within the `_transfer` function. This complexity increases the attack surface and the likelihood of calculation errors or unexpected behavior. Furthermore, the `totalProfitTaxRate` variable is declared but its application is not visible in the provided `_transfer` function, suggesting incomplete or missing critical economic logic. The `_swapAndDistribute` function, which is likely central to fee handling, is also truncated.

**Recommendation:** Simplify the tax calculation and distribution logic where possible to improve readability and reduce the risk of errors. Ensure all declared tax rates, especially `totalProfitTaxRate`, are fully implemented and their effects are clearly understood. Provide the complete source code, including `_swapAndDistribute`, for a thorough review of the entire tax mechanism.


### `M-02` — Dynamic 'Max Cap Buy/Sell' Based on Current Reserves  *(Severity: Medium · Status: Unresolved)*

The `_transfer` function imposes dynamic limits on buy and sell transactions, restricting them to `amount <= reserveThis / 10` (10% of the token's reserve in the Uniswap pair). This dynamic cap, while potentially intended to prevent large price impacts, makes trading highly dependent on current liquidity. If reserves are low, users might be unable to execute even small trades, leading to unexpected transaction failures or a denial of service for legitimate traders. This mechanism is also susceptible to manipulation if an attacker can temporarily reduce reserves to block trading.

**Recommendation:** Re-evaluate the necessity and implications of the dynamic `max cap buy/sell` limits. Consider implementing fixed limits or a more robust mechanism that ensures basic trading functionality even during low liquidity periods. Clearly document the behavior and potential consequences of this dynamic cap for users.


### `M-03` — Custom Uniswap V2 Math Deviation  *(Severity: Medium · Status: Unresolved)*

The `_getAmountOut` and `_getAmountIn` functions implement custom calculations for Uniswap V2-like swaps, using `9975` and `10000` for fee adjustments. This deviates from the standard Uniswap V2 fee of `0.3%` (typically represented as `997/1000` or `9970/10000`). While this might be an intentional design choice, it is non-standard and could lead to unexpected price impacts, arbitrage opportunities, or compatibility issues with external DeFi protocols that assume standard Uniswap V2 math.

**Recommendation:** Clearly document the reasons for deviating from standard Uniswap V2 math and the implications for users and integrators. Ensure that the custom calculations are thoroughly tested and verified to prevent unintended economic consequences. Consider aligning with standard Uniswap V2 math if the deviation does not offer a critical functional advantage.


### `L-01` — Publicly Callable `updatePoolReserve` with Potential for Manipulation  *(Severity: Low · Status: Unresolved)*

The `updatePoolReserve()` function can be called by any external address. Although it includes a time-based guard (`block.timestamp >= poolStatus.t + 1 hours`) to limit updates to once per hour, allowing public calls means an attacker could time their transaction to update the `poolStatus.bal` (USDT reserve) at a specific moment. Since `poolStatus.bal` directly influences the dynamic `max cap buy/sell` limits, this could be used to front-run or manipulate the perceived liquidity, potentially affecting legitimate trades.

**Recommendation:** Consider restricting the `updatePoolReserve()` function to `onlyOwner` or a trusted role, or implementing a more robust mechanism to prevent malicious timing attacks. Alternatively, ensure that the impact of `poolStatus.bal` updates on trading limits is thoroughly analyzed for potential manipulation vectors.


### `L-02` — Unused State Variables  *(Severity: Low · Status: Unresolved)*

The state variables `yplusSwapAddress` and `interactionContract` are declared in the contract but are neither initialized in the constructor nor assigned values via any setter functions in the provided code. This indicates either incomplete implementation, dead code, or variables intended for future use without current functionality. Unused variables can lead to confusion, increase contract size unnecessarily, and potentially introduce vulnerabilities if they are later used without proper initialization or validation.

**Recommendation:** Remove unused state variables to reduce contract complexity and gas costs. If these variables are intended for future use, implement proper initialization in the constructor or secure setter functions, and clearly document their purpose.


### `I-01` — Truncated Code Limits Audit Scope  *(Severity: Informational · Status: Unresolved)*

The provided source code for the `XPLUSToken` contract is incomplete. Specifically, the `_transfer` function is truncated, and critical logic related to `_swapAndDistribute()` and the full application of `totalProfitTaxRate` is missing. This significantly limits the ability to conduct a comprehensive security audit, as crucial functionality, potential vulnerabilities, and the complete economic model cannot be fully assessed.

**Recommendation:** Provide the complete and untruncated source code for all relevant contracts to enable a thorough and accurate security audit. Without the full code, any audit findings are necessarily partial and may not cover all potential risks.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xabae...8228`](https://bscscan.com/address/0xabae909cd93bc2ddf90086f9aa6c3f8e154e8228) |
| **Network** | BNB Chain |
| **Price** | $0.03641 |
| **24h Volume** | $1.95M |
| **Liquidity** | $9.12M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 37.9% of supply |
| **Buy / Sell Tax** | 0.1% / 0.1% |
| **24h Transactions** | 4983 buys / 14926 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd7501ec4223cf439da3606e038e463eeeaaf1627)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xpuls-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-23*
