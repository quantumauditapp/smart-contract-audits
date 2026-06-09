---
token: BankrCoin
ticker: BNKR
network: base
risk_score: 90
status: critical
date: 2026-05-31
---

# BankrCoin (BNKR) — Smart Contract Security Analysis | Base

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bankrcoin-base)

---

## Audit Summary

The Clanker protocol facilitates the deployment of new ERC20 tokens, creation of Uniswap V3 liquidity pools, and locking of initial LP positions. The audit identified a critical bug in the Uniswap V3 pool initialization process, which will prevent the core functionality of the `deployToken` function from working correctly. Additionally, several high and medium severity issues related to economic risks, centralization, and potential deployment failures were found. The contract relies heavily on external Uniswap V3 components and a custom liquidity locker.

> **Final Recommendation:** The Clanker contract contains a critical bug that prevents its primary function from operating as intended. Immediate remediation of the Uniswap V3 pool initialization error (C-01) and the `maxUsableTick` issue (M-02) is essential. Furthermore, addressing the high centralization of control (H-02) and the `amountOutMinimum: 0` risk (H-01) is crucial for the protocol's long-term security and user confidence. A comprehensive review of all external interactions and parameter settings is recommended.

For enhanced security and a more robust deployment, consider a Premium Deploy option. This service includes a dedicated security engineer to assist with contract deployment, post-deployment monitoring, and immediate incident response, ensuring a secure launch and ongoing operational integrity.

## Security Analysis

The Clanker protocol facilitates the deployment of new ERC20 tokens, creation of Uniswap V3 liquidity pools, and locking of initial LP positions. The audit identified a critical bug in the Uniswap V3 pool initialization process, which will prevent the core functionality of the `deployToken` function from working correctly. Additionally, several high and medium severity issues related to economic risks, centralization, and potential deployment failures were found. The contract relies heavily on external Uniswap V3 components and a custom liquidity locker.

The Clanker contract contains a critical bug that prevents its primary function from operating as intended. Immediate remediation of the Uniswap V3 pool initialization error (C-01) and the `maxUsableTick` issue (M-02) is essential. Furthermore, addressing the high centralization of control (H-02) and the `amountOutMinimum: 0` risk (H-01) is crucial for the protocol's long-term security and user confidence. A comprehensive review of all external interactions and parameter settings is recommended.

For enhanced security and a more robust deployment, consider a Premium Deploy option. This service includes a dedicated security engineer to assist with contract deployment, post-deployment monitoring, and immediate incident response, ensuring a secure launch and ongoing operational integrity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical architecture leverages established standards like ERC20 and integrates with Uniswap V3, demonstrating a foundational understanding of DeFi primitives (7.1 Architecture). However, a criti |
| **Governance / Economics** | 6/10 | High | The contract exhibits high centralization, with the `owner` having sole control over critical parameters such as `taxRate`, `lpFeesCut`, `protocolCut`, `defaultLockingPeriod`, and the ability to depre |
| **Upgrades** | 6/10 | Low | The Clanker contract is not designed with an upgrade mechanism (7.7 Upgrades). Any future modifications or bug fixes would necessitate deploying an entirely new contract and migrating existing assets  |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Critical Bug: Incorrect Uniswap V3 Pool Initialization  *(Severity: Critical · Status: Unresolved)*

The `deployToken` function attempts to initialize the newly created Uniswap V3 pool by calling `IUniswapV3Factory(pool).initialize(sqrtPriceX96);`. However, `pool` is the address of the newly created Uniswap V3 pool, which implements the `IUniswapV3Pool` interface, not `IUniswapV3Factory`. Calling `initialize` on the `IUniswapV3Factory` interface at the pool's address will either revert or call a non-existent function, leaving the actual Uniswap V3 pool uninitialized and unusable for liquidity provision or swaps. This prevents the core functionality of the `deployToken` function from succeeding.

**Recommendation:** Cast the `pool` address to the correct interface, `IUniswapV3Pool`, before calling `initialize`. Ensure `IUniswapV3Pool` is imported and available. The corrected line should be `IUniswapV3Pool(pool).initialize(sqrtPriceX96);`.


### `H-01` — High Risk: `amountOutMinimum: 0` in Uniswap V3 Swaps  *(Severity: High · Status: Unresolved)*

Both the `deployToken` and `initialSwapTokens` functions perform Uniswap V3 swaps using `amountOutMinimum: 0`. This parameter specifies the minimum amount of `tokenOut` that must be received for the swap to succeed. Setting it to zero means the transaction will succeed regardless of the actual amount received, exposing the caller (the protocol in `deployToken` and `msg.sender` in `initialSwapTokens`) to significant slippage, sandwich attacks, and potential loss of funds, especially in volatile markets or with low liquidity.

**Recommendation:** Implement a mechanism to calculate and enforce a reasonable `amountOutMinimum` based on current market conditions, expected slippage, and a user-defined tolerance. This could involve an oracle call, a calculation based on the current price, or allowing the caller to specify a minimum amount. For `deployToken`, a protocol-defined minimum slippage tolerance should be enforced.


### `H-02` — High Risk: Excessive Centralization of Control  *(Severity: High · Status: Unresolved)*

The `Clanker` contract is `Ownable`, granting the contract owner sole control over critical parameters and operations. The owner can modify `taxRate`, `lpFeesCut`, `protocolCut`, `defaultLockingPeriod`, `taxCollector`, and toggle `bundleFeeSwitch` and `deprecated`. This high degree of centralization creates a single point of failure, where a compromised owner key could lead to significant financial loss, manipulation of fees, or complete shutdown of the protocol's core functionality.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for ownership of the contract to distribute control and require multiple approvals for critical operations. For less sensitive parameters, consider time-locked changes or a decentralized governance mechanism if the protocol intends to evolve towards decentralization.


### `M-01` — Medium Risk: Arbitrary `create2` Salt Constraint  *(Severity: Medium · Status: Unresolved)*

The `deployToken` function includes a `require(address(token) < weth, "Invalid salt")` condition. This constraint forces the `create2` deployment of the new `Token` contract to result in an address numerically smaller than the WETH address. This arbitrary requirement can significantly increase the computational cost and time required to find a suitable `_salt` value, potentially leading to deployment failures if a valid salt cannot be found efficiently. It also introduces an unnecessary complexity that could be exploited by front-runners trying to find a valid salt before the legitimate deployer.

**Recommendation:** Re-evaluate the necessity of the `address(token) < weth` constraint. If it's purely for aesthetic or ordering purposes, consider removing it to simplify deployments and reduce potential issues. If there's a critical technical reason, document it clearly and explore alternative, more robust methods to achieve the desired outcome without relying on brute-forcing salt values.


### `M-02` — Medium Risk: Missing `maxUsableTick` Definition/Usage in `MintParams`  *(Severity: Medium · Status: Unresolved)*

In the `deployToken` function, the `INonfungiblePositionManager.MintParams` struct is initialized with `maxUsableTick(tickSpacing)` for the `tickUpper` parameter. This appears to be a placeholder or a missing function call. `maxUsableTick` is not defined in the provided contract or interfaces, and it's not a standard Uniswap V3 `MintParams` field. This will likely result in a compilation error or a runtime error if it's interpreted as an undeclared variable, preventing successful LP position minting.

**Recommendation:** Clarify the intended value for `tickUpper`. If it's meant to be a calculated value, ensure the `maxUsableTick` function or constant is correctly defined and imported, or replace it with a valid calculation (e.g., `TickMath.MAX_TICK` or a calculated upper bound based on `tickSpacing`). If it's a typo, correct it to the appropriate `tickUpper` value.


### `L-01` — Low Risk: Restrictive `deadline` for LP Position Minting  *(Severity: Low · Status: Unresolved)*

The `deadline` parameter for `positionManager.mint` is set to `block.timestamp`. This means the transaction must be mined within the exact block it was created to be valid. If the transaction is delayed even by one block, it will revert. This creates a very narrow window for transaction inclusion and can lead to unnecessary transaction failures, especially during network congestion.

**Recommendation:** Set the `deadline` to `block.timestamp + X`, where `X` is a reasonable time duration (e.g., 10-20 minutes or `1200` seconds). This provides a sufficient window for the transaction to be mined without being overly permissive.


### `I-01` — Informational: Unchecked Return Value of Low-Level `call` for `taxCollector`  *(Severity: Informational · Status: Unresolved)*

The low-level `call` to `payable(taxCollector).call{value: protocolFees}("")` checks the `success` boolean but does not check the `returndata`. While for a simple ETH transfer, checking `success` is often sufficient, in more complex scenarios or if the `taxCollector` address could be a contract with a fallback function that reverts with a specific message, checking `returndata` could provide more detailed error information. In this specific case, the `if (!success) { revert("Failed to send protocol fees"); }` is adequate for a simple ETH transfer.

**Recommendation:** For simple ETH transfers, the current check is generally acceptable. However, as a best practice for future development or more complex interactions, consider checking `returndata` for more comprehensive error handling, especially if the recipient is a contract that might revert with specific messages.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x22af...6f3b`](https://basescan.org/address/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b) |
| **Network** | Base |
| **Price** | $0.0007036 |
| **24h Volume** | $1.05M |
| **Liquidity** | $3.03M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 33.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1578 buys / 1625 sells |

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

## Frequently Asked Questions

### Is BankrCoin a scam?

BankrCoin's status is not indicative of an outright scam based on available data. Its contract is verified, ownership is renounced, and no mint function exists, which are strong positive indicators against common scam tactics like malicious code or supply inflation. While liquidity is not locked, posing a risk, the low overall risk score of 18/100 suggests a generally positive security evaluation.

### Is BankrCoin safe to buy?

Investing in BankrCoin involves inherent risks. The primary concern is that liquidity is not locked, meaning the substantial liquidity pool could potentially be removed, leading to a drastic price drop. Additionally, the concentration of 33.2% of the supply among the top 10 holders presents a risk of market manipulation. Investors should weigh these factors against the low risk score and conduct personal due diligence.

### Has BankrCoin been audited?

BankrCoin's contract is verified, making its code publicly viewable for transparency. However, contract verification differs from a professional security audit, which involves a deep, independent review for vulnerabilities. The provided information does not confirm that BankrCoin has undergone such an audit. Investors should understand that verification alone does not guarantee security against all potential flaws.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xaec085e5a5ce8d96a7bdd3eb3a62445d4f6ce703)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bankrcoin-base)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-31*
