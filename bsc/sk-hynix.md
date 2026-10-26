---
token: SK Hynix
ticker: SKHYB
network: bsc
risk_score: 9
status: low
date: 2026-08-14
---

# SK Hynix (SKHYB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sk-hynix-bsc)

---

## Audit Summary

The SecuritiesToken contract, an upgradeable ERC-20 implementation, demonstrates a robust architecture leveraging OpenZeppelin's upgradeable patterns and custom compliance/pause functionalities. While the contract exhibits good code quality and adherence to upgradeability best practices, a critical vulnerability exists in the initialization logic that could lead to a permanent loss of administrative control. Additionally, the highly centralized control by the DEFAULT_ADMIN_ROLE presents a significant single point of failure and economic risk. Recommendations focus on hardening initialization, enhancing access control, and improving transparency.

> **Final Recommendation:** Prioritize addressing the critical initialization vulnerability by adding a `require` check for `admin_ != address(0)`. Implement robust multi-signature or time-locked mechanisms for the `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control over critical functions and the `_uiMultiplier`. Enhance transparency by emitting events for all significant state changes, including role revocations, to facilitate off-chain monitoring and auditing.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates strong technical foundations, leveraging OpenZeppelin's upgradeable patterns and robust error handling with custom revert messages (e.g., `EmptyString()`, `ZeroAddress()`).… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model is based on a controlled 'securities token' with explicit roles for `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE`, which is appropriate for its stated purpose. The… |
| **Upgrades** | 5/10 | Medium | The contract is designed for upgradeability using OpenZeppelin's `initializer` pattern and `__gap` storage, deployed behind a BeaconProxy, which is a standard and secure upgrade mechanism (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 74.5% |
| **Top-3 Unlocked** | ⚠️ 88.9% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `M-01` — Powerful `_uiMultiplier` Mechanism  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_uiMultiplier` mechanism, controlled by `DEFAULT_ADMIN_ROLE` or `ISSUER_ROLE` via `_authorizeMultiplierUpdate`, allows for changing the effective value of tokens. While the `_validateMultiplier` function enforces bounds (1e9 to 1e27) and `_setUIMultiplier` limits the future effective timestamp to 365 days, this power can still significantly impact token holders. Misuse or compromise of the controlling role could lead to unexpected economic consequences for token value (7.4 Economic, 7.5 Governance).

**Recommendation:** Ensure that the process for updating the `_uiMultiplier` is subject to strict governance procedures, potentially involving a multi-signature wallet or a time-lock. Clearly communicate the implications of multiplier changes to token holders and provide transparent access to historical and pending multiplier updates.


### `L-01` — Lack of Event for Role Revocation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While `_grantRole` emits a `RoleGranted` event, there is no explicit event emitted when a role is revoked using `_revokeRole` or `_renounceRole` (inherited from `AccessControlEnumerableUpgradeable`). This can make it challenging for off-chain systems and auditors to track and verify changes in access control permissions, reducing transparency and auditability (7.2 Code Security, 7.8 Operations).

**Recommendation:** Consider overriding the `_revokeRole` and `_renounceRole` functions to emit a custom event, such as `RoleRevoked(bytes32 role, address account, address sender)`, to provide a complete audit trail of access control changes.


### `I-01` — Reliance on External Compliance and Pause Manager Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SecuritiesToken` contract integrates with external `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts. These external contracts are critical for enforcing compliance rules and managing the token's paused state. The security and integrity of the `SecuritiesToken` are directly dependent on the correct functioning and security of these external dependencies (7.6 External, 7.1 Architecture).

**Recommendation:** Ensure that the external `ComplianceClient` and `PauseManagerClient` contracts are thoroughly audited, well-maintained, and deployed with robust security practices. Implement monitoring for these external contracts to detect any unexpected behavior or compromises.


### `I-02` — Potential Loss of Admin Role During Initialization  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function, which sets up the contract's initial state and grants the `DEFAULT_ADMIN_ROLE`, does not validate the `admin_` address parameter. If `address(0)` is passed as `admin_` during the initial deployment and initialization, the `DEFAULT_ADMIN_ROLE` will be granted to the zero address. This would result in a permanent loss of administrative control over the contract, making it unmanageable and potentially un-upgradeable (7.3 Access Control, 7.7 Upgrades, 7.8 Operations).

**Recommendation:** Add a `require` statement at the beginning of the `initialize` function to ensure that `admin_` is not `address(0)`. For example: `require(admin_ != address(0), "SecuritiesToken: Admin cannot be zero address");`


### `I-03` — Centralized Control and Single Point of Failure  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` possesses extensive control over critical contract functionalities. This includes the ability to enable/disable minting and burning, change token metadata (name, symbol, identifier), and update the addresses of external `ComplianceClient` and `PauseManagerClient` contracts. This high degree of centralization creates a single point of failure, where a compromise of the admin key could lead to severe consequences, including unauthorized token issuance, manipulation of token properties, or redirection of control to malicious external contracts (7.3 Access Control, 7.4 Economic, 7.8 Operations).

**Recommendation:** Consider implementing a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to require multiple approvals for critical operations. For highly sensitive actions, a time-lock mechanism could be introduced to allow for community review or emergency intervention before changes take effect.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.6% of supply. What remains: 94.4% in wallets, 3.2% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SK Hynix (bStocks Tokenized Stock) (SKHYB), market cap $28M, rank #673. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $784K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 15 pools. Launch: 31 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xca75...db61`](https://bscscan.com/address/0xca750ef65f295bbecd685abf54e82caf297bdb61) |
| **Network** | BNB Chain |
| **Price** | $164.6600 |
| **24h Volume** | $784.4K |
| **Liquidity** | $1.04M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 97.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4058 buys / 3877 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xd7d30f434b12f7ed9b0ae11ff1c754745a10ad52)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sk-hynix-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
