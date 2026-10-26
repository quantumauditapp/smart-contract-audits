---
token: Ninja Squad Token
ticker: NST
network: arbitrum
risk_score: 72
status: high
date: 2026-09-18
---

# Ninja Squad Token (NST) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ninja-squad-token-arb)

---

## Audit Summary

The audit of the BridgeToken (TokenImplementation) contract, intended for use as a Beacon proxy implementation, identified a critical vulnerability related to uninitialized proxy state, which could allow unauthorized ownership transfer. Further high-risk concerns involve potential storage collisions during future upgrades due to the custom storage layout. The contract utilizes standard libraries like OpenZeppelin's `Ownable` and `Counters`, but the proxy-specific initialization requires careful attention.

> **Final Recommendation:** Prioritize the implementation and rigorous testing of a robust `initialize()` function for the proxy contract. This function must correctly set the `owner` and other initial state variables within the proxy's storage, preventing unauthorized access to administrative functions. For future upgrades, strictly adhere to storage layout guidelines, ensuring that the `TokenStorage.State` struct is only appended to, and existing variable types or order are never modified, to prevent storage collisions. Conduct a comprehensive review of the full contract codebase, including the `initialize()` function and any upgrade-related logic, to ensure all proxy-specific considerations are addressed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages standard and well-tested libraries such as `Counters` and `Address`, demonstrating good practices for common utilities (7.2 Code Security). The use of `TokenStorage.State` for… |
| **Governance / Economics** | 1/10 | High | The contract implements `Ownable` for access control, centralizing administrative functions under a single owner (7.3 Access Control). This provides a clear governance structure for critical… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a Beacon proxy, utilizing the `TokenStorage` struct to manage state, which is a good practice for upgrade safety by isolating state variables (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `M-01` — `_setOwner` is Private in `Ownable`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_setOwner` function within the `Ownable` contract is declared as `private`. This prevents derived contracts from directly calling it to set the owner during their `initialize()` function. While the `Ownable` constructor calls it, this is problematic for proxies as the constructor's effect is on the implementation's storage, not the proxy's. This design forces reliance on the constructor for initial owner assignment, which is a common source of proxy initialization vulnerabilities.

**Recommendation:** Consider making `_setOwner` `internal` or providing an `internal` `__Ownable_init()` function that calls `_setOwner`. This would allow the `initialize()` function of the derived contract to explicitly set the owner in the proxy's storage, aligning with best practices for upgradeable contracts and reducing the risk of uninitialized state.


### `M-02` — Uninitialized Proxy State / Missing `initialize` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `Ownable` contract's constructor sets the `_owner` variable to `_msgSender()` upon deployment. In the context of an upgradeable proxy, this constructor is called only when the implementation contract itself is deployed, not when the proxy is initialized. Consequently, the `_owner` variable in the proxy's storage slot will remain uninitialized (zero address) unless an explicit `initialize()` function is called on the proxy. If such an `initialize()` function is missing or not properly invoked, any user could call `transferOwnership()` or other `onlyOwner` functions and claim ownership of the contract, leading to com

**Recommendation:** Implement a dedicated `initialize()` function in the implementation contract, protected by an `initialized` flag, which sets the `owner` and other initial state variables. This function must be called exactly once on the proxy after deployment. Ensure the `Ownable` constructor is either removed or modified to be proxy-aware, or that the `initialize()` function explicitly overrides the owner set by the constructor in the proxy's storage. Consider using OpenZeppelin's `Initializable` pattern.


### `M-03` — Potential Storage Collisions in Upgrades  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses a custom storage layout with `TokenStorage.State _state;` to encapsulate all state variables. While this pattern helps prevent storage collisions when adding new variables to the end of the struct, any modification to the internal structure of the `State` struct itself (e.g., reordering existing variables, changing their types, or inserting new variables in the middle) in a future upgrade could lead to storage collisions. This would corrupt existing state data, potentially rendering the contract unusable or leading to unexpected behavior.

**Recommendation:** Strictly adhere to storage layout guidelines for upgradeable contracts. When upgrading, only append new variables to the end of the `TokenStorage.State` struct. Never reorder, remove, or change the type of existing variables within the struct. Thoroughly test all upgrade scenarios in a development environment before deploying to production.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — a contract — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Truncated Code for Upgrade Logic  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `ERC1967Upgrade` contract is truncated. This prevents a full review of the complete upgrade mechanism, including how the beacon address is managed, who has the authority to update the implementation address within the beacon, and any associated access control or timelock mechanisms. While the prefill indicates a Beacon proxy, the full context of its management is not available for audit.

**Recommendation:** Provide the complete source code for all contracts involved in the upgrade mechanism, including the Beacon contract and any associated governance or administrative contracts. This ensures a comprehensive security review of the entire upgrade process (7.7 Upgrades, 7.3 Access Control, 7.5 Governance).


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.0% of supply. What remains: 48.2% in wallets, 1.9% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Ninja Squad Token (NST), market cap $11M, rank #1138.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $180K (DexScreener, all pools). 24h trading volume $74K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: mintable with no on-chain cap found. Control: a contract. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $180K of DEX liquidity across 3 pools. Launch: 907 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x88a2...0cfb`](https://arbiscan.io/address/0x88a269df8fe7f53e590c561954c52fccc8ec0cfb) |
| **Network** | Arbitrum |
| **Price** | $1.2700 |
| **24h Volume** | $73.9K |
| **Liquidity** | $176.3K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 50.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 243 buys / 198 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0x53d3e59faac08184720bcb2816f4cf5b36d6767d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ninja-squad-token-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-18*
