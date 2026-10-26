---
token: GameStop
ticker: GMEB
network: bsc
risk_score: 8
status: low
date: 2026-08-14
---

# GameStop (GMEB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gamestop-bsc)

---

## Audit Summary

The audit of the SecuritiesToken contract, an upgradeable ERC-20 token, revealed a robust architecture leveraging OpenZeppelin standards for access control and upgradeability. Key strengths include comprehensive role-based access control for critical functions and integration with compliance and pause mechanisms. However, the contract exhibits a high degree of centralization in the DEFAULT_ADMIN_ROLE, critical dependencies on external contracts, and the economic implications of its UI multiplier mechanism. Upgradeability also introduces inherent risks.

> **Final Recommendation:** Implement multi-signature wallets or time-locked governance for the `DEFAULT_ADMIN_ROLE` and the BeaconProxy admin to decentralize control and enhance security. Thoroughly vet and monitor all external contract dependencies, especially `ComplianceClient` and `PauseManagerClient`. Establish clear policies and transparent communication for any changes to the UI multiplier to maintain user trust and economic stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good technical practices, utilizing OpenZeppelin's upgradeable patterns and access control. The `_update` function correctly integrates compliance and pause checks (7.2 Code… |
| **Governance / Economics** | 9/10 | Low | The economic model includes a UI multiplier that can be adjusted by authorized roles, which could lead to user confusion or economic instability if not managed transparently (7.4 Economic). The… |
| **Upgrades** | 5/10 | Medium | The contract is designed for upgradeability using the BeaconProxy pattern and OpenZeppelin's upgradeable contracts, including `__gap` storage for future compatibility (7.7 Upgrades). This allows for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 26.8% |
| **Top-3 Unlocked** | 55.9% |

## Security Findings

_🟡 2 Medium · ⚪ 10 Informational_

### `M-01` — Economic Impact of UI Multiplier  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC8056BaseUpgradeable` introduces a UI multiplier that can significantly alter the perceived value of tokens. The `_setUIMultiplier` function, callable by `onlyAdminOrIssuer` (after `_authorizeMultiplierUpdate`), allows changing this multiplier within defined bounds. While bounds are present, an unexpected or frequent change in the multiplier could confuse users, impact integrations, or lead to economic instability if not communicated clearly and managed carefully (7.4 Economic).

**Recommendation:** Establish clear policies and procedures for managing the UI multiplier. Ensure transparent communication with users and integrated platforms regarding any planned multiplier changes. Consider adding a timelock for multiplier updates to allow users to react.


### `M-04` — Critical External Dependencies  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract relies on external `ComplianceClient` and `PauseManagerClient` contracts, whose addresses can be set by the `DEFAULT_ADMIN_ROLE`. A malicious or compromised external contract, or an incorrectly set address, could lead to a complete halt of token operations (via `PauseManagerClient`) or arbitrary restrictions on transfers (via `ComplianceClient`). This introduces significant external dependency risks (7.6 External, 7.8 Operations).

**Recommendation:** Thoroughly vet and secure the external `ComplianceClient` and `PauseManagerClient` contracts. Implement robust monitoring for changes to these addresses and consider a timelock for `setCompliance` and `setPauseManager` functions.


### `I-01` — Role Definition via keccak256  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ISSUER_ROLE` is defined using `keccak256("ISSUER_ROLE")`. While this is a standard and secure practice for defining roles in OpenZeppelin's `AccessControl`, it's important to ensure that the string literal used is unique and consistent across all related contracts and off-chain systems to prevent role collision or misinterpretation (7.2 Code Security).

**Recommendation:** Document all role definitions and their corresponding string literals clearly. Ensure that any external systems interacting with these roles use the exact same string literals for `keccak256` hashing.


### `I-02` — Centralized Control and Single Point of Failure  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power, including setting token name/symbol/identifier, enabling/disabling mint/burn, and configuring critical external contracts (`ComplianceClient`, `PauseManagerClient`). This high degree of centralization means a compromise of the admin key could lead to full control over the token's functionality and potentially its economic parameters. While common for security tokens, this presents a significant operational risk (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for the `DEFAULT_ADMIN_ROLE` to mitigate the risk of a single point of failure.


### `I-03` — Upgradeability Risks  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is deployed as an implementation behind a BeaconProxy, allowing its logic to be upgraded by the BeaconProxy's admin. While OpenZeppelin's upgradeable patterns are used correctly (e.g., `__gap` storage, `initializer` functions), the ability to upgrade introduces a trust assumption. A malicious upgrade could introduce new vulnerabilities or change contract behavior unexpectedly (7.7 Upgrades).

**Recommendation:** Secure the admin key of the BeaconProxy with a multi-signature wallet or a robust governance mechanism. Implement a transparent upgrade process, including public announcements and audit reports for new implementations, to maintain user trust.


### `I-04` — Missing Zero Address Check for Admin in Initialization  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). In the `__securitiesToken_init` function, the `admin_` address passed to `_grantRole(DEFAULT_ADMIN_ROLE, admin_)` is not checked for being `address(0)`. While the `issuers_` array elements are checked, a `DEFAULT_ADMIN_ROLE` assigned to `address(0)` would effectively lock out administrative control, rendering the contract unmanageable (7.2 Code Security).

**Recommendation:** Add a check `if (admin_ == address(0)) revert ZeroAddress();` at the beginning of the `__securitiesToken_init` function to prevent accidental assignment of the admin role to the zero address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.9% of supply. What remains: 64.9% in wallets, 15.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GameStop (bStocks Tokenized Stock) (GMEB), market cap $7M, rank #1446. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $347K (DexScreener, all pools). 24h trading volume $2.4M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $347K of DEX liquidity across 4 pools. Launch: 2 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x46ce...b15c`](https://bscscan.com/address/0x46ceefda28dd7207059ed19b0acdc026955bb15c) |
| **Network** | BNB Chain |
| **Price** | $19.3500 |
| **24h Volume** | $2.42M |
| **Liquidity** | $335.7K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 79.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 44328 buys / 40389 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x908d49048eb3a7bedfd238972403842805eaf2be)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gamestop-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
