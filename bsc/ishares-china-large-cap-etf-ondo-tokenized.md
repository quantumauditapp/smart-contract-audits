---
token: iShares China Large-Cap ETF (Ondo Tokenized)
ticker: FXION
network: bsc
risk_score: 9
status: low
date: 2026-09-25
---

# iShares China Large-Cap ETF (Ondo Tokenized) (FXION) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ishares-china-large-cap-etf-ondo-tokenized-bsc)

---

## Audit Summary

The GMToken contract serves as an upgradeable ERC-20 token implementation, utilizing OpenZeppelin's Beacon Proxy pattern and AccessControl for role-based permissions. It integrates external compliance and token pausing functionalities. While the core code is well-structured and leverages battle-tested libraries, significant centralization risks exist due to powerful administrative roles that control token supply and critical external dependencies. The compliance check logic also presents a potential for unintended transaction blocking.

> **Final Recommendation:** It is strongly recommended to implement robust governance mechanisms for all privileged roles, especially the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, `BURNER_ROLE`, and `CONFIGURER_ROLE`. These roles should ideally be controlled by a multi-signature wallet with a high threshold or a decentralized autonomous organization (DAO) to mitigate centralization risks. Additionally, thoroughly review the implications of the `_beforeTokenTransfer` compliance check on `msg.sender` to ensure it does not inadvertently hinder legitimate interactions with other DeFi protocols, and consider providing clear documentation or whitelisting guidelines for integrated services.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The GMToken contract demonstrates good technical architecture (7.1) by inheriting from OpenZeppelin's upgradeable ERC-20 and AccessControl contracts, ensuring a robust foundation. Code security (7.2)… |
| **Governance / Economics** | 9/10 | Low | The contract's economic (7.4) and governance (7.5) models present high centralization risks. The `MINTER_ROLE` and `BURNER_ROLE` have complete control over token supply, allowing for arbitrary… |
| **Upgrades** | 5/10 | Medium | The contract is designed as an upgradeable implementation using OpenZeppelin's `Initializable` pattern and is deployed via a Beacon Proxy (7.7). This architecture allows for future logic upgrades… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 28.5% |
| **Top-3 Unlocked** | 61.2% |

## Security Findings

_🟡 1 Medium · ⚪ 10 Informational_

### `M-01` — Potential Transfer Blocking via `msg.sender` Compliance Check  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_beforeTokenTransfer` hook includes a conditional compliance check for `msg.sender` (`if (from != msg.sender && to != msg.sender) { _checkIsCompliant(msg.sender); }`). This means that for `transferFrom` operations or transfers initiated by an approved contract, the *caller* of the transaction must also be compliant. This could inadvertently block legitimate transfers if the interacting protocol (e.g., a DEX router, a lending pool) is not whitelisted by the `OndoComplianceGMClientUpgradeable` contract, even if the `from` and `to` addresses are compliant.

**Recommendation:** Clarify the intended behavior and implications of this `msg.sender` compliance check. If the intent is to allow protocol interactions, ensure that common DeFi protocols or their proxy addresses are whitelisted in the compliance contract. Alternatively, reconsider the necessity of this specific `msg.sender` check for `transferFrom` scenarios if it creates undue friction for legitimate integrations.


### `I-01` — High Dependency on External Contracts  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `GMToken` contract heavily relies on the `OndoComplianceGMClientUpgradeable` and `TokenPauseManagerClientUpgradeable` contracts for core functionalities like compliance checks and token pausing. The security, correctness, and availability of these external contracts are paramount to the overall integrity and intended behavior of the `GMToken` itself.

**Recommendation:** Ensure that the external `OndoComplianceGMClientUpgradeable` and `TokenPauseManagerClientUpgradeable` contracts have undergone thorough security audits and are maintained by trusted entities. Implement robust monitoring for these external dependencies to detect any unexpected behavior or compromise.


### `I-02` — Centralized Control Over Critical External Dependencies  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `CONFIGURER_ROLE` has the ability to change the addresses of the `_compliance` and `_tokenPauseManager` contracts via `setCompliance` and `setTokenPauseManager` functions. This allows a single entity holding this role to redirect critical compliance and token pausing functionalities to potentially malicious or non-functional contracts, effectively disabling or compromising these core security features.

**Recommendation:** Implement a robust governance mechanism, such as a multi-signature wallet or a time-locked contract, for the `CONFIGURER_ROLE`. Any changes to critical external dependencies should require multiple approvals or a delay period to provide transparency and allow for community oversight.


### `I-03` — Centralized Control Over Token Supply  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `MINTER_ROLE` can mint an arbitrary amount of tokens to any address, and the `BURNER_ROLE` can burn tokens from any address. While common for managed tokens, this grants significant power to the entities holding these roles, posing a high economic risk if these roles are compromised or misused. Malicious minting could devalue the token, and arbitrary burning could seize user funds.

**Recommendation:** Ensure that the `MINTER_ROLE` and `BURNER_ROLE` are controlled by highly secure, multi-signature wallets or a decentralized governance process. Implement strict operational procedures and monitoring for any minting or burning activities. Consider adding limits or additional checks for large mint/burn operations if feasible within the protocol's design.


### `I-04` — Critical Role Management for DEFAULT_ADMIN_ROLE  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` is granted to `msg.sender` during the `__gmToken_init_unchained` initialization. This role has the highest level of privilege, including the ability to grant and revoke all other roles. While standard for initial deployment, improper management of this role post-deployment represents a single point of failure.

**Recommendation:** Immediately after deployment and initialization, the `DEFAULT_ADMIN_ROLE` should be transferred from the deployer's address to a secure, multi-signature wallet or a robust governance contract. This minimizes the risk associated with a single private key controlling all administrative functions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.3% of supply. What remains: 0.6% in wallets, 54.8% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as iShares China Large-Cap ETF (Ondo Tokenized) (FXION), market cap $3M, rank #2101. Its admin (0x8860…3b26) controls 440 issuer-backed coins CoinGecko lists on bsc, $1.0B together, among them Circle Internet Group (Ondo Tokenized Stock), Ondo U.S. Dollar Token, iShares Core S&P 500 ETF (Ondo Tokenized ETF): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.7M (DexScreener, all pools). 24h trading volume $14.1M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Exchange-Traded Funds (ETFs). Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.7M of DEX liquidity across 6 pools. Launch: 17 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9b8e...eea1`](https://bscscan.com/address/0x9b8e987e6fec8cf1380c4dca7071e2c7853aeea1) |
| **Network** | BNB Chain |
| **Price** | $34.0830 |
| **24h Volume** | $14.11M |
| **Liquidity** | $1.54M |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 17d |
| **Top-10 Holders** | 55.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 59147 buys / 60210 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x8768c8969e177575e37435b8295afa2dfb231c86)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ishares-china-large-cap-etf-ondo-tokenized-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-25*
