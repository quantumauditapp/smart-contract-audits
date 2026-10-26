---
token: CF Large Cap Index
ticker: LCAP
network: base
risk_score: 68
status: high
date: 2026-10-19
---

# CF Large Cap Index (LCAP) — Smart Contract Security Analysis | Base

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cf-large-cap-index-base)

---

## Audit Summary

The audit of the Folio contract (implementation for FolioProxy) revealed a well-structured system utilizing OpenZeppelin's upgradeable contracts and access control. Key strengths include reentrancy protection and modular design. However, the audit identified a high centralization risk due to extensive `DEFAULT_ADMIN_ROLE` privileges, a critical upgrade safety concern with direct storage manipulation via assembly, and operational complexities in fee recipient management.

> **Final Recommendation:** It is strongly recommended to implement a Timelock for the `DEFAULT_ADMIN_ROLE` to introduce a delay for critical administrative actions, enhancing security and governance transparency. The use of assembly for direct storage slot manipulation in `_setName` should be refactored to use standard OpenZeppelin upgradeable storage patterns to prevent potential storage collisions during future upgrades. Additionally, consider refining the `_setFeeRecipients` function to reduce operational complexity and potential griefing vectors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Folio contract demonstrates strong technical foundations, leveraging OpenZeppelin's `ERC20Upgradeable`, `AccessControlEnumerableUpgradeable`, and `ReentrancyGuardUpgradeable` for robust security… |
| **Governance / Economics** | 1/10 | High | The contract implements a comprehensive role-based access control system, including `DEFAULT_ADMIN_ROLE`, `REBALANCE_MANAGER`, and `AUCTION_LAUNCHER`, which is a strength for managing protocol… |
| **Upgrades** | 1/10 | High | The Folio contract is designed as an upgradeable proxy, utilizing OpenZeppelin's `Initializable` pattern and `AccessControlEnumerableUpgradeable`, which provides a clear path for future enhancements… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 5 Medium · 🟢 2 Low · ⚪ 5 Informational_

### `M-01` — `_setName` Uses Assembly for Direct Storage Slot Manipulation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_setName` function directly manipulates a storage slot using inline assembly (`assembly { $.slot := ERC20_STORAGE_LOCATION } $._name = _newName;`) to update the ERC-20 token's name. While `ERC20_STORAGE_LOCATION` is a constant, relying on fixed storage slots in an upgradeable contract is a fragile pattern. If the `ERC20Upgradeable` contract's storage layout changes in a future OpenZeppelin upgrade, or if `ERC20_STORAGE_LOCATION` is miscalculated or misconfigured, it could lead to storage collisions, corrupting the contract's state and potentially leading to critical vulnerabilities (7.7 Upgrades, 7.2 Code Security

**Recommendation:** Refactor the `_setName` function to avoid direct assembly-based storage manipulation. Instead, consider using a standard upgradeable pattern for modifying ERC-20 metadata, or ensure that `ERC20_STORAGE_LOCATION` is robustly verified against all potential OpenZeppelin upgrades and contract inheritance structures. If `_name` is intended to be immutable after initialization, remove the setter entirely.


### `M-02` — Operational Burden and Potential Griefing in Fee Recipient Management  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_setFeeRecipients` function requires fee recipients to be provided in strictly ascending order by address (`require(_feeRecipients[i].recipient > previousRecipient)`). While this helps prevent duplicate entries and ensures deterministic storage, it creates an operational burden for the `DEFAULT_ADMIN_ROLE`. If a new fee recipient needs to be inserted with an address that falls between two existing recipients, all subsequent recipients must be removed and then re-added in the correct sorted order. This process is gas-intensive and could be exploited as a griefing vector if an attacker gains admin access, making it

**Recommendation:** Consider alternative methods for managing fee recipients that do not impose strict sorting requirements, such as using a mapping for individual recipient portions or allowing for unsorted additions/removals with internal sorting logic if necessary. If sorting is deemed essential, provide helper functions to simplify the process of adding, removing, or updating recipients without requiring a full re-submission of the entire list.


### `M-03` — Centralized Control over Critical Functions  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DEFAULT_ADMIN_ROLE` in the Folio contract possesses extensive privileges, including the ability to set TVL and mint fees, modify the asset basket (add/remove tokens), set auction length, change the mandate, and deprecate the entire Folio. While `REBALANCE_MANAGER` and `AUCTION_LAUNCHER` roles also control significant aspects of rebalancing and auctions, the `DEFAULT_ADMIN_ROLE`'s broad authority centralizes control. This poses a significant single point of failure and a high risk of malicious actions or accidental errors if the admin key is compromised. Unlike the proxy admin, there is no apparent Timelock protect

**Recommendation:** Implement a Timelock mechanism for the `DEFAULT_ADMIN_ROLE` to introduce a mandatory delay for critical administrative actions. This would allow time for review and potential intervention, significantly reducing the risk associated with centralized control. Consider further decentralizing roles where appropriate.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x8d38…a01d — holds 98.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 39% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Lack of Timelock for `DEFAULT_ADMIN_ROLE` Actions  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). While the proxy's administrative functions are protected by a Timelock, the `DEFAULT_ADMIN_ROLE` within the `Folio` contract itself can execute critical operations (e.g., `setTVLFee`, `setMintFee`, `addToBasket`, `deprecateFolio`) immediately. The absence of a Timelock for these internal administrative actions means there is no delay period for community review or emergency intervention, increasing the risk of immediate damage from a compromised or malicious admin key (7.3 Access Control, 7.5 Governance).

**Recommendation:** Integrate a Timelock mechanism for the `DEFAULT_ADMIN_ROLE` to introduce a delay for all critical administrative functions. This would provide a window for monitoring and potential mitigation, enhancing the overall security and governance posture of the protocol.


### `L-02` — Presence of Deprecated Variables and Code  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract contains several `_DEPRECATED` variables and mappings (e.g., `auctions_DEPRECATED`, `sellEnds_DEPRECATED`, `buyEnds_DEPRECATED`, `auctionDelay_DEPRECATED`, `auctionDetails_DEPRECATED`, `dustAmount_DEPRECATED`). While these are explicitly marked as deprecated, their continued presence in the codebase adds to its complexity, increases the contract's deployed size, and could potentially lead to confusion for developers or auditors. It also suggests that the contract might have undergone significant architectural changes without full cleanup (7.2 Code Security).

**Recommendation:** Remove all deprecated variables and associated code paths from the contract. If historical data or functionality is still required, consider migrating it to a separate, immutable data contract or ensuring that the deprecated code is entirely unreachable and does not consume unnecessary gas or storage.


### `I-01` — Reliance on `block.timestamp` for Time-Sensitive Operations  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract extensively uses `block.timestamp` for various time-sensitive operations, including fee accounting (`lastPoke`, `_getPendingFeeShares`), auction timing (`auctionLength`, `auctions[auctionId].endTime`), and rebalance availability (`rebalance.startedAt`, `rebalance.restrictedUntil`, `rebalance.availableUntil`). While `block.timestamp` is commonly used, it can be manipulated by miners within a certain range (up to 900 seconds on Ethereum mainnet). For critical operations, this manipulation could potentially lead to minor timing discrepancies or, in specific scenarios, be exploited by a malicious miner to gain

**Recommendation:** For highly critical time-sensitive operations where miner manipulation of `block.timestamp` could have significant adverse effects, consider using a more robust and decentralized time oracle (e.g., Chainlink Keepers or a custom oracle solution). For less critical operations, `block.timestamp` is generally acceptable, but be aware of its limitations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 94.4% of supply. What remains: 79.1% in wallets, 15.3% in other contracts. 19,596 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CF Large Cap Index (LCAP), market cap $5M, rank #1671. 19,596 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $993K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 6 pools. Launch: 423 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4da9...e6e8`](https://basescan.org/address/0x4da9a0f397db1397902070f93a4d6ddbc0e0e6e8) |
| **Network** | Base |
| **Price** | $6.8200 |
| **24h Volume** | $1.14M |
| **Liquidity** | $480.2K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 237 buys / 393 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x3a88ef38879efb900c2d7b6199d21c139cef5fa7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cf-large-cap-index-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
