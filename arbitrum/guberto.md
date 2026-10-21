---
token: GUBERTO
ticker: GUBERTO
network: arbitrum
risk_score: 85
status: critical
date: 2026-09-15
---

# GUBERTO (GUBERTO) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/guberto-arb)

---

## Audit Summary

The GuCoin contract implements an ERC-20 token with LayerZero OFT capabilities, integrating with a bonding curve and liquidity manager for its economic model. Key features include dynamic supply management, fee distribution, and automated LP seeding. The audit identified a high-severity reentrancy risk in ETH transfers, medium-severity issues related to fee configuration and LP seeding mechanics, and a low-severity concern regarding unaccounted ETH. The contract's reliance on external contracts also introduces dependency risks.

> **Final Recommendation:** Address the identified reentrancy vulnerability in `burnCurve` by implementing a reentrancy guard or using `transfer` for ETH payments. Carefully review and test the fee distribution logic in `_seedLP` to ensure that the sum of all distributed fees does not exceed 100% of the available WETH, considering all fee recipients. Consider the implications of the `_seedLP` trigger mechanism and potential front-running, possibly by making the fee distribution to the caller more deterministic or by having a dedicated function for LP seeding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The GuCoin contract demonstrates a well-structured architecture, leveraging immutable state variables for critical addresses and parameters (7.1 Architecture). It inherits from LayerZero's OFT for… |
| **Governance / Economics** | 1/10 | High | The economic model centers around a bonding curve, with `VIRTUAL_BALANCE`, `INITIAL_SUPPLY`, and `MAX_SUPPLY` defining token dynamics (7.4 Economic). Fees are distributed to the creator, protocol… |
| **Upgrades** | 3/10 | High | The GuCoin contract is not designed with upgradeability in mind (7.7 Upgrades). All critical addresses and parameters are set as `immutable` in the constructor, ensuring their immutability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Reentrancy Risk in `burnCurve` ETH Transfer  *(Severity: High · Status: Unresolved)*

The `burnCurve` function performs an external call `bondingCurve.call{value: amountETH}("")` after modifying `accETH` and burning tokens. While `_validateBondingCurve()` restricts calls to the `bondingCurve` contract, if the `bondingCurve` contract is malicious or compromised, it could re-enter the `GuCoin` contract and potentially drain funds or manipulate state before the transaction completes. This violates the Checks-Effects-Interactions pattern.

**Recommendation:** Implement a reentrancy guard (e.g., OpenZeppelin's `ReentrancyGuard`) on the `burnCurve` function. Alternatively, consider using `transfer` instead of `call` for fixed gas stipend, or ensure that all state changes are completed before any external calls are made.


### `M-01` — Fee Distribution Vulnerability in `_seedLP`  *(Severity: Medium · Status: Unresolved)*

The `_seedLP` function distributes WETH to `creator`, `owner()`, and `caller` based on `PROTOCOL_FEE` and `CREATOR_FEE`. Specifically, `creator` receives `CREATOR_FEE / 10_000`, `owner()` receives `PROTOCOL_FEE / 10_000`, and `caller` receives `CREATOR_FEE / 20_000`. If the sum of these percentages (i.e., `1.5 * CREATOR_FEE + PROTOCOL_FEE`) exceeds `10_000` (representing 100%), the contract will attempt to transfer more WETH than it holds, causing a revert and preventing LP seeding. This is a configuration risk.

**Recommendation:** Ensure that the sum of `1.5 * CREATOR_FEE + PROTOCOL_FEE` is always less than or equal to `10_000`. Implement a check in the constructor or a setter function (if fees were mutable) to enforce this invariant. Thoroughly test fee calculations with various valid and edge-case values.


### `M-02` — `_seedLP` Triggered by Last Buyer  *(Severity: Medium · Status: Unresolved)*

The `_seedLP` function, which seeds the liquidity pool and distributes a portion of the `CREATOR_FEE` to the `caller`, is triggered when `totalSupply()` reaches `MAX_SUPPLY` during a `mint` operation. This design means the last buyer to mint tokens could potentially be front-run by another user to become the `caller` and receive the `CREATOR_FEE / 20_000` portion. This introduces an element of unpredictability and potential for gas wars or unfair distribution.

**Recommendation:** Consider alternative mechanisms for triggering `_seedLP` and distributing the `caller`'s fee. Options include: (1) having a dedicated, permissioned function for LP seeding, (2) distributing the `caller`'s fee to a more deterministic address (e.g., the `creator` or `owner`), or (3) implementing a mechanism to prevent front-running for this specific transaction.


### `L-01` — Unaccounted ETH in `_seedLP`  *(Severity: Low · Status: Unresolved)*

The `_seedLP` function wraps `address(this).balance` into WETH for distribution. If ETH is sent directly to the `GuCoin` contract (e.g., via `selfdestruct` from another contract, or a direct `send`/`transfer` from an EOA) *after* the constructor but *before* `_seedLP` is called, this unaccounted ETH would be included in the LP seeding and fee distribution. This could lead to unintended beneficiaries receiving a portion of this extra ETH or an inflated LP.

**Recommendation:** Ensure that the `GuCoin` contract does not receive ETH directly outside of its intended `mint` function (which is restricted to the `bondingCurve`). If direct ETH transfers are not intended, consider adding a `receive()` or `fallback()` function that reverts to prevent accidental or malicious ETH deposits. If ETH is expected, ensure it's accounted for in the economic model.


### `I-01` — Centralization Risk via External Contracts  *(Severity: Informational · Status: Unresolved)*

The `GuCoin` contract heavily relies on the security and correct functioning of several external contracts, including `IGuBondingCurve`, `IGuLiquidityManager`, and `IGuFactory`. These contracts are immutable addresses set in the constructor. A compromise, malfunction, or malicious upgrade in any of these external dependencies could directly impact the `GuCoin`'s operations, economic model, and overall integrity. (7.6 External)

**Recommendation:** Ensure that all external contracts integrated with `GuCoin` undergo rigorous security audits and are managed by trusted entities. Implement robust monitoring for these external dependencies to detect any unusual behavior promptly. While the addresses are immutable, the logic within those contracts is critical.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4727...9b40`](https://arbiscan.io/address/0x4727a7d2022e99ee5c298513b730307f458f9b40) |
| **Network** | Arbitrum |
| **Price** | $0.0003106 |
| **24h Volume** | $114.6K |
| **Liquidity** | $30.1K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 89.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 188 buys / 136 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xa45410c3764d5e6ffb4ab68e08635b7dbb8b7deb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/guberto-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*
