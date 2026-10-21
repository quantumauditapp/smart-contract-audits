---
token: CoinMarketCap 20 Index DTF
ticker: CMC20
network: bsc
risk_score: 71
status: high
date: 2026-09-02
---

# CoinMarketCap 20 Index DTF (CMC20) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 71/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinmarketcap-20-index-dtf-bsc)

---

## Audit Summary

The Folio contract serves as an upgradeable ERC20 token managing a basket of assets, incorporating features like fees, rebalancing, and trusted fillers. The contract leverages OpenZeppelin's upgradeable standards, reentrancy guards, and access control. Key strengths include the use of a Timelock for administrative actions and a robust fee distribution mechanism. However, the system exhibits a high degree of centralized control by the admin role, and relies on complex, unaudited external components for core economic functions like rebalancing and auctions. The presence of deprecated code also adds to complexity.

> **Final Recommendation:** Prioritize a comprehensive audit of all external contracts and libraries, especially those governing rebalancing, auctions, and trusted fillers, as these are critical to the protocol's economic integrity. Evaluate the necessity of the highly centralized `DEFAULT_ADMIN_ROLE` and explore options for further decentralization or multi-signature protection for the Timelock's owner. Implement a strict whitelist for basket assets to mitigate risks from malicious or non-standard ERC20 tokens. Finally, consider refactoring to remove deprecated code to enhance clarity and reduce the attack surface.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Folio contract demonstrates good technical practices, utilizing OpenZeppelin's upgradeable contracts, `ReentrancyGuardUpgradeable`, and `SafeERC20` for secure token interactions (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The governance and economic model features a `DEFAULT_ADMIN_ROLE` with extensive control over critical parameters, including fees, basket assets, and rebalancing settings (7.3 Access Control, 7.5… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using OpenZeppelin's `Initializable` and `Upgradeable` patterns, including `__ERC20_init`, `__AccessControlEnumerable_init`, and `__ReentrancyGuard_init`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.4% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control by DEFAULT_ADMIN_ROLE  *(Severity: High · Status: Unresolved)*

The `DEFAULT_ADMIN_ROLE` possesses extensive control over critical contract parameters, including setting fees (`setTVLFee`, `setMintFee`, `setFeeRecipients`), managing basket assets (`addToBasket`, `removeFromBasket`), configuring rebalancing (`setRebalanceControl`), enabling/disabling trusted fillers (`setTrustedFillerRegistry`), and deprecating the entire Folio (`deprecateFolio`). While this role is assigned to a Timelock contract with a 2-day delay, this concentration of power means that a compromise of the Timelock's owner could lead to significant financial loss or protocol manipulation. (7.3 Access Control, 7.5 Governance, 7.4 Economic)

**Recommendation:** Consider implementing a multi-signature wallet for the Timelock's owner or further decentralizing control over highly sensitive parameters where feasible, perhaps through community governance or additional timelocks for specific actions.


### `M-01` — Unaudited External Rebalancing and Auction Logic  *(Severity: Medium · Status: Unresolved)*

The `Folio` contract integrates complex rebalancing and auction mechanisms through external libraries (`RebalancingLib`) and interfaces (`ITrustedFillerRegistry`, `IBaseTrustedFiller`). The provided code snippet does not include the full implementation of these external components. Without a comprehensive audit of these external contracts and libraries, their security, potential for manipulation, front-running, or economic exploits cannot be fully assessed. (7.6 External, 7.4 Economic, 7.1 Architecture)

**Recommendation:** Conduct a thorough security audit of all external contracts and libraries, specifically `RebalancingLib`, `ITrustedFillerRegistry`, and `IBaseTrustedFiller`, to ensure their robustness and prevent vulnerabilities that could impact the `Folio` contract.


### `M-02` — Dependency on External IFolioDAOFeeRegistry  *(Severity: Medium · Status: Unresolved)*

The calculation of DAO fees in the `mint` function (and potentially other fee-related operations) relies on the `getFeeDetails` function of an external `IFolioDAOFeeRegistry` contract. The security and integrity of this external registry are paramount. If the `daoFeeRegistry` were compromised or misconfigured, it could lead to incorrect fee calculations, unexpected fee distributions, or denial of service for fee-related operations within the `Folio` contract. (7.6 External, 7.4 Economic)

**Recommendation:** Ensure the `IFolioDAOFeeRegistry` contract is highly secure, immutable, or managed by a robust governance process. Implement robust input validation and consider circuit breakers or fallback mechanisms in case of unexpected behavior from the external registry.


### `L-01` — Risk from Malicious or Non-Standard ERC20 Tokens  *(Severity: Low · Status: Unresolved)*

The `addToBasket` function allows the `DEFAULT_ADMIN_ROLE` to add any ERC20 token. While `SafeERC20` is used for token interactions, malicious or non-standard ERC20 tokens (e.g., those with re-entrant `transferFrom` hooks, fee-on-transfer mechanisms, or tokens that can be paused/blacklisted) could still introduce unexpected behavior, lead to loss of funds, or disrupt the contract's operations (e.g., rebalancing, minting, redeeming). (7.6 External, 7.4 Economic)

**Recommendation:** Implement a strict whitelist for approved ERC20 tokens that have been thoroughly vetted for standard behavior. Consider adding additional checks or safeguards when interacting with newly added tokens.


### `I-01` — Presence of Deprecated Code and Variables  *(Severity: Informational · Status: Unresolved)*

The contract contains several variables and structs explicitly marked with `_DEPRECATED` (e.g., `auctions_DEPRECATED`, `sellEnds_DEPRECATED`, `DeprecatedStruct`). While these are likely inactive or remnants of previous versions, their presence adds to the code's complexity, increases the cognitive load for auditors and developers, and could potentially lead to confusion or unintended interactions if not completely isolated or removed. (7.1 Architecture, 7.2 Code Security)

**Recommendation:** Consider removing all deprecated code and variables to improve code clarity, reduce the attack surface, and simplify future maintenance and audits. If removal is not feasible, ensure they are clearly documented as unreachable and have no impact on current logic.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2f8a...6867`](https://bscscan.com/address/0x2f8a339b5889ffac4c5a956787cda593b3c36867) |
| **Network** | BNB Chain |
| **Price** | $166.0420 |
| **24h Volume** | $792.0K |
| **Liquidity** | $1.69M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 86.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 855 buys / 964 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xb4bd7ec1df39806df478d0ce540580a118671eea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinmarketcap-20-index-dtf-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
