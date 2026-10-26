---
token: EURC
ticker: EURC
network: base
risk_score: 9
status: low
date: 2026-07-24
---

# EURC (EURC) — Smart Contract Security Analysis | Base

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eurc-base)

---

## Audit Summary

This audit covers the FiatTokenV2_2 contract, which serves as the implementation logic for a USDC stablecoin proxy on the Base network. The contract implements ERC-20 functionalities, EIP-712 signed messages, and a custom blacklisting mechanism. The codebase is generally well-structured and follows established patterns for stablecoin operations, including upgradeability. Key findings highlight the inherent centralization risks typical for stablecoins and the complexity introduced by a non-standard blacklist storage method.

> **Final Recommendation:** It is recommended to enhance the security posture of critical administrative roles, particularly the proxy admin, by transitioning from a single EOA to a robust multi-signature wallet with a high threshold or a time-locked governance mechanism. Thorough internal documentation for the custom blacklist storage mechanism should be maintained to mitigate future integration risks. Additionally, ensure comprehensive testing of upgrade paths on testnets, especially for functions involving state migrations like `initializeV2_2`, to prevent potential issues during live deployments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture (7.1) is robust, leveraging an upgradeable proxy pattern and EIP-712 for off-chain signed transactions. Code security (7.2) is generally strong, with appropriate checks for… |
| **Governance / Economics** | 9/10 | Low | The economic model (7.4) is that of a centralized stablecoin, backed by fiat reserves, which inherently carries a high level of governance risk (7.5). Critical functions such as blacklisting… |
| **Upgrades** | 2/10 | High | The contract utilizes a ZeppelinOS legacy proxy pattern, allowing for seamless upgrades of the token logic (7.7). The `initializeV2_2` function is designed for a controlled, single-time execution… |

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
| **Top-1 Unlocked Holder** | 34.0% |
| **Top-3 Unlocked** | 76.6% |

## Security Findings

_🟢 1 Low · ⚪ 9 Informational_

### `L-02` — Reliance on `_chainId()` for EIP-712 Domain Separator  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_domainSeparator()` function uses `_chainId()` (which retrieves the chain ID via assembly) as part of the EIP-712 domain separator. While standard practice for EIP-712, if the contract were to be deployed on a chain with an unexpected chain ID, or if a chain's ID were to change (highly improbable for established networks), it would invalidate all existing EIP-712 signatures, requiring users to re-sign (7.2 Code Security, 7.6 External).

**Recommendation:** This is generally robust for stable chains like Base. No direct action is required, but it's a consideration for deployment on new or less stable networks, or if the contract were to be forked to a chain with a different ID, as it would necessitate re-issuing signatures.


### `I-01` — Single-Use Upgrade Initialization Function  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_2` function includes a `require(_initializedVersion == 2);` check, ensuring it can only be called once and only when the previous version was correctly initialized. This is a standard and secure pattern for upgradeable contracts. However, if the initialization process were to fail mid-execution (e.g., due to an out-of-gas error or an unexpected revert within the `accountsToBlacklist` loop), the function could not be retried, potentially leaving the contract in an inconsistent state (7.7 Upgrades, 7.8 Operations).

**Recommendation:** Ensure that the `accountsToBlacklist` array is processed efficiently and within gas limits, especially for large lists. Consider robust pre-deployment testing of the upgrade path on a testnet with realistic data to minimize the risk of failure during the single allowed execution.


### `I-02` — Centralized Control and Single Point of Failure  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract design, typical for a centralized stablecoin, grants significant power to a small set of privileged addresses (admin, owner, pauser, blacklister). These roles can pause transfers, blacklist accounts, and control contract upgrades. The proxy's admin is an EOA, representing a single point of failure for upgradeability and overall contract control. A compromise of this EOA could lead to unauthorized upgrades or manipulation of critical contract functions (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** While inherent to stablecoin design, consider implementing multi-signature wallets or a time-locked governance mechanism for critical administrative functions, especially the proxy admin, to reduce the risk associated with a single EOA compromise. This enhances operational security and resilience against key loss.


### `I-03` — Non-Standard Balance and Blacklist Storage Mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract employs a custom storage mechanism where `balanceAndBlacklistStates` uses a single `uint256` to store both an account's balance (lower 255 bits) and its blacklist status (most significant bit). While the implementation appears correct and includes checks like `_balance <= ((1 << 255) - 1)` to prevent overflow into the blacklist bit, this non-standard approach increases complexity and could be a source of subtle bugs or integration issues if not perfectly maintained or understood by external systems (7.1 Architecture, 7.2 Code Security).

**Recommendation:** Ensure thorough internal documentation and testing for this custom storage logic. Future upgrades or integrations should exercise extreme caution when interacting with or modifying this specific storage pattern to prevent unintended side effects or data corruption.


### `I-04` — Self-Blacklisting in `initializeV2_2`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_2` function explicitly blacklists the contract's own address (`_blacklist(address(this))`). While this might be intended to prevent tokens from being accidentally sent to and locked within the contract itself, it is an unusual pattern that could have unforeseen implications for future interactions or integrations if not fully understood by all parties (7.2 Code Security, 7.8 Operations).

**Recommendation:** Document the precise rationale behind blacklisting the contract address. Confirm that this action does not interfere with any expected contract functionalities, such as receiving tokens from other contracts, or future upgrade paths that might require the contract to hold tokens temporarily.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.8% of supply. What remains: 31.3% in wallets, 16.5% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as EURC (EURC), market cap $482M, rank #114. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.3M (DexScreener, all pools). 24h trading volume $6.3M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a single wallet (EOA) — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: EUR Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $4.3M of DEX liquidity across 30 pools. Launch: 365 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x60a3...db42`](https://basescan.org/address/0x60a3e35cc302bfa44cb288bc5a4f316fdb1adb42) |
| **Network** | Base |
| **Price** | $1.1600 |
| **24h Volume** | $6.31M |
| **Liquidity** | $2.14M |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 47.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1155 buys / 1250 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe846373c1a92b167b4e9cd5d8e4d6b1db9e90ec7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eurc-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
