---
token: United Stables
ticker: U
network: bsc
risk_score: 82
status: critical
date: 2026-08-13
---

# United Stables (U) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 82/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-stables-bsc)

---

## Audit Summary

The StablecoinV2 contract, an upgradeable ERC20 token, introduces EIP-7598 authorization features. The audit identified a critical upgradeability flaw in the base contract, `Stablecoin`, due to a missing `__gap` variable. High centralization of control over core token functions and potential front-running risks for authorization cancellations were also noted. The contract leverages OpenZeppelin's upgradeable patterns and includes features like `autoMint` and `frozen` accounts, managed by distinct roles.

> **Final Recommendation:** Address the critical upgradeability issue by adding a `__gap` variable to the `Stablecoin` base contract to ensure storage compatibility for future upgrades. Review the extent of centralized control, particularly for minting and freezing functions, and consider implementing additional safeguards or decentralization measures if feasible for the protocol's long-term vision. Users should be made aware of the front-running risk associated with `cancelAuthorization` and advised on best practices for transaction submission.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture (7.1) leverages OpenZeppelin's upgradeable contracts and EIP-7598 for signature-based transfers, enhancing functionality. Code security (7.2) is generally good, using… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4) and governance (7.5) are highly centralized, with an `owner` (multisig) controlling minting, pausing, freezing accounts, and setting `autoMintMaxLimit` (H-01). An… |
| **Upgrades** | 1/10 | High | The contract utilizes OpenZeppelin's `TransparentUpgradeableProxy` pattern (7.7) and correctly implements `initializer` and `reinitializer` functions for `Stablecoin` and `StablecoinV2` respectively.… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-4 |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `C-01` — Missing `__gap` in Base Contract for Upgradeability  *(Severity: Critical · Status: Unresolved)*

The `Stablecoin` base contract, which `StablecoinV2` inherits from, does not include a `__gap` storage variable. This is crucial for upgradeable contracts to prevent storage collisions if new state variables are added to the base contract in future upgrades, or if `StablecoinV2` adds new state variables that conflict with future `Stablecoin` state variables. While `StablecoinV2` itself has a `__gap`, the base contract's omission creates a significant risk for the overall upgradeability pattern (7.7 Architecture).

**Recommendation:** Add `uint256[50] private __gap;` (or an appropriately sized array) to the `Stablecoin` contract to ensure future storage compatibility and prevent potential storage collisions.


### `H-01` — Centralized Control of Core Token Functions  *(Severity: High · Status: Unresolved)*

The contract exhibits significant centralization (7.3 Access Control, 7.5 Governance), with the `owner` (a 2/4 multisig) having control over critical functions such as `mint`, `pause`, `freeze` accounts, `setAutoMintMaxLimit`, and enabling/disabling EIP-7598 features. Additionally, an `autoOwner` role can `autoMint` up to a specified limit. While a multisig mitigates some risk, a compromise of the multisig or malicious actions by its members could lead to severe consequences, including arbitrary token minting, freezing user funds, or halting operations.

**Recommendation:** Evaluate if any of these highly centralized functions can be decentralized or made subject to a more robust governance mechanism (e.g., time-locks, community voting) if the protocol's roadmap allows. Clearly communicate the extent of centralized control to users.


### `M-01` — Front-running Risk for `cancelAuthorization`  *(Severity: Medium · Status: Unresolved)*

The `cancelAuthorization` function allows an `authorizer` to invalidate a previously issued authorization by marking its `nonce` as used. However, if an attacker observes a pending `cancelAuthorization` transaction, they could front-run it by submitting a `transferWithAuthorization` or `receiveWithAuthorization` transaction using the same `nonce` before the cancellation is processed. This could lead to an unauthorized transfer of funds despite the authorizer's intent to cancel (7.2 Code Security).

**Recommendation:** While inherent to signature-based systems, users should be aware of this risk. Consider implementing a mechanism where `cancelAuthorization` can be submitted with a higher gas price to increase its chances of being included first, or advise users to ensure their cancellation transactions are prioritized.


### `M-02` — Potential for `autoMintMaxLimit` to be Set to Zero  *(Severity: Medium · Status: Unresolved)*

The `setAutoMintMaxLimit` function allows the `owner` to set the `autoMintMaxLimit` to any `uint256` value, including zero. If the limit is set to zero, the `autoMint` function would become unusable, as `require(autoMintMaxLimit >= amount, ...)` would fail for any `amount > 0`. While this might be an intentional 'kill switch' for `autoMint`, it could also be set accidentally, disrupting operations (7.4 Economic).

**Recommendation:** Consider adding a `require(limit > 0 \|\| limit == 0)` if setting to zero is intended as a disable, or `require(limit > 0)` if `autoMint` should always be available. Document the intended behavior of setting `autoMintMaxLimit` to zero.


### `L-01` — `block.timestamp` Reliance for `validAfter`/`validBefore`  *(Severity: Low · Status: Unresolved)*

The `_transferOrReceiveWithAuthorization` function relies on `block.timestamp` for checking `validAfter` and `validBefore`. While generally acceptable, `block.timestamp` can be manipulated by miners within a certain range (up to 900 seconds on Ethereum, similar on BSC). This could slightly extend or shorten the validity window of an authorization, potentially allowing a transaction to be included just outside the intended window (7.2 Code Security).

**Recommendation:** Acknowledge this inherent EVM characteristic. For most applications, the precision of `block.timestamp` is sufficient. If extreme precision is required, consider alternative time sources or adjust validity windows to account for potential miner manipulation.


### `I-01` — Unused `_msgSender()` in `mint` event  *(Severity: Informational · Status: Unresolved)*

In the `mint(uint256 amount)` function, the `Mint` event is emitted with `_msgSender()` as both `caller` and `to`. However, the `_mint` function itself mints to `_msgSender()`. The `to` parameter in the event is redundant in this specific overload, as it will always be the same as `caller` (7.2 Code Security).

**Recommendation:** Consider removing the `to` parameter from the `Mint` event in this specific overload, or ensure consistency if `_msgSender()` is always the recipient. This is a minor stylistic point.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xce24...6666`](https://bscscan.com/address/0xce24439f2d9c6a2289f741120fe202248b666666) |
| **Network** | BNB Chain |
| **Price** | $1.0003 |
| **24h Volume** | $447.8K |
| **Liquidity** | $21.02M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 93.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3463 buys / 615 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa0909f81785f87f3e79309f0e73a7d82208094e4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-stables-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
