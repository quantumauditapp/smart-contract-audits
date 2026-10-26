---
token: Tesla, Inc. 
ticker: TSLAB
network: bsc
risk_score: 8
status: low
date: 2026-08-14
---

# Tesla, Inc.  (TSLAB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tesla-inc-bsc)

---

## Audit Summary

The SecuritiesToken contract, an upgradeable ERC-20 token, implements robust access control, compliance, and pause functionalities, leveraging OpenZeppelin standards. It features a scalable UI multiplier and controlled mint/burn mechanisms suitable for a securities token. Key strengths include secure upgradeability patterns and input validation. However, the contract exhibits a high degree of centralization, particularly with the DEFAULT_ADMIN_ROLE possessing extensive immediate control over critical token parameters, supply, and external dependencies. The Beacon Proxy pattern also centralizes upgrade authority. Several medium-severity findings highlight these centralization and dependency risks.

> **Final Recommendation:** To enhance the security and decentralization posture of the SecuritiesToken, consider implementing a timelock mechanism for all critical administrative functions currently controlled by the `DEFAULT_ADMIN_ROLE`. This would introduce a delay for sensitive operations, allowing for community oversight and mitigating the impact of a compromised administrative key. Additionally, thoroughly audit the external `ComplianceClient` and `PauseManagerClient` contracts to ensure their security and prevent potential cascading vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract demonstrates good adherence to secure coding practices, utilizing OpenZeppelin's upgradeable standards and Solidity 0.8+ for overflow protection. It includes robust input validation for… |
| **Governance / Economics** | 9/10 | Low | The `SecuritiesToken` contract features a strong access control model with `DEFAULT_ADMIN_ROLE` and `ISSUER_ROLE` for managing token operations (7.3 Access Control). Minting and burning are… |
| **Upgrades** | 5/10 | Medium | The contract is designed for upgradeability using the Beacon Proxy pattern, correctly implementing OpenZeppelin's `initializer` pattern and a `__gap` storage variable to ensure future compatibility… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 34.6% |
| **Top-3 Unlocked** | 70.4% |

## Security Findings

_🟡 2 Medium · ⚪ 10 Informational_

### `M-01` — Issuers Can Update UI Multiplier  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_authorizeMultiplierUpdate()` function, which gates the ability to change the `_uiMultiplier`, allows both the `DEFAULT_ADMIN_ROLE` and the `ISSUER_ROLE` to perform this action. While the `_validateMultiplier` function enforces bounds (1e9 to 1e27) and `_setUIMultiplier` limits the effective timestamp to 365 days in the future, granting issuers the power to change this critical parameter (7.3 Access Control, 7.4 Economic) could lead to confusion, misrepresentation of token value, or potential market manipulation if not properly governed or if issuers act maliciously.

**Recommendation:** Re-evaluate whether the `ISSUER_ROLE` should have the authority to update the UI multiplier. If this is an intended feature, ensure that the implications are clearly communicated to token holders and that robust governance procedures are in place for issuers. Consider restricting this power solely to the `DEFAULT_ADMIN_ROLE` or requiring a multi-signature approval for such changes.


### `M-02` — Reliance on External Client Contracts for Core Logic  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_update` function, which is central to all token transfers, calls `_checkTokenIsPaused()` and `_checkIsCompliant()`. These functions interact with external `PauseManagerClient` and `ComplianceClient` contracts (7.6 External, 7.2 Code Security). The security and integrity of these external contracts are paramount. A vulnerability, compromise, or malicious implementation within these client contracts could directly impact the token's transfer functionality, potentially leading to freezing of funds, unauthorized transfers, or reentrancy issues if the external contracts are not carefully designed and audited.

**Recommendation:** Conduct thorough security audits of the `PauseManagerClient` and `ComplianceClient` contracts. Ensure that these external contracts are immutable or have robust, timelocked upgrade mechanisms. Implement strict access controls on who can set these client contract addresses. Consider adding circuit breakers or emergency pause mechanisms within the `SecuritiesToken` itself that can override or disable interactions with potentially compromised external clients.


### `I-01` — `_checkAdminOrIssuer` is Private  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_checkAdminOrIssuer` function is declared as `private`. While it is correctly used by the `onlyAdminOrIssuer` modifier, making it `internal view` instead of `private view` would offer more flexibility (7.1 Architecture, 7.2 Code Security). This would allow inheriting contracts to directly call this function for internal checks without needing to duplicate the logic or rely solely on the modifier, potentially improving code reusability and extensibility for future upgrades or derived contracts.

**Recommendation:** Consider changing the visibility of `_checkAdminOrIssuer` from `private` to `internal view` to allow for greater flexibility and reusability by inheriting contracts, if such extensibility is a design goal.


### `I-02` — Centralized Control over Token Supply and Critical Parameters  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` possesses extensive and immediate control over critical token functionalities. This includes the ability to enable/disable minting and burning, set compliance and pause managers, change the token's name, symbol, and identifier, and manage all roles. The `ISSUER_ROLE` can also mint and burn tokens. This high degree of centralization (7.3 Access Control, 7.4 Economic, 7.5 Governance) means that a single compromised administrative key or malicious administrator could significantly impact the token's supply, functionality, and perceived value without any delay or external oversight.

**Recommendation:** Implement a multi-signature wallet for the `DEFAULT_ADMIN_ROLE` to distribute control among multiple trusted parties. For highly sensitive operations, consider integrating a timelock mechanism to introduce a delay before changes take effect, allowing for community review or emergency intervention. Explore options for progressive decentralization of certain administrative powers if feasible for the project's long-term vision.


### `I-03` — Beacon Proxy Centralization Risk  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is deployed behind a Beacon Proxy (7.7 Upgrades). While this pattern offers flexible upgradeability and efficient management of multiple proxies, it centralizes control over the contract's logic. The owner of the Beacon contract has the unilateral power to upgrade the implementation for all associated proxies. A compromise of the Beacon owner's key or a malicious action by the owner could lead to a complete and immediate change of the token's functionality, potentially resulting in loss of funds or unauthorized operations (7.5 Governance, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet for the Beacon owner address to distribute control. Integrate a timelock mechanism for all Beacon upgrade operations to introduce a delay, allowing for community review and mitigating the impact of a compromised key. Clearly document the upgrade process and the role of the Beacon owner.


### `I-04` — Lack of Timelock for Critical Administrative Operations  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several critical administrative functions, such as `setMintEnabled`, `setBurnEnabled`, `setCompliance`, `setPauseManager`, `setName`, `setSymbol`, `setIdentifier`, and role management functions, can be executed immediately by the `DEFAULT_ADMIN_ROLE` (7.3 Access Control, 7.8 Operations). The absence of a timelock for these operations means that a single compromised administrative key could instantly make significant, irreversible changes to the token's behavior, parameters, or external dependencies without any warning or opportunity for intervention.

**Recommendation:** Integrate a timelock mechanism for all critical administrative functions. This would introduce a mandatory delay between the initiation and execution of sensitive changes, providing a window for detection of malicious activity, community oversight, or emergency response. This significantly reduces the risk associated with a single point of failure.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.0% of supply. What remains: 86.6% in wallets, 6.4% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Tesla (bStocks Tokenized Stock) (TSLAB), market cap $26M, rank #702. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $376K (DexScreener, all pools). 24h trading volume $590K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $376K of DEX liquidity across 8 pools. Launch: 14 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 14 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 14 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5b19...292f`](https://bscscan.com/address/0x5b1910eaad6450e50f816082aa078c41f10c292f) |
| **Network** | BNB Chain |
| **Price** | $369.3800 |
| **24h Volume** | $590.2K |
| **Liquidity** | $227.2K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 14d |
| **Top-10 Holders** | 93.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1944 buys / 1903 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb0f5e5400e8f0f7c242f2b7740c004f020579c41)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tesla-inc-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
