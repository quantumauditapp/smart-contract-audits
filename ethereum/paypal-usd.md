---
token: PayPal USD
ticker: PYUSD
network: ethereum
risk_score: 9
status: low
date: 2026-08-11
---

# PayPal USD (PYUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/paypal-usd-eth)

---

## Audit Summary

The audit covers the PYUSD token contract, an ERC-20 compatible stablecoin implementation utilizing an upgradeable proxy pattern. The contract leverages OpenZeppelin's AccessControl for role-based permissions, enabling centralized control over critical functions such as pausing, freezing addresses, and managing token supply via an external `SupplyControl` contract. While the code quality is generally high and follows established patterns, the inherent centralization and reliance on external components introduce significant governance and economic risks. Upgradeability is well-structured, though the presence of deprecated storage variables warrants careful management.

> **Final Recommendation:** It is crucial to implement robust security measures for all privileged roles (DEFAULT_ADMIN_ROLE, PAUSE_ROLE, ASSET_PROTECTION_ROLE), ideally through multi-signature wallets or time-locked contracts, to mitigate the risks associated with centralized control. A thorough audit and continuous monitoring of the external `SupplyControl` contract are essential, as its integrity directly impacts the token's supply mechanics. For future upgrades, carefully manage the deprecated storage variables to ensure no collisions occur and that the storage layout remains consistent.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical implementation (7.2 Code Security) demonstrates good practices, utilizing Solidity 0.8.x for automatic overflow/underflow checks and custom errors for robust handling. Standard ERC-20… |
| **Governance / Economics** | 9/10 | Low | The contract exhibits a high degree of centralization (7.5 Governance, 7.4 Economic), which is typical for a stablecoin but represents a significant risk. The `DEFAULT_ADMIN_ROLE` can change the… |
| **Upgrades** | 2/10 | High | The contract is designed for upgradeability using an `AdminUpgradeabilityProxy` and adheres to OpenZeppelin's upgradeable patterns (7.7 Upgrades), including `_disableInitializers()` and `__gap`… |

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
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `M-03` — Critical Reliance on External `SupplyControl` Contract  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `increaseSupplyToAddress` and `decreaseSupplyFromAddress` functions (minting and burning logic) delegate critical permission checks to an external `supplyControl` contract. The security and correct configuration of this external contract are paramount. If the `supplyControl` contract is compromised, misconfigured, or contains vulnerabilities, it could allow unauthorized minting, burning, or manipulation of the token supply, leading to a loss of peg or trust.

**Recommendation:** Ensure the `SupplyControl` contract itself undergoes rigorous security audits and is managed with the highest security standards. Implement robust monitoring for any changes or suspicious activity related to the `SupplyControl` contract. Consider implementing circuit breakers or emergency mechanisms in the main token contract to mitigate risks if the `SupplyControl` contract becomes compromised.


### `L-01` — Public `initialize` Function  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function is declared as `public`. While the `_getInitializedVersion()` and `_initialize()` logic from OpenZeppelin's `Initializable` pattern prevents re-initialization, making it safe, it is generally a best practice to restrict access to `initialize` to prevent accidental calls or to make its purpose clearer. In a proxy setup, `initialize` is typically called only once by the proxy admin.

**Recommendation:** Consider adding an `onlyProxyAdmin` or similar modifier to the `initialize` function if it's intended to be called exclusively by the proxy administrator, or if the `_initialize` function itself doesn't already restrict access sufficiently. This improves clarity and reduces the attack surface, even if the current implementation is functionally safe.


### `I-01` — Non-Standard Decimal Count (6 Decimals)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The PYUSD token uses 6 decimals, which is a non-standard choice for many ERC-20 tokens, where 18 decimals are most common (e.g., ETH, USDC, USDT). While this is a design decision and not a vulnerability in the contract itself, it can lead to compatibility issues or unexpected behavior when interacting with DeFi protocols, exchanges, or wallets that are primarily designed or assume 18-decimal tokens. Users and integrators must be explicitly aware of this difference.

**Recommendation:** Ensure all documentation, user interfaces, and integration guides prominently highlight that PYUSD uses 6 decimals. Developers integrating with PYUSD should be advised to explicitly handle the decimal conversion to avoid precision errors or miscalculations.


### `I-02` — Centralized Control and Single Points of Failure  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract design grants significant power to several privileged roles. The `DEFAULT_ADMIN_ROLE` can set the `supplyControl` contract, which governs minting and burning. The `ASSET_PROTECTION_ROLE` can freeze/unfreeze addresses and wipe their balances, directly affecting user funds. The `PAUSE_ROLE` can halt all token transfers. This high degree of centralization, while common for stablecoins, creates multiple single points of failure where the compromise or misuse of any associated private key could lead to severe financial losses or operational disruption.

**Recommendation:** Implement multi-signature wallets or time-locked contracts for all privileged roles (DEFAULT_ADMIN_ROLE, PAUSE_ROLE, ASSET_PROTECTION_ROLE) to introduce a higher level of security and prevent single points of failure. Clearly document the responsibilities and operational procedures for each role.


### `I-03` — Deprecated Storage Variables  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BaseStorage` contract contains numerous `Deprecated` variables (e.g., `ownerDeprecated`, `assetProtectionRoleDeprecated`, `supplyControllerDeprecated`). While the `__gap_BaseStorage` array is correctly used for upgradeability, the presence of these deprecated variables indicates past storage layout changes. Without careful management, this could lead to confusion, unintended interactions, or potential storage collisions in future upgrades if not properly accounted for, especially if these slots were previously active and their data needs to be explicitly handled or discarded.

**Recommendation:** Maintain clear documentation of all storage layout changes, including the purpose and fate of deprecated variables. During future upgrades, meticulously verify the storage layout to ensure no collisions occur with current or future variables. Consider explicitly clearing or zeroing out deprecated storage slots if their data is no longer relevant to prevent accidental re-use or misinterpretation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.0% of supply. What remains: 63.6% in wallets, 24.4% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PayPal USD (PYUSD), market cap $3.0B, rank #36. Its owner (0x3af3…024b) controls 3 issuer-backed coins CoinGecko lists on ethereum, $3.1B together, among them BUSD, Pax Dollar: one issuer's programme, read on-chain. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $140.9M (DexScreener, all pools). 24h trading volume $51.6M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a single wallet (EOA) — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin — issuer-backed (fiat reserves)  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Fiat-backed Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $140.9M of DEX liquidity across 19 pools. Launch: 209 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x6c3e...a0e8`](https://etherscan.io/address/0x6c3ea9036406852006290770bedfcaba0e23a0e8) |
| **Network** | Ethereum |
| **Price** | $1.0001 |
| **24h Volume** | $51.57M |
| **Liquidity** | $100.15M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 88.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 135 buys / 186 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe63e32b2ae40601662f760d6bf5d771057324fbd97784fe1d3717069f7b75d45)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/paypal-usd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
