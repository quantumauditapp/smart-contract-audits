---
token: Apple
ticker: AAPLB
network: bsc
risk_score: 11
status: low
date: 2026-08-30
---

# Apple (AAPLB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apple-bsc)

---

## Audit Summary

The audit focused on the `SecuritiesToken` contract, which serves as the implementation for a BeaconProxy. The contract implements an upgradeable ERC-20 token with custom scaling (`ERC8056BaseUpgradeable`), access control, compliance, and pause functionalities. While the contract leverages well-audited OpenZeppelin libraries for upgradeability and access control, several areas of concern were identified, primarily related to centralized administrative power, the broad authority granted to the 'Issuer' role, and dependencies on external contracts. A critical missing zero-address check for the admin during initialization was also noted. The `ERC8056BaseUpgradeable` code was truncated, limiting a full review of its complex scaling logic.

> **Final Recommendation:** Strengthen access control by implementing a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control. Re-evaluate the scope of the `ISSUER_ROLE`'s permissions, specifically regarding the ability to authorize multiplier updates, and consider restricting this sensitive function to the `DEFAULT_ADMIN_ROLE` only. Implement a zero-address check for the `admin_` parameter in the `initialize` function to prevent accidental deployment into an unmanageable state. Ensure that all external dependencies, such as the `ComplianceClient` and `PauseManagerClient`, are thoroughly audited and managed by trusted entities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture is sound, utilizing OpenZeppelin's upgradeable contracts and access control patterns (7.1 Architecture, 7.2 Code Security). The contract correctly implements `__gap`… |
| **Governance / Economics** | 9/10 | Low | The contract exhibits a high degree of centralization, with the `DEFAULT_ADMIN_ROLE` possessing extensive control over critical parameters, role management, and external dependencies (7.3 Access… |
| **Upgrades** | 5/10 | Medium | The contract is designed as an upgradeable implementation for a BeaconProxy, correctly utilizing OpenZeppelin's upgradeable patterns (7.7 Upgrades). The `__gap` storage variable is present, ensuring… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 53.5% |
| **Top-3 Unlocked** | ⚠️ 91.9% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 9 Informational_

### `M-04` — Issuer Role Can Authorize Multiplier Updates  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_authorizeMultiplierUpdate()` function, which is a prerequisite for changing the `_uiMultiplier`, is accessible to both `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE` via the `onlyAdminOrIssuer` modifier. Changes to the `_uiMultiplier` directly impact the token's value and user balances. Granting this powerful ability to potentially multiple `ISSUER_ROLE` holders increases the attack surface for economic manipulation or accidental misconfiguration, as the `ISSUER_ROLE`'s primary function is typically related to minting/burning, not economic parameter adjustments.

**Recommendation:** Restrict the `_authorizeMultiplierUpdate()` function to only the `DEFAULT_ADMIN_ROLE`. This ensures that only the most trusted and secure role can initiate changes to the token's core economic scaling factor.


### `L-01` — Inconsistent Pragma Version  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The main `SecuritiesToken.sol` contract uses `pragma solidity ^0.8.20;` while the imported `ERC8056BaseUpgradeable.sol` uses `pragma solidity ^0.8.24;`. Although both versions are compatible with a compiler version of 0.8.24 (as indicated in the prefill), maintaining a consistent pragma across all contract files is a best practice for clarity and to avoid potential future compiler-related issues or warnings.

**Recommendation:** Standardize the pragma version across all contract files to `pragma solidity ^0.8.24;` or the specific version used for compilation.


### `I-01` — Truncated `ERC8056BaseUpgradeable` Code  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The provided source code for the `ERC8056BaseUpgradeable` contract was truncated. This contract is fundamental to the `SecuritiesToken`'s core token mechanics, particularly its scaled amount (`_uiMultiplier`) logic. A complete security assessment of the `SecuritiesToken`'s economic model and potential for integer overflows/underflows or rounding errors within the scaling mechanism requires a full review of the `ERC8056BaseUpgradeable` implementation.

**Recommendation:** Provide the complete source code for all inherited and imported contracts to enable a comprehensive security audit of the entire system.


### `I-02` — Centralized Control by DEFAULT_ADMIN_ROLE  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power, including the ability to set token name/symbol/identifier, enable/disable minting/burning, manage all roles (including `ISSUER_ROLE`), and set the addresses for the `ComplianceClient` and `PauseManagerClient`. A compromise of this single role would grant an attacker full control over the token's functionality and potentially its economic parameters.

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control and require multiple approvals for critical operations. This significantly reduces the risk of a single point of failure.


### `I-03` — Missing Zero Address Check for Admin in Initializer  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function grants the `DEFAULT_ADMIN_ROLE` to the `admin_` address provided. However, there is no check to ensure that `admin_` is not `address(0)`. If the contract is initialized with `admin_` as `address(0)`, no entity would possess the `DEFAULT_ADMIN_ROLE`, rendering the contract unmanageable and unable to perform critical administrative functions (e.g., setting compliance, pause manager, or granting other roles).

**Recommendation:** Add a `require(admin_ != address(0), "ZeroAddress");` check at the beginning of the `__securitiesToken_init` function to prevent initialization with a zero address admin.


### `I-04` — Dependency on External Compliance and Pause Manager Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SecuritiesToken` contract relies heavily on external `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts, whose addresses are set by the `DEFAULT_ADMIN_ROLE`. The security and trustworthiness of these external contracts are paramount, as a malicious or compromised `ComplianceClient` could block legitimate transfers or allow non-compliant ones, and a malicious `PauseManagerClient` could permanently pause the token or pause it at will, effectively freezing all token operations.

**Recommendation:** Ensure that the `ComplianceClient` and `PauseManagerClient` contracts are thoroughly audited, well-secured, and controlled by trusted entities, ideally through a multi-signature setup. Implement robust monitoring for these external contracts. Consider adding a time-lock or governance mechanism for changing these critical external contract addresses.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.4% of supply. What remains: 83.8% in wallets, 9.6% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Apple (bStocks Tokenized Stock) (AAPLB), market cap $5M, rank #1589. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $435K (DexScreener, all pools). 24h trading volume $402K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $435K of DEX liquidity across 7 pools. Launch: 31 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x431a...9b7a`](https://bscscan.com/address/0x431a3bee82e2ca41e49895cbece5bb0f76a89b7a) |
| **Network** | BNB Chain |
| **Price** | $320.6500 |
| **24h Volume** | $402.4K |
| **Liquidity** | $373.6K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 93.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3818 buys / 3335 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xe9b9998b2ec5430d2246c7f1f8d9f298c97d7365)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apple-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*
