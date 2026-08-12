---
token: DBURN
ticker: DBURN
network: bsc
risk_score: 9
status: low
date: 2026-08-12
---

# DBURN (DBURN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dburn-bsc)

---

## Audit Summary

The BurnToken contract implements a custom ERC20 token with dynamic tax phases, a pool burning mechanism, and integration with external tax processors and DEX routers. The audit identified a high-severity reentrancy vulnerability in the tax processing logic, a medium-severity risk due to reliance on external contracts for core economic functions, and other minor issues. The contract demonstrates good initialization practices and includes a reentrancy guard for stair tax swaps, but the identified reentrancy in the `processTax` call requires immediate attention.

> **Final Recommendation:** Address the identified reentrancy vulnerability by implementing a reentrancy guard around the `ITaxProcessor.processTax` call. Evaluate the economic implications of external contract failures and consider alternative strategies or stronger assurances for critical tax processing and swapping functions. Review the centralization aspects of owner and token deployer roles, potentially exploring multi-signature wallets or time-locks for critical operations to enhance security and decentralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract exhibits robust initialization logic and comprehensive parameter validation (7.1 Architecture). A reentrancy guard (`_swappingStairTax`) is correctly implemented for stair tax swaps… |
| **Governance / Economics** | 7/10 | Low | The economic model features dynamic tax phases and an automated pool burning mechanism, which are configurable and contribute to tokenomics (7.4 Economic). The `taxWhitelist` and `tradingOpenTime`… |
| **Upgrades** | 10/10 | Low | The BurnToken contract is not designed as an upgradeable proxy, thus eliminating direct upgrade-related risks (7.7 Upgrades). A `markMigrated` function exists for specific `LaunchType.Curve`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Reentrancy Vulnerability in `processTax` Call  *(Severity: High · Status: Unresolved)*

The `_update` function, specifically within the `if (useTaxProcessor)` block, makes an external call to `ITaxProcessor(taxProcessor).processTax` without a reentrancy guard. Although `_swapAccruedStairTax` (called earlier in the same block) is protected by `_swappingStairTax`, the `processTax` call is not. A malicious `taxProcessor` contract could reenter the `BurnToken` contract and manipulate balances or state variables before the main transfer `super._update(from, to, value - taxAmount)` is completed, leading to potential fund loss or incorrect accounting.

**Recommendation:** Implement a reentrancy guard (e.g., a `nonReentrant` modifier or a boolean flag like `_swappingStairTax`) around the external call to `ITaxProcessor(taxProcessor).processTax` to prevent reentrant calls. Ensure that the guard is set before the external call and reset after it, or use OpenZeppelin's `ReentrancyGuard`.


### `M-01` — Reliance on External Contracts for Core Economic Logic  *(Severity: Medium · Status: Unresolved)*

The contract's core economic functions, such as tax processing via `ITaxProcessor` and stair tax swapping via `IUniswapV2Router`, rely on external contracts. While `try/catch` blocks are used to handle potential reverts from these external calls, a failure means that the intended tax collection or conversion might not occur, impacting the protocol's economic model. This introduces a dependency risk where the protocol's financial integrity is tied to the robustness and availability of these external systems.

**Recommendation:** Assess the potential impact of `ITaxProcessor` and `IUniswapV2Router` failures on the protocol's economics. Consider implementing fallback mechanisms or clearer communication to users if taxes cannot be processed or swapped. Ensure that the chosen external contracts are highly reliable and audited. Document the implications of these external dependencies for users and stakeholders.


### `L-01` — Unconventional `approve` Function Behavior  *(Severity: Low · Status: Unresolved)*

The `approve` function overrides the standard ERC20 behavior by calling `_executePoolBurn()` before returning. While `_executePoolBurn` is a public utility function designed to burn tokens from the DEX pair, triggering a burn on every `approve` call is an unconventional design choice. This might be unexpected for users or other protocols interacting with the token, potentially leading to confusion or unintended side effects in integrations that assume standard ERC20 `approve` semantics.

**Recommendation:** Consider separating the `_executePoolBurn` call from the `approve` function. If the intent is to ensure regular burning, rely on external calls to `executePoolBurn()` or integrate it into other frequently called functions where its side effect is more intuitive. Clearly document this behavior if it is an intentional design choice.


### `I-01` — Centralization Risk with Owner and Token Deployer Roles  *(Severity: Informational · Status: Unresolved)*

The `owner` (inherited from Ownable) and `tokenDeployer` roles hold significant power within the contract. The `owner` can `setTaxWhitelist`, allowing specific addresses to bypass taxes. The `tokenDeployer` can `markMigrated`, which is critical for `LaunchType.Curve`. While common for new token deployments, this introduces a centralization risk where a compromised private key for either role could lead to manipulation of the token's tax structure or migration status.

**Recommendation:** For enhanced security and decentralization, consider implementing a multi-signature wallet for the `owner` and `tokenDeployer` roles. Additionally, explore time-locks for critical administrative actions to provide a window for community review or intervention in case of a compromised key. Clearly communicate the extent of administrative control to the community.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdd2f...3333`](https://bscscan.com/address/0xdd2fee7fc438aea520e2678e9ddbebc5b7b63333) |
| **Network** | BNB Chain |
| **Price** | $0.0912 |
| **24h Volume** | $408.2K |
| **Liquidity** | $254.7K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 5d |
| **Top-10 Holders** | 45.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2795 buys / 1001 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x12ca5bdf5fae4b0fe7d2855c6799ae09218d6874)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dburn-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
