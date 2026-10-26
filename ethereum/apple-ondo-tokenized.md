---
token: Apple (Ondo Tokenized)
ticker: AAPLON
network: ethereum
risk_score: 9
status: low
date: 2026-09-13
---

# Apple (Ondo Tokenized) (AAPLON) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/apple-ondo-tokenized-eth)

---

## Audit Summary

The GMToken contract implements an upgradeable ERC-20 token with extensive access control for minting, burning, pausing, and compliance. It leverages OpenZeppelin's upgradeable contracts and a Beacon Proxy pattern. While the architecture provides granular control, the high degree of centralization, particularly the power of the DEFAULT_ADMIN_ROLE and the unrestricted BURNER_ROLE, introduces significant security and economic risks. Proper management of these roles is critical to the security of the token.

> **Final Recommendation:** It is crucial to implement robust operational security measures for all privileged roles, especially the `DEFAULT_ADMIN_ROLE`, ideally transferring it to a multi-signature wallet or a well-governed DAO. Re-evaluate the scope of the `BURNER_ROLE` to restrict burning to approved amounts or the burner's own balance, or implement a more secure mechanism for burning from arbitrary addresses. Carefully manage the `CONFIGURER_ROLE` due to its ability to alter critical external dependencies.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract utilizes well-audited OpenZeppelin upgradeable components, ensuring a solid foundation for ERC-20 functionality and access control (7.2 Code Security). The `_beforeTokenTransfer` hook… |
| **Governance / Economics** | 9/10 | Low | The token's economic model is highly centralized, with the `DEFAULT_ADMIN_ROLE` possessing ultimate control over all critical functions, including minting, burning, pausing, and compliance settings… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements the upgradeable pattern using `_disableInitializers()` in the constructor and `initializer` modifiers for setup, ensuring proper initialization for a Beacon Proxy… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.4% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 8 Informational_

### `M-01` — Initialization Order in `__gmToken_init`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `__gmToken_init_unchained` function, which sets the `DEFAULT_ADMIN_ROLE` and overrides name/symbol, is called after the initialization of `OndoComplianceGMClientInitializable_init` and `TokenPauseManagerClientInitializable_init_unchained`. While not a direct vulnerability in this context, it is generally safer practice to initialize all base contracts first before the derived contract's specific logic to ensure all dependencies are fully set up before custom logic executes (7.1 Architecture, 7.7 Upgrades).

**Recommendation:** Consider reordering the initialization calls within `__gmToken_init` to ensure `__gmToken_init_unchained` is called before the external client initializers, or at least ensure that no critical state relies on `DEFAULT_ADMIN_ROLE` or name/symbol being set before the external clients are initialized.


### `M-03` — Unrestricted Burner Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `BURNER_ROLE` allows an authorized address to burn tokens from *any* holder's balance (`_burn(from, amount)`). This means a malicious or compromised burner could arbitrarily destroy tokens held by users, leading to direct loss of user funds without their consent or prior approval (7.3 Access Control, 7.4 Economic).

**Recommendation:** Restrict the `burn` function to only allow burning from `msg.sender` (the burner's own balance) or implement a `burnFrom` function that requires prior `approve` calls, similar to `transferFrom`. If burning from arbitrary addresses is a requirement, ensure robust off-chain controls and oversight for the `BURNER_ROLE`.


### `M-04` — Configurer Role Can Change Critical Dependencies  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `CONFIGURER_ROLE` can update the addresses of the `OndoComplianceGMClientUpgradeable` and `TokenPauseManagerClientUpgradeable` contracts via `setCompliance` and `setTokenPauseManager`. If a malicious or compromised address is set for these dependencies, it could lead to arbitrary pausing of transfers or manipulation of compliance checks, effectively halting or controlling token movement (7.3 Access Control, 7.6 External).

**Recommendation:** Implement a timelock for changes to critical external dependencies to allow for community review or emergency intervention. Ensure that the `CONFIGURER_ROLE` is managed with the highest security standards, potentially by a multi-signature wallet.


### `I-01` — Missing Custom Events for Role Management  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While `AccessControlUpgradeable` emits `RoleGranted` and `RoleRevoked` events, the `GMToken` contract itself does not emit custom events when specific roles like `MINTER_ROLE`, `BURNER_ROLE`, or `CONFIGURER_ROLE` are granted or revoked. This can make off-chain monitoring and auditing of critical permission changes more challenging for specific roles (7.2 Code Security, 7.8 Operations).

**Recommendation:** Consider adding custom events in `_grantRole` and `_revokeRole` overrides (or in `grantRole`/`revokeRole` if not overriding internal functions) to specifically log when `MINTER_ROLE`, `BURNER_ROLE`, or `CONFIGURER_ROLE` are assigned or removed. This enhances transparency and ease of monitoring.


### `I-02` — Centralized Control and High Privileges  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` holds extensive power, including the ability to grant/revoke all other roles (MINTER, BURNER, CONFIGURER). This centralizes control over token supply (mint/burn), token transfer restrictions (pause/compliance), and core token metadata. A compromise of this role would lead to catastrophic loss of funds or manipulation of the token ecosystem (7.3 Access Control, 7.4 Economic, 7.5 Governance).

**Recommendation:** Transfer the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet or a decentralized autonomous organization (DAO) to distribute control and reduce the risk of a single point of failure. Implement strict operational procedures for managing this role.


### `I-03` — Lack of Specific Renouncement Mechanism for DEFAULT_ADMIN_ROLE  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While `renounceRole` exists for general roles, there is no specific mechanism or recommendation for the `DEFAULT_ADMIN_ROLE` to renounce its powers to a multi-signature wallet or governance contract after initial setup. This keeps a single point of failure for the most powerful role if not explicitly managed off-chain (7.3 Access Control, 7.8 Operations).

**Recommendation:** Provide clear documentation and a recommended procedure for the `DEFAULT_ADMIN_ROLE` to be transferred to a more secure, multi-signature controlled address or a governance contract post-deployment, if this is the intended long-term state.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 93.8% of supply. What remains: 7.6% in wallets, 86.1% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Apple (Ondo Tokenized Stock) (AAPLON), market cap $10M, rank #1225. Its admin (0x3715…34f1) controls 441 issuer-backed coins CoinGecko lists on ethereum, $1.0B together, among them Circle Internet Group (Ondo Tokenized Stock), Ondo U.S. Dollar Token, iShares Core S&P 500 ETF (Ondo Tokenized ETF): one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $63K (DexScreener, all pools). 24h trading volume $38K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $63K of DEX liquidity across 6 pools. Launch: 357 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x14c3...2d4c`](https://etherscan.io/address/0x14c3abf95cb9c93a8b82c1cdcb76d72cb87b2d4c) |
| **Network** | Ethereum |
| **Price** | $333.7200 |
| **24h Volume** | $38.1K |
| **Liquidity** | $34.4K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 93.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 221 buys / 156 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xad82c9eb065a5cfed71db087e4a52c8a09c69921)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/apple-ondo-tokenized-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
