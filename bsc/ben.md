---
token: BEN
ticker: BEN
network: bsc
risk_score: 0
status: low
date: 2026-09-12
---

# BEN (BEN) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ben-bsc)

---

## Audit Summary

The FlapTaxTokenV3 contract implements an upgradeable ERC20 token with a dynamic tax mechanism and a multi-state pool system. The contract utilizes OpenZeppelin's upgradeable libraries and includes features like anti-farmer duration and tax liquidation. Key strengths include the use of battle-tested libraries, storage packing for gas efficiency, and robust initialization checks. However, potential reentrancy in the truncated `_liquidateTax` function, reliance on `block.timestamp` for critical state transitions, and integer truncation risks for packed state variables warrant attention. Centralized owner control over migration functions is also noted.

> **Final Recommendation:** It is recommended to implement reentrancy guards (e.g., ReentrancyGuard) for any external calls made within the `_liquidateTax` function to prevent potential fund manipulation. Review the initialization parameters for `START_LIQ_THRESHOLD` to ensure it does not exceed the `uint96` maximum, preventing silent truncation. Consider the implications of `block.timestamp` reliance for critical state changes and evaluate if a more robust time-based mechanism or a multi-signature wallet for owner functions would enhance security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract demonstrates good technical practices, leveraging OpenZeppelin's upgradeable ERC20 and Ownable implementations (7.2 Code Security). The `PackedPoolState` struct uses efficient storage… |
| **Governance / Economics** | 8/10 | Low | The economic model incorporates dynamic tax rates and anti-farmer mechanisms, with checks like `taxDuration >= antiFarmerDuration` ensuring logical consistency (7.4 Economic). The `maxSupply` is… |
| **Upgrades** | 9/10 | Low | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's `Initializable` and `Upgradeable` contracts, including `_disableInitializers()` in the constructor and the `initializer`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 23.8% |
| **Top-3 Unlocked** | 53.3% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Timestamp Dependence for Critical State Transitions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function relies on `block.timestamp` to determine critical state transitions, specifically for `taxExpirationTime` and `antiFarmerExpirationTime`. While `block.timestamp` is suitable for general time-based events, miners can manipulate it within a small window (up to 900 seconds on Ethereum, similar on BSC). This could allow a miner or a sophisticated attacker to slightly accelerate or delay the transition to `TaxFree` or `TaxEnforced` states, potentially impacting tax collection or anti-farmer mechanisms in a specific block.

**Recommendation:** For highly sensitive time-based events where precise timing is critical, consider using a time-weighted average oracle or a more robust time source if available and suitable for the use case. For less critical events, acknowledge the inherent miner manipulability of `block.timestamp` and ensure the impact of minor deviations is acceptable. In this context, the impact might be limited but should be understood.


### `M-02` — Integer Truncation Risk for Packed State Variables  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PackedPoolState` struct uses smaller integer types (`uint64`, `uint48`, `uint96`) for `taxExpirationTime`, `antiFarmerExpirationTime`, and `liquidationThreshold` respectively. During initialization, `initialLiquidationThreshold` (a `uint256`) is cast to `uint96` for `liquidationThreshold`. If `START_LIQ_THRESHOLD` (which sets `initialLiquidationThreshold`) is initialized with a value greater than `type(uint96).max` (approximately `7.9 * 10^28`), it will be silently truncated, leading to an incorrect and potentially exploitable `liquidationThreshold`. While `block.timestamp` is currently well within `uint48` and `u

**Recommendation:** Ensure that `START_LIQ_THRESHOLD` is always initialized with a value that fits within `uint96` to prevent silent truncation. Add a `require` statement in the `initialize` function to explicitly check `require(params.initialLiquidationThreshold <= type(uint96).max, 'Liquidation threshold too large');` or similar. For time-related variables, consider if `uint256` is more appropriate if durations could be exceptionally long, or add checks to ensure sums fit within the packed types.


### `M-03` — Potential Reentrancy in `_liquidateTax` Function  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_liquidateTax` function is called within the `_transfer` function. While the provided code is truncated, the presence of `ITaxProcessor` and `IDividend` interfaces strongly suggests that `_liquidateTax` will make external calls to these contracts. If these external calls are made before critical state updates (e.g., updating `poolState` or `balanceOf(address(this))`) or without proper reentrancy guards, a malicious external contract could re-enter `_transfer` or `_liquidateTax` to drain funds or manipulate the contract's state. This is a common vulnerability pattern in contracts interacting with external addresses

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard` or a custom mutex) on the `_liquidateTax` function and any other functions that make external calls and modify state. Ensure that all state changes related to the external call are completed before the call is made (Checks-Effects-Interactions pattern).


### `L-01` — Centralized Control Over Migration Functions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `startMigration` and `finalizeMigration` functions are protected by the `onlyOwner` modifier. This grants the contract owner exclusive control over initiating and completing the migration process, which involves critical state changes. While common for administrative functions, this centralization introduces a single point of failure. If the owner's private key is compromised, an attacker could manipulate the contract's state transitions related to migration.

**Recommendation:** For critical administrative functions, consider implementing a multi-signature wallet (e.g., Gnosis Safe) as the contract owner. This distributes control and requires multiple approvals for sensitive operations, significantly reducing the risk associated with a single compromised key. Alternatively, implement a time-lock mechanism for these functions to provide a window for users to react to pending changes.


### `I-01` — Initial Token Distribution to Deployer  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). During the `initialize` function, the entire `maxSupply` of tokens is minted to `msg.sender` (the deployer of the proxy contract). This means that initially, all tokens are held by a single address. While this is a common pattern for initial token distribution, it implies that the deployer has full control over the initial supply and subsequent distribution.

**Recommendation:** This is an informational finding and not a vulnerability in itself. However, it is important for transparency and to ensure that the project's token distribution strategy is clearly communicated to the community. If not already planned, consider a clear and secure strategy for distributing these tokens to avoid centralization concerns or potential market manipulation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7bc7...7777`](https://bscscan.com/address/0x7bc70ae0f2a67d2fdc0180a697a611f21c857777) |
| **Network** | BNB Chain |
| **Price** | $0.0024 |
| **24h Volume** | $1.05M |
| **Liquidity** | $207.4K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 5d |
| **Top-10 Holders** | 20.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3550 buys / 2841 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8f6814bd5db791fc8b64eea6bbad8bbeb508d6c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ben-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*
