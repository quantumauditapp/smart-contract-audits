---
token: WhaleBit
ticker: CES
network: polygon
risk_score: 60
status: medium
date: 2026-10-20
---

# WhaleBit (CES) — Smart Contract Security Analysis | Polygon

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/whalebit-poly)

---

## Audit Summary

The CES_tokenV1 is a standard ERC-20 implementation utilizing the UUPS proxy pattern. The contract includes centralized administrative controls for minting, token metadata management, and user blacklisting. While the code follows standard OpenZeppelin patterns, the presence of a blacklist mechanism introduces a degree of centralization risk for token holders.

> **Final Recommendation:** The protocol should consider implementing a multi-signature wallet or a timelock controller for the DEFAULT_ADMIN_ROLE to mitigate the risks associated with centralized control. This would ensure that sensitive operations like blacklisting or minting require consensus rather than a single point of failure.

Additionally, users should be aware that the token is subject to administrative intervention. We recommend documenting the criteria for blacklisting to provide transparency to the community regarding the use of the blockUser function.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture leverages UUPS proxy patterns for upgradeability, ensuring gas efficiency and standard compliance. 7.1 Architecture is robust, utilizing OpenZeppelin's battle-tested libraries. 7.2… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized, as the admin holds the ability to mint tokens and blacklist users. This design allows for rapid response to security incidents but creates a… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via the UUPS pattern, which is the industry standard for secure proxy updates. 7.8 Operations are supported by clear administrative functions for role management and stuck… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 83.9% |
| **Top-3 Unlocked** | ⚠️ 92.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-06` — Centralized Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The contract includes a blacklist mechanism managed by the admin. The functions blockUser and unblockUser allow the administrator to prevent specific addresses from transferring or receiving tokens, effectively freezing their assets.

**Recommendation:** Implement a timelock or multi-signature requirement for the admin role to prevent unilateral and potentially malicious use of the blacklisting functionality.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.1% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0xa741…0c2a — holds 83.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 83.5% of supply. What remains: 4.8% in wallets, 78.6% in other contracts. 294,785 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Whalebit (CES). 294,785 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $49K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $483K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $7.08 on 2025-09-29; the price is now 97.8707% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable, capped at 0.0% of supply per year. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $49K of DEX liquidity across 8 pools. Launch: 535 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1bdf...1610`](https://polygonscan.com/address/0x1bdf71ede1a4777db1eebe7232bcda20d6fc1610) |
| **Network** | Polygon |
| **Price** | $0.1943 |
| **24h Volume** | $482.7K |
| **Liquidity** | $49.4K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 83.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1542 buys / 1657 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x296b95dd0e8b726c4e358b0683ff0b6d675c35e9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/whalebit-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
