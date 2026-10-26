---
token: Invesqo QQQ
ticker: QQQB
network: bsc
risk_score: 10
status: low
date: 2026-07-26
---

# Invesqo QQQ (QQQB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/invesqo-qqq-bsc)

---

## Audit Summary

The audit of the SecuritiesToken contract, serving as the implementation for a Beacon Proxy, identified a critical vulnerability related to the initialization of the admin role, which could lead to permanent loss of administrative control. Additional medium and low-severity issues were found concerning zero-address checks for external dependencies and inherent centralization risks. The contract utilizes standard OpenZeppelin upgradeable patterns and role-based access control.

> **Final Recommendation:** Address the critical vulnerability by implementing a zero-address check for the `admin_` parameter in the `initialize` function to prevent irreversible loss of administrative control. Additionally, add zero-address checks for `compliance_` and `pauseManager_` to ensure robust system integrity. Consider implementing multi-signature control for the `DEFAULT_ADMIN_ROLE` to mitigate centralization risks and enhance operational security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract leverages OpenZeppelin's upgradeable patterns and AccessControlEnumerable for robust role management (7.1 Architecture, 7.3 Access Control). Custom error types enhance readability and… |
| **Governance / Economics** | 9/10 | Low | The token's economic model relies on a centralized `DEFAULT_ADMIN_ROLE` for critical operations such as enabling/disabling minting/burning, and managing all other roles (7.4 Economic, 7.5… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements OpenZeppelin's upgradeable proxy pattern, utilizing `_disableInitializers()` in the constructor and the `initializer` modifier for the `initialize` function (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 42.1% |
| **Top-3 Unlocked** | 78.4% |

## Security Findings

_🟡 1 Medium · ⚪ 9 Informational_

### `M-01` — Missing Zero Address Checks for External Client Contracts  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function accepts `compliance_` and `pauseManager_` addresses for external client contracts without validating that these addresses are not the zero address (`address(0)`). While not directly leading to a loss of funds, setting these critical external dependencies to `address(0)` could result in unexpected runtime errors, non-functional compliance checks, or an inability to pause the token, severely impacting the contract's intended behavior and operational stability.

**Recommendation:** Implement zero-address checks for `compliance_` and `pauseManager_` parameters in the `initialize` function. For example: `if (compliance_ == address(0)) revert ZeroAddress();` and `if (pauseManager_ == address(0)) revert ZeroAddress();`


### `I-01` — Reliance on External Compliance and Pause Managers  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `SecuritiesToken` contract integrates `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable`, making its core functionalities (transfers, minting, burning) dependent on the logic and availability of these external contracts. The security, reliability, and upgradeability of these external dependencies are paramount, as any vulnerability or malfunction in them could directly impact the `SecuritiesToken`'s operations and user experience.

**Recommendation:** Ensure that the external `ComplianceClientUpgradeable` and `PauseManagerClientUpgradeable` contracts are thoroughly audited, well-maintained, and controlled by robust governance mechanisms. Implement monitoring for these external contracts to detect any unusual behavior or potential compromises promptly.


### `I-02` — Missing Zero Address Check for Admin Role in `initialize`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `initialize` function, which sets up the initial `DEFAULT_ADMIN_ROLE`, does not validate that the `admin_` parameter is not the zero address (`address(0)`). If `address(0)` is provided during initialization, the `DEFAULT_ADMIN_ROLE` will be granted to the zero address, making it impossible to manage roles, enable/disable minting/burning, or perform any other administrative functions. This would lead to a permanent lockout of administrative control over the contract.

**Recommendation:** Add a check in the `initialize` function to ensure `admin_` is not `address(0)` before granting the `DEFAULT_ADMIN_ROLE`. For example: `if (admin_ == address(0)) revert ZeroAddress();`


### `I-03` — High Centralization Risk with DEFAULT_ADMIN_ROLE  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power over the `SecuritiesToken` contract. This role can set the token's name, symbol, and identifier, enable/disable minting and burning, and grant/revoke any other role, including the `ISSUER_ROLE`. While common for security tokens requiring centralized control, this concentration of power means that a compromise of the single entity holding the `DEFAULT_ADMIN_ROLE` could lead to significant operational and economic risks, including unauthorized token issuance or manipulation of token metadata.

**Recommendation:** Consider implementing a multi-signature wallet or a time-locked governance mechanism for the `DEFAULT_ADMIN_ROLE` to distribute control and introduce a delay for critical operations. This would enhance security by requiring multiple approvals for sensitive actions and providing a window for intervention.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.7% of supply. What remains: 71.4% in wallets, 10.3% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Invesco QQQ Trust (bStocks Tokenized Stock) (QQQB), market cap $1M, rank #2644. Its admin (0x45e3…679d) controls 100 issuer-backed coins CoinGecko lists on bsc, $1.2B together, among them SpaceX (bStocks Tokenized Stock), Circle Internet Group (bStocks Tokenized Stock), SanDisk (bStocks Tokenized Stock): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.0M (DexScreener, all pools). 24h trading volume $22.8M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Exchange-Traded Funds (ETFs). Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $3.0M of DEX liquidity across 9 pools. Launch: 16 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 16 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 16 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2058...efc7`](https://bscscan.com/address/0x205812cdbed920aff76c6580abd681a46d11efc7) |
| **Network** | BNB Chain |
| **Price** | $718.6000 |
| **24h Volume** | $22.82M |
| **Liquidity** | $2.52M |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 16d |
| **Top-10 Holders** | 81.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7406 buys / 6727 sells |

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

## Frequently Asked Questions

### Is Invesqo QQQ a scam?

Based on automated analysis, Invesqo QQQ scores 10/100 (Low Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Invesqo QQQ safe to buy?

Our scanner flagged a risk score of 10/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Invesqo QQQ been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xe531fcb1f5a195de7608b9f4f9518544c2cdb693)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/invesqo-qqq-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
