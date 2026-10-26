---
token: Euro Coin
ticker: EURC
network: ethereum
risk_score: 12
status: low
date: 2026-08-11
---

# Euro Coin (EURC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/euro-coin-eth)

---

## Audit Summary

This audit covers the FiatTokenV2_2 implementation contract, which serves as the logic for a proxy-based ERC-20 stablecoin. The contract introduces a new storage mechanism for balances and blacklist status, combining them into a single mapping. While the new bit-packing logic is technically sound, the upgrade path from previous versions (e.g., FiatTokenV1) that used separate storage mappings for balances and blacklisted accounts appears to be critically flawed. The `initializeV2_2` function only migrates blacklisted accounts, not existing token balances, leading to a high risk of data loss for all user balances upon upgrade. Other aspects, such as EIP-712 signature handling and access controls, are implemented robustly, but the upgrade safety issue overshadows these strengths.

> **Final Recommendation:** Prioritize a thorough review of the upgrade path, specifically focusing on storage layout compatibility and data migration strategies. If this contract was deployed as an upgrade from a version using separate `_balances` and `_blacklisted` mappings without a comprehensive balance migration, immediate action is required to address the potential data loss. Ensure all future upgrades include explicit, audited migration logic for any changes in storage layout affecting user data. Additionally, consider documenting the EIP-712 domain versioning strategy to clarify its relationship with contract versions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates strong technical implementation for its core functionalities, including robust EIP-712 signature handling for delegated operations and an efficient bit-packing mechanism for… |
| **Governance / Economics** | 9/10 | Low | The contract incorporates standard stablecoin governance features such as pausing and blacklisting, which are essential for emergency response and regulatory compliance (7.5 Governance). EIP-712… |
| **Upgrades** | 2/10 | High | The contract is designed as an upgradeable proxy implementation, featuring a versioned initializer (`initializeV2_2`) to manage upgrade logic (7.7 Upgrades). This initializer includes specific… |

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
| **Top-1 Unlocked Holder** | 13.7% |
| **Top-3 Unlocked** | 39.2% |

## Security Findings

_⚪ 9 Informational_

### `I-01` — Centralized Control by Privileged Roles  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract inherits functionalities such as pausing and blacklisting, which grant significant control to privileged roles (e.g., owner, pauser, blacklister). These roles can pause all transfers, blacklist specific accounts (preventing them from sending/receiving tokens), and potentially mint/burn tokens (inherited from parent contracts). While common for stablecoins to ensure regulatory compliance and emergency response, this centralization introduces a single point of failure and trust, as a compromise of these roles could have severe consequences.

**Recommendation:** Ensure that the private keys controlling these privileged roles are secured with the highest industry standards (e.g., multi-signature wallets, hardware security modules, robust access control policies). Consider implementing a time-lock mechanism for critical administrative actions to provide a window for community review or emergency intervention.


### `I-02` — Hardcoded EIP-712 Domain Version String  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_domainSeparator()` function uses `EIP712.makeDomainSeparator` with a hardcoded version string of `"2"`. While this is a common practice for EIP-712 domains, if future contract upgrades introduce significant changes to the EIP-712 message structures or authorization logic, maintaining a static domain version might lead to confusion or require careful external communication to users about which domain version corresponds to which contract version. It might also imply that all `FiatTokenV2.x` versions share the same EIP-712 domain, which should be explicitly documented.

**Recommendation:** Document the rationale behind the hardcoded EIP-712 domain version `"2"` and clarify its relationship to the contract's semantic versioning (e.g., `V2_2`). If future changes to EIP-712 message structures are anticipated, consider making the EIP-712 version string configurable or derive it from the contract's semantic version to avoid potential ambiguities.


### `I-03` — Blacklisting of Implementation Contract Address  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initializeV2_2` function explicitly calls `_blacklist(address(this))`, which blacklists the implementation contract itself. While implementation contracts are generally not intended to hold tokens, if tokens were accidentally sent to this address, they would become permanently locked and unrecoverable due to the blacklisting status. This is an edge case but represents a potential loss of funds if such an accidental transfer occurs.

**Recommendation:** Confirm that there are no scenarios where the implementation contract is expected to hold tokens. If there are, re-evaluate the necessity of blacklisting `address(this)`. Otherwise, ensure clear documentation and operational procedures are in place to prevent accidental token transfers to the implementation contract address.


### `I-04` — Critical Upgrade Storage Collision and Data Loss  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `FiatTokenV2_2` contract introduces a new storage mechanism by overriding `_balanceOf`, `_isBlacklisted`, `_setBalance`, and `_setBlacklistState` to use a single `balanceAndBlacklistStates` mapping. Previous versions, such as `FiatTokenV1`, utilized separate `_balances` and `_blacklisted` mappings. The `initializeV2_2` function, intended for upgrade logic, only migrates accounts from `_deprecatedBlacklisted` to the new `balanceAndBlacklistStates` format. Crucially, it lacks any migration logic for existing token balances stored in the `_balances` mapping from prior versions. This design flaw means that upon upgradi

**Recommendation:** If this contract was deployed as an upgrade from a version with separate `_balances` and `_blacklisted` mappings, an immediate and comprehensive audit of the upgrade process is required. A robust migration strategy must be implemented to transfer all existing token balances from the old `_balances` mapping to the new `balanceAndBlacklistStates` mapping during the upgrade. This typically involves a dedicated migration function or a more sophisticated proxy upgrade mechanism that handles storage…


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.9% of supply. What remains: 10.6% in wallets, 29.2% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as EURC (EURC), market cap $482M, rank #114. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $6.6M (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a single wallet (EOA) — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: EUR Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $6.6M of DEX liquidity across 13 pools. Launch: 1504 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1aba...c33c`](https://etherscan.io/address/0x1abaea1f7c830bd89acc67ec4af516284b1bc33c) |
| **Network** | Ethereum |
| **Price** | $1.1600 |
| **24h Volume** | $1.25M |
| **Liquidity** | $3.52M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 4y |
| **Top-10 Holders** | 39.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 40 buys / 99 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x95dbb3c7546f22bce375900abfdd64a4e5bd73d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/euro-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
