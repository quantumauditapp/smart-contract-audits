---
token: 中国人能飞火箭
ticker: 中国人能飞
network: bsc
risk_score: 38
status: medium
date: 2026-09-27
---

# 中国人能飞火箭 (中国人能飞) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-edf71e-bsc)

---

## Audit Summary

The audit of FlapTaxTokenV3, an upgradeable ERC20 token with a complex multi-state tax mechanism, was conducted. A significant portion of the critical `_liquidateTax` function was truncated, preventing a full assessment of its security and economic implications. Key findings include high centralization risks due to the owner controlling the entire initial token supply and critical state transitions, alongside potential reentrancy vulnerabilities in the incomplete liquidation logic. The contract utilizes standard OpenZeppelin upgradeable patterns, which appear correctly implemented.

> **Final Recommendation:** It is critical to provide the complete source code for the `_liquidateTax` function to enable a thorough security review of its reentrancy risks, gas efficiency, and economic impact. Consider mechanisms to decentralize control over the initial token supply and critical state transitions to reduce single points of failure. Implement robust monitoring for owner-controlled functions and external contract interactions. Thoroughly test all state transitions and tax calculations, especially given the complexity of the multi-state tax machine.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a multi-state tax system and overrides the `_transfer` function to apply custom logic, including calling `_liquidateTax`. The use of `PackedPoolState` is a gas-efficient… |
| **Governance / Economics** | 4/10 | Medium | The economic model is centered around a dynamic tax system and a liquidation mechanism. A major concern is the initial minting of the entire `maxSupply` to the deployer (7.4 Economic), granting the… |
| **Upgrades** | 8/10 | Low | The contract correctly utilizes OpenZeppelin's `Initializable` and `__Ownable_init` patterns for upgradeability (7.7 Upgrades). The constructor disables initializers, preventing re-initialization… |

## Security Findings

_🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Truncated Critical Liquidation Logic  *(Severity: High · Status: Unresolved)*

The `_liquidateTax` function, which is called on every `_transfer` and is central to the token's economic model and state transitions, is significantly truncated in the provided source code. This prevents a full security assessment of potential reentrancy vulnerabilities, external call risks, gas consumption, and the overall economic stability and fairness of the tax and liquidation mechanism (7.2 Code Security, 7.4 Economic).

**Recommendation:** Provide the complete and verified source code for the `_liquidateTax` function to allow for a comprehensive security audit. Without the full implementation, critical vulnerabilities may remain undetected.


### `H-02` — Centralized Control of Initial Token Supply  *(Severity: High · Status: Unresolved)*

The `initialize` function mints the entire `maxSupply` (1 billion tokens) directly to the contract deployer (`msg.sender`), who is also the owner. This grants the owner complete control over the initial token distribution, posing a significant centralization risk and potential for market manipulation or unfair distribution (7.4 Economic, 7.5 Governance).

**Recommendation:** Consider a more decentralized or transparent mechanism for initial token distribution, such as a vesting schedule, a public sale, or a multi-signature wallet for managing the initial supply. This reduces the single point of failure and increases trust.


### `M-01` — Potential Reentrancy in `_liquidateTax` (Due to Truncation)  *(Severity: Medium · Status: Unresolved)*

The `_liquidateTax` function is called on every `_transfer` and is likely to contain external calls (e.g., to `taxProcessor`, `dividendContract`, or `v2Router` for swaps) in its truncated part. If these external calls are made before critical state updates or without proper reentrancy guards (like OpenZeppelin's `nonReentrant` modifier), the contract could be vulnerable to reentrancy attacks (7.2 Code Security).

**Recommendation:** Upon providing the full `_liquidateTax` source code, ensure that all external calls adhere to the Checks-Effects-Interactions pattern. Implement reentrancy guards (e.g., `nonReentrant` from OpenZeppelin) on functions that make external calls and modify critical state, especially if they are called within the `_transfer` flow.


### `M-02` — Critical Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `onlyOwner` role has significant control over critical state transitions, specifically `startMigration` and `finalizeMigration`, which directly impact the token's operational state and tax enforcement. This centralization introduces a single point of failure, where a compromised owner key could lead to unauthorized state changes or manipulation of the token's tax mechanics (7.3 Access Control, 7.5 Governance).

**Recommendation:** Implement a multi-signature wallet for the owner address to enhance security. Consider introducing a time-lock for critical owner-controlled operations to provide a window for community review or intervention. Explore mechanisms for progressive decentralization of these controls over time.


### `L-01` — Complex Multi-State Tax Machine  *(Severity: Low · Status: Unresolved)*

The contract implements a complex multi-state tax system (`BondingCurve`, `Migrating`, `TaxEnforcedAntiFarmer`, `TaxEnforced`, `TaxFree`) with various conditions for state transitions and tax application. While designed for specific tokenomics, this complexity increases the surface area for logical errors and makes auditing, understanding, and maintaining the contract more challenging (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Ensure comprehensive unit and integration tests cover all possible state transitions and tax calculation scenarios. Provide detailed documentation and flowcharts explaining the state machine logic and its intended behavior to minimize misinterpretations and potential errors.


### `I-01` — Reliance on `block.timestamp` for Expiration  *(Severity: Informational · Status: Unresolved)*

The `taxExpirationTime` and `antiFarmerExpirationTime` variables rely on `block.timestamp` for their calculation and comparison. While common, `block.timestamp` can be manipulated by miners within a small range (up to 900 seconds on Ethereum, similar on BSC), which could slightly influence the precise timing of state transitions (7.2 Code Security).

**Recommendation:** For time-sensitive operations, consider using `block.number` and average block times if precise, unmanipulable timing is critical. However, for expiration times of this nature, `block.timestamp` is generally considered acceptable, and the risk is low.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1088...7777`](https://bscscan.com/address/0x108876c3df3d893350e9b780563b3697aa3e7777) |
| **Network** | BNB Chain |
| **Price** | $0.0006463 |
| **24h Volume** | $469.9K |
| **Liquidity** | $94.4K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | 18.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1986 buys / 1541 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8650b97cc260125119d8c6fbe7cce69a2676ee49)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-edf71e-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*
