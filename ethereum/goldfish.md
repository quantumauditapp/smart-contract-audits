---
token: Goldfish
ticker: GGBR
network: ethereum
risk_score: 12
status: low
date: 2026-09-01
---

# Goldfish (GGBR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/goldfish-eth)

---

## Audit Summary

The GoldfishToken contract, an upgradeable ERC-20, exhibits a high degree of centralization, particularly concerning the `DEFAULT_ADMIN_ROLE`. A critical finding highlights the `forceTransfer` function, which acts as a backdoor allowing the admin to move any user's tokens. The absence of multi-signature protection or time-locks for critical operations further exacerbates these risks. While the contract leverages well-audited OpenZeppelin libraries for core functionalities and implements granular access control for specific actions, the overarching administrative power presents significant security and economic concerns.

> **Final Recommendation:** It is strongly recommended to implement a robust multi-signature wallet (e.g., Gnosis Safe) for the `DEFAULT_ADMIN_ROLE` and other critical roles to mitigate the single point of failure risk. The `forceTransfer` function should be removed or protected by a multi-signature wallet with a time-lock and potentially a governance vote. Additionally, consider implementing stricter controls or governance for `maxSupply` adjustments to prevent arbitrary inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract is built upon battle-tested OpenZeppelin libraries (ERC20Burnable, Pausable, AccessControl, UUPS), providing a solid foundation for its core ERC-20 functionalities (7.2 Code Security).… |
| **Governance / Economics** | 9/10 | Low | The contract implements granular roles (PAUSER_ROLE, FREEZER_ROLE, SUPPLY_MANAGER_ROLE) which is a positive for delegated responsibilities (7.5 Governance). However, the `DEFAULT_ADMIN_ROLE` holds… |
| **Upgrades** | 5/10 | Medium | The contract correctly implements the UUPS upgrade pattern using OpenZeppelin's `UUPSUpgradeable` module (7.7 Upgrades). The `_authorizeUpgrade` function is appropriately restricted to the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 96.0% |
| **Top-3 Unlocked** | ⚠️ 98.8% |

## Security Findings

_🟡 2 Medium · 🟢 2 Low · ⚪ 6 Informational_

### `M-01` — Arbitrary `maxSupply` Increase  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `setMaxSupply` function, callable by the `SUPPLY_MANAGER_ROLE`, allows increasing the `maxSupply` to an arbitrarily high value. While it prevents reducing the supply below the current `totalSupply()`, there is no upper bound or governance mechanism to limit how much the `maxSupply` can be increased. This could lead to unexpected and significant token inflation if the `SUPPLY_MANAGER_ROLE` is compromised or acts maliciously, devaluing existing token holdings.

**Recommendation:** Implement a more constrained mechanism for `maxSupply` adjustments. Consider adding a maximum allowable increase percentage per operation, a time-lock for changes, or requiring a governance vote for significant increases. Alternatively, define a hard-coded, immutable maximum supply if the token is intended to be deflationary or have a fixed cap.


### `M-03` — Lack of Multi-signature / Time-lock for Critical Operations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). All critical administrative roles (`DEFAULT_ADMIN_ROLE`, `PAUSER_ROLE`, `FREEZER_ROLE`, `SUPPLY_MANAGER_ROLE`) are initially granted to the deployer (`msg.sender`) and can be managed by the `DEFAULT_ADMIN_ROLE`. There are no multi-signature wallet requirements or time-locks implemented for sensitive operations such as contract upgrades, setting the minter, blacklisting, freezing, or using `forceTransfer`. This creates a single point of failure, making the protocol highly vulnerable to compromise of a single private key or malicious insider actions.

**Recommendation:** Implement a robust access control mechanism for critical roles, preferably using a multi-signature wallet (e.g., Gnosis Safe) for `DEFAULT_ADMIN_ROLE` and other sensitive roles. Consider adding time-locks for highly impactful operations like contract upgrades or `forceTransfer` to provide a window for users to react to potentially malicious actions.


### `L-01` — Disabled `burnFrom` Functionality  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `burnFrom` function, a standard part of the ERC20Burnable extension, has been explicitly disabled by reverting all calls. This design choice removes a common functionality that allows approved third parties (e.g., DeFi protocols) to burn tokens on behalf of a user. While a design decision, it limits the composability and utility of the token within the broader DeFi ecosystem.

**Recommendation:** Review the necessity of disabling `burnFrom`. If the intention is to prevent specific types of interactions, consider if alternative mechanisms or more granular controls could achieve the same security goals without completely removing standard functionality. If the decision is final, ensure clear documentation for users and integrators.


### `L-02` — `batchTransfer` Self-Transfer Restriction  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `batchTransfer` function explicitly disallows self-transfers within the batch by including the check `require(_recipients[i] != msg.sender, "Self-transfer not allowed");`. While not a security vulnerability, this is an unusual restriction for a batch transfer function. Users might expect to be able to include their own address in a batch for various reasons (e.g., consolidating funds, rebalancing).

**Recommendation:** Re-evaluate the necessity of preventing self-transfers in `batchTransfer`. If there's no specific security rationale, removing this restriction would improve user experience and align with common token transfer patterns. If it's a deliberate design choice, ensure it's clearly documented.


### `I-01` — Extreme Centralization and Backdoor Functionality (`forceTransfer`)  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` possesses extensive control, including the ability to upgrade the contract, blacklist accounts, set the minter, and crucially, execute `forceTransfer`. The `forceTransfer` function allows the admin to transfer any amount of tokens from any address to any other address without the token holder's consent. This represents a severe centralization risk and a direct backdoor, enabling arbitrary seizure or redistribution of user funds.

**Recommendation:** Remove or significantly restrict the `forceTransfer` function. If such a function is deemed absolutely necessary for emergency scenarios, it should be protected by a multi-signature wallet with a time-lock, require a governance vote, or be limited to specific, predefined emergency conditions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.5% of supply. What remains: 89.2% in wallets, 8.3% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Goldfish Gold (GGBR), market cap $82M, rank #313. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $181K (DexScreener, all pools). 24h trading volume $2K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Gold. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $181K of DEX liquidity across 1 pools. Launch: 324 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7e2a...b71a`](https://etherscan.io/address/0x7e2ac793f3e692f388e66c7dc28f739d13b0b71a) |
| **Network** | Ethereum |
| **Price** | $4.1700 |
| **24h Volume** | $1.5K |
| **Liquidity** | $181.2K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 97.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 123 buys / 195 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x75a5a265d21bc89ec130f18edde2b49a4b200dac)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/goldfish-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
