---
token: Asteroid Shiba
ticker: ASTEROID
network: bsc
risk_score: 50
status: high
date: 2026-08-15
---

# Asteroid Shiba (ASTEROID) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 50/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/asteroid-shiba-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a multi-stage tax mechanism. A critical finding is the absence of the `_processTax` function's implementation, which is central to the token's economic model and prevents a full security assessment of tax handling. Other significant risks include the highly centralized initial token supply and the potential for denial of service if the `_processTax` function were to revert. The contract utilizes OpenZeppelin's upgradeable patterns and standard ERC20 features.

> **Final Recommendation:** It is imperative to provide the complete source code for the `_processTax` function to enable a thorough security assessment of the core tax mechanism. Address the high centralization of token supply by implementing a transparent and secure distribution strategy. Consider adding owner-controlled setter functions for critical external contract addresses to enhance operational flexibility without requiring full contract upgrades. Thoroughly test the complex state machine transitions and the `_liquidateTax` function to ensure robustness against edge cases and potential denial of service scenarios.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1) is complex due to its multi-state tax machine, increasing the surface for logic errors. A critical code security (7.2) issue is the missing implementation of the… |
| **Governance / Economics** | 4/10 | Medium | The economic model (7.4) presents a high risk due to the entire `maxSupply` being minted to the owner during initialization, leading to extreme centralization and potential market manipulation.… |
| **Upgrades** | 8/10 | Low | The contract is designed for upgradeability (7.7) using OpenZeppelin's `Initializable` and `Upgradeable` patterns, including `_disableInitializers()` in the constructor. This indicates a UUPS proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 81.9% |
| **Top-3 Unlocked** | ⚠️ 90.4% |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing Critical Function Implementation (`_processTax`)  *(Severity: Critical · Status: Unresolved)*

The `_processTax` internal function, which is responsible for handling and distributing collected taxes, is called within `_liquidateTax` but its implementation is not provided in the source code. This function is central to the token's economic model and its absence prevents a full security assessment of the tax mechanism, potentially hiding severe vulnerabilities such as reentrancy, incorrect distribution, or stuck funds.

**Recommendation:** Provide the complete and verified source code for the `_processTax` function. This function must be thoroughly audited for reentrancy, integer overflows/underflows, correct fund handling, and interaction with external contracts (`ITaxProcessor`, `IDividend`, `v2Router`).


### `H-01` — Centralized Token Supply  *(Severity: High · Status: Unresolved)*

During initialization, the entire `maxSupply` of tokens is minted to the `msg.sender` (the contract owner). This grants the owner 100% of the token supply, enabling potential market manipulation, rug pulls, or other adverse economic impacts if not managed transparently and securely. This level of centralization poses a significant risk to token holders and the protocol's integrity.

**Recommendation:** Implement a clear and transparent token distribution strategy. This could involve vesting schedules, multi-signature wallets for large holdings, or mechanisms for decentralized distribution to mitigate the risks associated with a single entity holding the entire supply.


### `H-02` — Potential Denial of Service from `_processTax`  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function is called at the beginning of every `_transfer` operation. If the unimplemented `_processTax` function (which is called by `_liquidateTax`) were to revert for any reason (e.g., due to an issue in an external call, insufficient funds, or a bug), all subsequent `_transfer` operations would be blocked. This would lead to a complete denial of service for all token holders, preventing any token movements.

**Recommendation:** Ensure the `_processTax` function is robust and handles all potential failure scenarios gracefully. Consider implementing error handling mechanisms, such as try-catch blocks for external calls, or a circuit breaker pattern to temporarily disable tax processing without halting all transfers if a critical issue arises. Thoroughly test `_processTax` under various conditions, including low liquidity or external contract failures.


### `M-01` — Immutability of Key External Contract Addresses  *(Severity: Medium · Status: Unresolved)*

Critical external contract addresses such as `taxProcessor`, `dividendContract`, `v2Router`, `quoteToken`, and `mainPool` are set only during the `initialize` function and lack owner-controlled setter functions. This means if any of these external dependencies need to be updated (e.g., due to an exploit, deprecation, or upgrade of the external service), the `FlapTaxTokenV3` contract itself would require an upgrade, which is a more complex, costly, and potentially risky operation than a simple setter function.

**Recommendation:** Consider implementing `onlyOwner` setter functions for these critical external contract addresses. This would allow for greater operational flexibility and responsiveness to changes in the ecosystem without necessitating a full contract upgrade.


### `M-02` — Reliance on `block.timestamp` for Critical State Transitions  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function uses `block.timestamp` to determine `taxExpirationTime` and `antiFarmerExpirationTime` and to trigger state changes (e.g., `PoolState.TaxFree`, `PoolState.TaxEnforced`). While common, `block.timestamp` can be manipulated by miners within a certain range (e.g., up to 900 seconds on Ethereum). This could allow miners or sophisticated attackers to front-run or back-run state transitions if the exact timing has significant economic implications, potentially exploiting tax rate changes or anti-farmer durations.

**Recommendation:** While `block.timestamp` is often the only available time source, be aware of its manipulability. If precise, unmanipulable timing is critical for economically sensitive state transitions, consider alternative mechanisms like Chainlink Keepers or a time oracle, or ensure that the economic impact of minor time manipulation is acceptable.


### `L-01` — Complex State Machine Logic  *(Severity: Low · Status: Unresolved)*

The contract implements a multi-stage `PoolState` machine (`BondingCurve`, `Migrating`, `TaxEnforcedAntiFarmer`, `TaxEnforced`, `TaxFree`) with intricate transition logic, especially within `_liquidateTax` and `_transfer`. Such complexity increases the likelihood of subtle logic errors or unexpected behavior, even with thorough testing, and can make the contract harder to reason about and maintain.

**Recommendation:** Ensure comprehensive unit and integration tests cover all possible state transitions and edge cases within the `PoolState` machine. Consider adding clear Natspec documentation for each state and transition condition to improve clarity and maintainability.


### `I-01` — Gas Overhead from `_liquidateTax` on Every Transfer  *(Severity: Informational · Status: Unresolved)*

The `_liquidateTax` function is invoked at the beginning of every `_transfer` call. This design choice ensures timely tax processing and state updates but adds a fixed gas overhead to every token transfer, regardless of whether tax is actually collected or liquidated in that specific transaction. For high-frequency transfers, this could lead to higher transaction costs for users.

**Recommendation:** This is a design trade-off. If gas efficiency becomes a significant concern, consider alternative mechanisms for triggering tax liquidation, such as a periodic `onlyOwner` call or a pull-based system, though this might introduce other complexities or delays in tax processing.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3309...7777`](https://bscscan.com/address/0x330990dae53bca4c5811c5362b44c33a47db7777) |
| **Network** | BNB Chain |
| **Price** | $0.001027 |
| **24h Volume** | $957.0K |
| **Liquidity** | $145.5K |
| **Volume / Liquidity** | 6.6× |
| **Token Age** | 14d |
| **Top-10 Holders** | 25.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3262 buys / 2138 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x60c04117753e634fe2d0587493613aaccdd0329c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/asteroid-shiba-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
