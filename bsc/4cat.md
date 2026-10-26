---
token: 4cat
ticker: 4CAT
network: bsc
risk_score: 13
status: low
date: 2026-09-22
---

# 4cat (4CAT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/4cat-bsc)

---

## Audit Summary

The Stock4TaxToken contract implements an ERC-20 compatible token with a complex tax and fee distribution mechanism, operating as a proxy. The audit identified significant centralization risks due to multiple privileged roles and reliance on external contracts. Critical functions like `_transfer` and `_dispatchFee` were not fully provided, limiting a complete security assessment. Economic parameters, such as high sell fees and dispatch thresholds, require careful consideration.

> **Final Recommendation:** It is strongly recommended to conduct a thorough review of the complete source code, especially the `_transfer` and `_dispatchFee` functions, to ensure all security considerations are addressed. Implement robust access control mechanisms and multi-signature wallets for all privileged roles (`tokenModule`, `vault`, `migrateModule`, `shareHolderManager`) to mitigate centralization risks. Carefully evaluate and document the trust assumptions for all external contracts, such as `ITokenHelper` and `IShareHolderManager`, and consider implementing circuit breakers or emergency pause functionalities for critical operations. Finally, review the economic parameters, particularly the `sellFeeRate` and dispatch thresholds, to ensure they align with the project's long-term goals and user expectations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes OpenZeppelin's SafeERC20 for secure token operations, mitigating common integer overflow/underflow risks (7.2 Code Security). Reentrancy guards (`swapping`, `dispatchingFee`)… |
| **Governance / Economics** | 6/10 | Medium | The contract exhibits significant centralization through various privileged roles (7.3 Access Control). The `tokenModule` can configure critical external addresses via `postInitialize`, and the… |
| **Upgrades** | 9/10 | Low | The contract is deployed as an upgradeable proxy, utilizing the `initializer` modifier for its `initialize` function (7.7 Upgrades). A `postInitialize` function is also present, protected by the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 2 Low · ⚪ 1 Informational_

### `M-01` — Heavy Reliance on External Contracts  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Stock4TaxToken` contract heavily relies on several external interfaces, including `ITokenHelper`, `IShareHolderManager`, `ITaxVault`, and `IWrappedNative`. The `ITokenHelper` contract, in particular, performs critical swap and liquidity operations. The security and correct functioning of these external contracts are paramount to the integrity and operation of `Stock4TaxToken`. A vulnerability, compromise, or malicious upgrade in any of these external dependencies could directly impact the token's functionality, security, or economic stability.

**Recommendation:** Thoroughly audit all external contracts that `Stock4TaxToken` interacts with. Implement robust input validation for addresses set for these external contracts. Consider adding circuit breakers or emergency pause functionalities that can temporarily disable interactions with compromised external contracts if a vulnerability is detected. Ensure that the addresses of these external contracts are immutable or can only be updated through a secure, multi-signature governance process.


### `M-02` — Incomplete Code for Critical Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `Stock4TaxToken` contract is incomplete. Specifically, the `_transfer` function is truncated, and the `_dispatchFee` function is entirely absent from the provided snippet. These functions are central to the token's core logic, handling token transfers, fee collection, and distribution. Without a full review of these critical implementations, it is impossible to thoroughly assess potential vulnerabilities such as reentrancy, incorrect fee calculations, improper handling of edge cases, or other security flaws.

**Recommendation:** Provide the complete and verified source code for all relevant functions, especially `_transfer` and `_dispatchFee`, for a comprehensive security audit. A full review is essential to ensure the absence of hidden vulnerabilities that could lead to asset loss or protocol malfunction.


### `M-03` — Centralized Control Over Critical Parameters and Blacklisting  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract grants significant centralized control to several privileged roles. The `tokenModule` address can call `postInitialize` to set critical external contract addresses like `tokenHelper`, `shareHolderManager`, and `lpV2Manager`. The `shareHolderManager` contract, once set, can blacklist users from transferring tokens via its `isBlacklisted` function. Additionally, `onlyTaxVault` and `onlyMigrateModule` modifiers restrict access to specific functions to `vault` and `migrateModule` addresses, respectively. This concentration of power introduces a single point of failure and potential for censorship or malicious

**Recommendation:** Implement multi-signature wallets for all privileged roles (`tokenModule`, `vault`, `migrateModule`, `shareHolderManager`) to require multiple approvals for critical actions. Clearly document the responsibilities and powers of each role. Consider decentralizing the blacklist mechanism or providing a transparent process for appeals and removals. For critical parameter updates, consider a time-locked governance mechanism.


### `L-01` — High Configurable Sell Fee Rate  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `sellFeeRate` parameter is initialized with a minimum value of 100 (representing 10%) and a maximum of 1000 (representing 100%). While configurable, a default or minimum sell fee of 10% is substantial. Such a high fee can significantly impact user experience, deter trading activity, and potentially lead to reduced liquidity or adoption of the token. Although not a direct security vulnerability, it is an economic parameter that could negatively affect the token's ecosystem.

**Recommendation:** Carefully consider the economic implications of a high sell fee rate. Evaluate if the current minimum and default values align with the project's goals for trading volume and user engagement. Clearly communicate the fee structure to users. Provide mechanisms for governance to adjust these fees if market conditions or project strategy changes.


### `L-02` — Potential for Fee Accumulation if Dispatch Thresholds are Misconfigured  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `minDispatch` and `minDispatchQuote` parameters dictate the minimum amounts of accumulated fees required before the `dispatchTax` function can effectively distribute them. If these thresholds are set too high, accumulated fees might remain undistributed for extended periods. This could lead to user dissatisfaction, perceived illiquidity of rewards, or a build-up of a large amount of funds in the contract, potentially making it a more attractive target for attackers, even if protected.

**Recommendation:** Regularly monitor the accumulated fees and dispatch activity. Ensure that `minDispatch` and `minDispatchQuote` are set to reasonable values that balance gas costs with timely fee distribution. Consider implementing a mechanism for governance to adjust these thresholds based on network conditions and accumulated fee volumes. Clearly communicate the dispatch mechanics to token holders.


### `I-01` — Multi-Step Initialization for Proxy Contract  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract employs a multi-step initialization process, using both an `initialize` function (protected by `initializer`) and a `postInitialize` function. The `postInitialize` function, which sets critical external addresses, is protected by the `only tokenModule` modifier. While this pattern allows for flexible setup, it adds complexity to the deployment and configuration process. It requires careful management of the `tokenModule` role to ensure that the second initialization phase is executed correctly and securely, without front-running or misconfiguration.

**Recommendation:** Ensure that the `tokenModule` role is assigned to a highly secure, preferably multi-signature, address. Clearly document the sequence and dependencies of the initialization steps. Implement monitoring to detect any unauthorized attempts to call `postInitialize` or any other privileged functions. Consider adding a time-lock for the `postInitialize` call after the initial deployment to provide a window for verification.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa5b9...ffff`](https://bscscan.com/address/0xa5b977667117877d06e0e74bd6d85cf7e241ffff) |
| **Network** | BNB Chain |
| **Price** | $0.00009554 |
| **24h Volume** | $328.3K |
| **Liquidity** | $34.4K |
| **Volume / Liquidity** | 9.5× |
| **Token Age** | 14d |
| **Top-10 Holders** | 42.6% of supply |
| **Buy / Sell Tax** | 1.0% / 0.0% |
| **24h Transactions** | 1603 buys / 1345 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xe64159613b19dc63cd4700ade4fa5898cdf8eeaa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/4cat-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
