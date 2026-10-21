---
token: Fuse Cat
ticker: FUSECAT
network: ethereum
risk_score: 62
status: medium
date: 2026-09-14
---

# Fuse Cat (FUSECAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fuse-cat-eth-a4f9)

---

## Audit Summary

The Fuse Cat Token contract implements a custom ERC-20 token with advanced features including dynamic transaction taxes, anti-bot mechanisms, max transaction/wallet size limits, and an early buying phase. The contract exhibits a high degree of centralization, with the owner possessing extensive control over critical parameters and operational functions. Key technical concerns include a non-standard `balanceOf` override, potential for sandwich attacks on tax swaps, and the use of a global variable for transaction state. The lack of upgradeability means any discovered issues cannot be patched post-deployment.

> **Final Recommendation:** It is strongly recommended to decentralize control where possible, or at minimum, implement a multi-signature wallet for critical administrative functions to mitigate the high centralization risk. Review and harden the `balanceOf` function and the tax swap mechanism to prevent sandwich attacks and ensure predictable behavior. Consider implementing a timelock for sensitive parameter changes to provide transparency and reaction time for the community. Given the non-upgradeable nature, a thorough and comprehensive audit is paramount before deployment to minimize the risk of immutable vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes SafeMath for arithmetic operations, enhancing robustness against overflow/underflow (7.2 Code Security). However, the `balanceOf` function includes non-standard conditional… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralization, with the owner having extensive control over critical parameters such as tax rates, max transaction/wallet sizes, trading status, and the… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade proxy pattern, meaning it is not upgradeable (7.7 Upgrades). Any vulnerabilities discovered post-deployment or desired feature enhancements cannot be… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.1% (≈ permanent lock) |
| **LP Locked** | 99.1% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Centralized Control and Extensive Owner Privileges  *(Severity: Critical · Status: Unresolved)*

The contract owner possesses extensive control over critical parameters and operational functions, including setting tax rates, modifying max transaction/wallet sizes, enabling/disabling trading, managing blacklisted addresses, and controlling the early buying phase. This high degree of centralization introduces significant trust assumptions and a single point of failure, allowing the owner to unilaterally alter tokenomics or restrict user access.

**Recommendation:** Implement a multi-signature wallet for critical administrative functions to distribute control and reduce the risk of a single point of compromise. Consider introducing a timelock for sensitive parameter changes to provide transparency and allow the community to react to proposed modifications. Explore mechanisms for progressive decentralization over time.


### `H-01` — Sandwich Attack Vulnerability in Tax Swaps  *(Severity: High · Status: Unresolved)*

The `swapExactTokensForETHSupportingFeeOnTransferTokens` function, used for automatic tax collection, is called with `amountOutMin = 0`. This allows malicious actors to execute sandwich attacks by front-running the swap with a buy order and back-running with a sell order, manipulating the price and extracting value. This results in the `_taxWallet` receiving less ETH than expected, impacting the protocol's intended revenue.

**Recommendation:** Implement a slippage tolerance by calculating a reasonable `amountOutMin` based on the expected amount and a predefined acceptable slippage percentage. Alternatively, consider using a trusted oracle or a TWAP mechanism to determine a fair price for swaps, or integrate with a DEX aggregator that handles slippage protection.


### `H-02` — Ambiguous `balanceOf` Override and `tx.origin` Usage  *(Severity: High · Status: Unresolved)*

The `balanceOf` function is overridden with complex conditional logic (`_MARTIANSsp` variable) and includes a check for `_isExcludedFromFee[tx.origin]`. This non-standard implementation can lead to unexpected balance reporting for external integrations (e.g., DEXs, wallets) and introduces a dependency on `tx.origin`, which is generally discouraged due to potential phishing risks (though less critical here for fee exclusion).

**Recommendation:** Simplify the `balanceOf` function to adhere to standard ERC-20 behavior. If specific addresses need to be excluded from fees, manage this logic within the `_transfer` function rather than altering `balanceOf`. Avoid using `tx.origin` for any critical logic, even for fee exclusion, to prevent potential misinterpretations or vulnerabilities in complex interaction scenarios.


### `M-01` — Dynamic Tax Mechanism Susceptible to Manipulation  *(Severity: Medium · Status: Unresolved)*

The contract implements dynamic buy/sell taxes that reduce after a certain number of transactions (`_buyCount`, `sellCount`) reaches predefined thresholds (`_reduceBuyTaxAt`, `_reduceSellTaxAt`). This mechanism can be gamed by bots or sophisticated users who can execute numerous small transactions to artificially inflate the transaction counts, thereby lowering the taxes for subsequent larger trades and impacting the intended tax revenue model.

**Recommendation:** Re-evaluate the dynamic tax reduction mechanism. Consider alternative methods for tax reduction that are less susceptible to manipulation, such as time-based reductions, or implement more robust anti-bot measures that specifically target such gaming behavior. Clearly document the intended behavior and potential implications of this mechanism.


### `M-02` — Global Variable for Transaction State (`_SYMBOLgod`)  *(Severity: Medium · Status: Unresolved)*

The `_SYMBOLgod` variable is declared as a global state variable and is used to temporarily store the `amount` within the `transferFrom` function. While its immediate use might mitigate direct reentrancy in this specific context, using a global state variable for local transaction data is poor programming practice. It can lead to subtle bugs, race conditions, or unexpected behavior in more complex scenarios or if the contract's logic is expanded in the future.

**Recommendation:** Refactor the `transferFrom` function to use a local variable for the `amount` instead of the global `_SYMBOLgod` variable. This improves code clarity, reduces potential side effects, and adheres to best practices for managing transaction-specific data.


### `L-01` — Renounce Ownership Implication  *(Severity: Low · Status: Unresolved)*

The `renounceOwnership` function allows the owner to transfer ownership to the zero address. Given the extensive owner privileges in this contract, calling this function would effectively make the contract unmanageable, as many critical functions are protected by the `onlyOwner` modifier. This could lead to a 'bricked' contract where no administrative actions can be performed.

**Recommendation:** Ensure the owner fully understands the implications of `renounceOwnership`. If the intention is to decentralize control, a more robust governance mechanism should be implemented rather than simply renouncing ownership. If renouncing is desired, ensure all necessary parameters are immutable or managed by other means before doing so.


### `I-01` — Lack of Upgradeability  *(Severity: Informational · Status: Unresolved)*

The contract is not designed with an upgrade proxy pattern (e.g., UUPS, Transparent). This means that the contract's logic is immutable once deployed. Any discovered vulnerabilities, bugs, or desired feature enhancements post-deployment cannot be implemented without deploying a new contract and migrating all assets and users, which is a complex, costly, and risky process.

**Recommendation:** For future projects or if long-term adaptability is a requirement, consider implementing an upgradeable proxy pattern. This allows for bug fixes and feature enhancements without requiring a full redeployment and migration, improving the protocol's resilience and longevity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6821...0212`](https://etherscan.io/address/0x6821c6c62bc13105bab758cc703cff39e5690212) |
| **Network** | Ethereum |
| **Price** | $0.00711 |
| **24h Volume** | $1.91M |
| **Liquidity** | $285.6K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 13h |
| **Top-10 Holders** | 13.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5320 buys / 3684 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa34e36019c4e6c8323bdcf31ff1a83e7e652787f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fuse-cat-eth-a4f9)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
