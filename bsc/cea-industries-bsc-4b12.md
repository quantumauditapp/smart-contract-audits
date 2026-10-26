---
token: CEA Industries
ticker: BNCB
network: bsc
risk_score: 12
status: low
date: 2026-09-17
---

# CEA Industries (BNCB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cea-industries-bsc-4b12)

---

## Audit Summary

The SecuritiesToken contract, an upgradeable ERC-20 token, demonstrates good technical implementation using OpenZeppelin standards and the ERC8056 scaled UI token pattern. However, the design incorporates a high degree of centralization, with the DEFAULT_ADMIN_ROLE possessing extensive control over critical economic parameters and external dependencies. This centralization, combined with the wide range of the UI multiplier, introduces significant economic and governance risks. Recommendations focus on strengthening governance and access controls for administrative functions.

> **Final Recommendation:** To mitigate the identified risks, it is strongly recommended to implement robust governance mechanisms around the `DEFAULT_ADMIN_ROLE`. This should include adopting a multi-signature wallet for the admin role and, for critical operations such as setting the `_uiMultiplier` or changing external dependency addresses, incorporating time-lock mechanisms. Additionally, a clear operational policy should be established for the `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts, ensuring their security and proper functioning to prevent denial of service. Consider reviewing the acceptable range for the `_uiMultiplier` to ensure it aligns with the project's economic model and risk tolerance, potentially narrowing the bounds if extreme fluctuations are not intended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract `SecuritiesToken` demonstrates good technical practices, inheriting from OpenZeppelin's upgradeable contracts and implementing the ERC8056 standard for scaled UI amounts. It includes… |
| **Governance / Economics** | 9/10 | Low | The `SecuritiesToken` contract exhibits a high degree of centralization, with the `DEFAULT_ADMIN_ROLE` possessing extensive control over critical functions (7.3 Access Control, 7.5 Governance). The… |
| **Upgrades** | 5/10 | Medium | The contract is designed with a robust upgradeability mechanism, utilizing OpenZeppelin's `initializer` pattern and `__gap` storage to prevent storage collisions during upgrades (7.7 Upgrades). It is… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 57.4% |
| **Top-3 Unlocked** | 69.6% |

## Security Findings

_🟡 1 Medium · ⚪ 10 Informational_

### `M-03` — Extreme Multiplier Range Allows Significant Value Manipulation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_validateMultiplier` function in `ERC8056BaseUpgradeable` allows the `_uiMultiplier` to be set within an extremely wide range, from `1e9` (0.000000001x) to `1e27` (1,000,000,000x). A malicious `DEFAULT_ADMIN_ROLE` or `ISSUER_ROLE` (who can authorize multiplier updates) could set an extreme multiplier, effectively destroying or massively inflating the perceived value of token holders' balances, leading to severe economic consequences (7.4 Economic).

**Recommendation:** Review and narrow the acceptable range for the `_uiMultiplier` to align with the intended economic model and prevent extreme value fluctuations. If such a wide range is intentional, ensure robust governance and multi-sig controls are in place for any multiplier updates.


### `I-01` — Potential High Gas Cost for Initializing Issuers  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function iterates through the `issuers_` array to grant the `ISSUER_ROLE`. If the `issuers_` array contains a very large number of addresses, the transaction to initialize the contract could exceed the block gas limit on deployment. While this is a deployment-time concern and not a runtime vulnerability, it could complicate initial setup (7.2 Code Security, 7.8 Operations).

**Recommendation:** For very large lists of initial issuers, consider a phased approach or a separate function to add issuers post-initialization, allowing for multiple transactions if needed. Ensure the initial `issuers_` array size is within practical gas limits for deployment.


### `I-02` — Centralized Control and Economic Manipulation via Admin/Issuer Roles  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power, including the ability to grant/revoke `ISSUER_ROLE` (which can mint/burn tokens), enable/disable minting/burning, and set the `_uiMultiplier`. This high degree of centralization means a single compromised or malicious admin address could arbitrarily inflate or deflate the token supply, manipulate token value, or block operations, posing a significant economic and governance risk (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control and require multiple approvals for critical actions. For highly sensitive operations like setting the `_uiMultiplier` or changing compliance/pause managers, consider adding a time-lock mechanism to allow for community review or emergency intervention.


### `I-03` — External Dependency Risk for Compliance and Pause Managers  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SecuritiesToken` contract relies on external contracts for compliance (`ComplianceClientUpgradeable`) and pausing functionality (`PauseManagerClientUpgradeable`). The `_update` function, which handles all token transfers, calls `_checkTokenIsPaused()` and `_checkIsCompliant()`. If these external contracts are compromised, maliciously configured, or become inoperable, they could lead to a denial of service by indefinitely pausing transfers or enforcing arbitrary, undesirable compliance rules (7.6 External, 7.8 Operations).

**Recommendation:** Implement strict access controls and robust security measures for the `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts. Consider adding circuit breakers or emergency mechanisms in `SecuritiesToken` to bypass or disable these external checks under extreme circumstances, if feasible and aligned with the project's risk model. Ensure the addresses of these external contracts are managed securely, ideally through a multi-sig wallet and time-lock.


### `I-04` — Lack of Time Locks for Critical Administrative Operations  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While access to critical administrative functions (e.g., setting compliance/pause managers, enabling/disabling mint/burn, changing the multiplier) is restricted to the `DEFAULT_ADMIN_ROLE`, there are no time-lock mechanisms in place. This means that once an admin initiates a critical change, it takes effect immediately. In the event of a compromised admin key, this could allow an attacker to make immediate, irreversible malicious changes without any window for detection or intervention (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a time-lock mechanism for highly sensitive administrative functions. This would introduce a delay between the initiation and execution of a critical change, providing a window for monitoring, detection, and potential mitigation if an unauthorized action is identified.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.4% of supply. What remains: 64.0% in wallets, 28.4% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CEA Industries (bStocks Tokenized Stock) (BNCB), market cap $36M, rank #567. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $6.2M (DexScreener, all pools). 24h trading volume $775K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $6.2M of DEX liquidity across 8 pools. Launch: 4 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4902...ec3f`](https://bscscan.com/address/0x4902c5ebc598265ed2212b559b042de8a5eeec3f) |
| **Network** | BNB Chain |
| **Price** | $4.9800 |
| **24h Volume** | $775.5K |
| **Liquidity** | $4.67M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4d |
| **Top-10 Holders** | 92.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2356 buys / 800 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xcf936261a1582b45eae2246105b3388d1e31c94d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cea-industries-bsc-4b12)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-17*
