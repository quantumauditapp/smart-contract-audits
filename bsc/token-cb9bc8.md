---
token: 蝴蝶人生
ticker: 蝴蝶人生
network: bsc
risk_score: 34
status: low
date: 2026-09-12
---

# 蝴蝶人生 (蝴蝶人生) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-cb9bc8-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and state-based transitions. The audit identified a critical reentrancy vulnerability in the tax liquidation logic, which could lead to double processing of tax funds. Additionally, the contract exhibits centralized control by the owner and relies heavily on external, unaudited dependencies, posing significant operational and economic risks. While the use of OpenZeppelin upgradeable contracts provides a solid foundation, the identified issues require immediate attention.

> **Final Recommendation:** Address the critical reentrancy vulnerability in `_liquidateTax` by implementing a robust reentrancy guard that updates storage state before external calls, or by using OpenZeppelin's `ReentrancyGuard` modifier. Enhance security by considering a multi-signature wallet for ownership or implementing a more decentralized governance model to mitigate the risks associated with centralized control. Thoroughly audit all external dependencies (`ITaxProcessor`, `IDividend`) and consider adding mechanisms for updating these addresses or implementing emergency circuit breakers. Finally, evaluate the economic implications of the `liquidationThreshold` adjustment logic and consider adding a minimum floor or owner-controlled reset mechanism.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages OpenZeppelin's upgradeable ERC20, Ownable, and Permit modules, demonstrating a commitment to established standards (7.2 Code Security). The state-based tax mechanism is complex… |
| **Governance / Economics** | 6/10 | Medium | The contract's economic model is centered around a dynamic tax system and liquidation mechanism, with `maxSupply` being fixed at initialization (7.4 Economic). The `_liquidateTax` function includes… |
| **Upgrades** | 8/10 | Low | The contract is designed as an upgradeable proxy implementation, correctly utilizing OpenZeppelin's `Initializable` and `Upgradeable` patterns (7.7 Upgrades). The `_disableInitializers()` in the… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `C-01` — Reentrancy Vulnerability in `_liquidateTax`  *(Severity: Critical · Status: Unresolved)*

The `_liquidateTax` function, called by `_transfer`, attempts to prevent reentrancy by setting `currentPoolState.notLiquidating = false;` before making external calls to `ITaxProcessor.processTax` and `IDividend.distributeDividends`. However, `currentPoolState` is a local memory variable. The updated `poolState` (storage) is only written *after* these external calls complete. If an external call re-enters `_transfer` (and subsequently `_liquidateTax`), the `poolState.notLiquidating` in storage would still be `true` from the perspective of the re-entrant call, allowing the liquidation logic to execute again. This could lead to double processing of tax funds, unexpected state changes, or drai…

**Recommendation:** Implement a proper reentrancy guard using the Checks-Effects-Interactions pattern. Update the `poolState.notLiquidating` storage variable *before* any external calls are made. A robust solution would be to use OpenZeppelin's `ReentrancyGuard` modifier on the `_liquidateTax` function or ensure the storage variable `poolState.notLiquidating` is updated to `false` before any external calls and reverted to `true` only after all external calls have successfully completed.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract grants significant control to the `onlyOwner` for critical operations such as `startMigration` and `finalizeMigration`. While this provides clear administrative control, it introduces a single point of failure. A compromise of the owner's private key could lead to unauthorized manipulation of the token's state and tax mechanisms, potentially causing economic instability or loss of funds.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address to distribute control and reduce the risk of a single point of failure. Alternatively, explore transitioning to a more decentralized governance model (e.g., a DAO) for critical protocol decisions, or at least for the most sensitive functions.


### `M-02` — Critical External Dependency Risk  *(Severity: Medium · Status: Unresolved)*

The contract relies on external `ITaxProcessor` and `IDividend` contracts for core tax processing and dividend distribution. The addresses for these contracts are set during initialization and cannot be changed post-deployment. If these external contracts contain vulnerabilities, are malicious, or become unmaintained, they could lead to a denial of service for token transfers (if they revert) or a loss of collected tax funds (if they mismanage or are exploited).

**Recommendation:** Thoroughly audit the `ITaxProcessor` and `IDividend` contracts to ensure their security and reliability. Consider adding an `onlyOwner` function to allow updating these critical external addresses in case of an emergency or to facilitate upgrades of these dependencies. Implement circuit breakers or emergency stop functions that can disable or bypass these external calls if they become problematic.


### `L-01` — Lack of Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The contract lacks a general emergency pause mechanism (e.g., using OpenZeppelin's `Pausable` module) that could temporarily halt sensitive operations like token transfers. In the event of a critical bug discovery, a market exploit, or other unforeseen circumstances, the absence of such a mechanism could prevent the team from quickly mitigating damage.

**Recommendation:** Integrate OpenZeppelin's `PausableUpgradeable` contract. This would allow the owner (or a designated role) to pause and unpause transfers and other critical functions, providing a crucial safety net during emergencies.


### `I-01` — Immutability of `metaURI`  *(Severity: Informational · Status: Unresolved)*

The `metaURI` variable, which stores the token's metadata URI, is set during initialization and cannot be updated thereafter. While this ensures immutability, it removes the flexibility to change the URI if, for example, the hosting service changes, the link breaks, or the metadata itself needs to be updated.

**Recommendation:** If flexibility is desired for future updates, consider adding an `onlyOwner` function to allow modification of the `metaURI`. If the immutability is an intentional design choice, ensure this is clearly documented.


### `I-02` — Potential for Decreasing `liquidationThreshold`  *(Severity: Informational · Status: Unresolved)*

The `_liquidateTax` function includes logic to decrease the `liquidationThreshold` by 10% (`currentPoolState.liquidationThreshold * 9 / 10`) if the `taxAmount` is less than the current threshold. This mechanism could lead to a continuously decreasing threshold over time if collected tax amounts are frequently low. A very low `liquidationThreshold` might make it difficult to trigger the desired liquidation behavior, potentially accumulating large amounts of tax that are never processed.

**Recommendation:** Review the long-term economic implications of a continuously decreasing `liquidationThreshold`. Ensure this behavior aligns with the protocol's intended design. Consider implementing a minimum floor for the `liquidationThreshold` or providing an `onlyOwner` function to reset or adjust it if it drops to an undesirable level.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x87ae...7777`](https://bscscan.com/address/0x87ae267002cd1ea0ec86bf3601d4a8ad76a47777) |
| **Network** | BNB Chain |
| **Price** | $0.005144 |
| **24h Volume** | $1.56M |
| **Liquidity** | $251.6K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 20d |
| **Top-10 Holders** | 29.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11750 buys / 3261 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd4ae7dd719ec71594f13d0e3b17e65e9085f1ca1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-cb9bc8-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
