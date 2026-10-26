---
token: Coinbase Wrapped BTC
ticker: CBBTC
network: base
risk_score: 9
status: low
date: 2026-08-11
---

# Coinbase Wrapped BTC (CBBTC) — Smart Contract Security Analysis | Base

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-base)

---

## Audit Summary

This audit covers the FiatTokenV2_1 contract, which serves as an implementation for an upgradeable proxy. The analysis focuses on the `initializeV2_1` function and general security practices. While the contract utilizes well-vetted libraries like OpenZeppelin's SafeMath and SafeERC20, specific logic within the upgrade initialization introduces medium-level risks related to critical state changes and potential misconfiguration. The provided source code for inherited contracts and libraries was truncated, limiting a full comprehensive analysis of all dependencies.

> **Final Recommendation:** Thoroughly review the design implications of blacklisting the token contract itself and ensure this aligns with all intended operational scenarios and external integrations. Implement robust access control and multi-signature protection for the `initializeV2_1` function to prevent unauthorized or erroneous execution. Consider upgrading to a more recent Solidity compiler version to benefit from enhanced security features and optimizations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good architectural practices (7.1 Architecture) by inheriting from a base token contract and utilizing well-audited OpenZeppelin libraries for SafeMath and SafeERC20… |
| **Governance / Economics** | 9/10 | Low | The contract relies on a centralized administrative model for upgrades and critical state changes, such as the `initializeV2_1` function which transfers contract-held tokens and blacklists the… |
| **Upgrades** | 2/10 | High | The system employs a proxy pattern, allowing for future upgrades. The `FiatTokenV2_1` contract represents an upgrade, introducing the `initializeV2_1` function. This function is critical for the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 4.1% |

## Security Findings

_🟡 1 Medium · 🟢 2 Low · ⚪ 6 Informational_

### `M-01` — Critical State Changes in `initializeV2_1`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_1` function performs two highly impactful operations: it transfers the entire balance of the token contract (`balances[address(this)]`) to a `lostAndFound` address, and then blacklists the token contract itself (`blacklisted[address(this)] = true`). If the `lostAndFound` address is incorrect, or if blacklisting the contract prevents it from performing necessary future operations (e.g., receiving tokens, interacting with other protocols), it could lead to a denial of service or loss of funds. The rationale and implications of blacklisting the contract address should be thoroughly documented and verifie

**Recommendation:** Ensure the `lostAndFound` address is correctly configured and immutable after initialization. Clearly document the intended purpose and long-term implications of blacklisting the token contract address. Verify that this action does not inadvertently break any existing or future integrations or functionalities of the token.


### `L-01` — Checks-Effects-Interactions Pattern Violation in `initializeV2_1`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_1` function performs an internal `_transfer` to an external `lostAndFound` address before updating critical state variables (`blacklisted[address(this)]` and `_initializedVersion`). While `_transfer` is internal and less prone to reentrancy than direct external calls, the general security best practice (Checks-Effects-Interactions pattern) dictates that all state changes should occur before any external interactions. This minimizes the window for reentrancy or unexpected behavior if the external call were to trigger unforeseen side effects.

**Recommendation:** Reorder the operations within `initializeV2_1` to update `blacklisted[address(this)] = true` and `_initializedVersion = 2` *before* calling `_transfer(address(this), lostAndFound, lockedAmount)`. This adheres to the Checks-Effects-Interactions pattern, enhancing robustness.


### `L-02` — Use of Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is compiled with `pragma solidity 0.6.12`. While functional, this version is older. Newer Solidity versions (e.g., 0.8.x) introduce several security enhancements, such as default checked arithmetic for `uint256` operations (preventing overflow/underflow without explicit SafeMath calls), more explicit error handling, and improved gas optimizations. Sticking to older versions might miss out on these built-in security features and potential future compiler bug fixes.

**Recommendation:** Consider upgrading the Solidity compiler version to a more recent stable release (e.g., 0.8.x). This would allow for the removal of explicit SafeMath library usage, simplifying the code and leveraging native compiler checks for arithmetic safety. Thorough testing would be required after such an upgrade.


### `I-01` — Incomplete Source Code for Dependencies  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for `FiatTokenV2` (the base contract) and parts of the `EIP712` library were truncated. This limits the ability to perform a complete and comprehensive security analysis, particularly regarding potential storage collisions in the upgradeable proxy context, or specific logic within the inherited token functionality (e.g., the exact implementation of `_transfer` or other critical functions).

**Recommendation:** For a full audit, ensure all dependent contract source codes are provided in their entirety. This allows for a complete analysis of inheritance, storage layout, and inter-contract interactions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.5% of supply. What remains: 1.0% in wallets, 90.5% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Coinbase Wrapped BTC (CBBTC), market cap $7.7B. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $99.0M (DexScreener, all pools). 24h trading volume $2.4M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a single wallet (EOA) — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $99.0M of DEX liquidity across 28 pools. Launch: 365 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcbb7...33bf`](https://basescan.org/address/0xcbb7c0000ab88b473b1f5afd9ef808440eed33bf) |
| **Network** | Base |
| **Price** | $80,993.3600 |
| **24h Volume** | $2.43M |
| **Liquidity** | $18.10M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 495 buys / 446 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x70acdf2ad0bf2402c957154f944c19ef4e1cbae1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
