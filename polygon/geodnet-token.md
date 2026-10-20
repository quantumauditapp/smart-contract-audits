---
token: Geodnet Token
ticker: GEOD
network: polygon
risk_score: 36
status: medium
date: 2026-10-20
---

# Geodnet Token (GEOD) — Smart Contract Security Analysis | Polygon

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/geodnet-token-poly)

---

## Audit Summary

The XToken contract is a standard ERC-20 implementation with added administrative controls for minting, pausing, and blacklisting. While the code follows established OpenZeppelin patterns (7.1 Architecture), it grants significant centralized power to privileged roles (7.3 Access Control). The protocol relies on trust in the administrative entities, as there are no time-locks or multi-signature requirements visible in the current configuration.

> **Final Recommendation:** To improve security, transition the administrative roles from single addresses to a multi-signature wallet or a decentralized governance contract. This would mitigate the risk of a single compromised key performing unauthorized minting or freezing actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard, battle-tested OpenZeppelin libraries for ERC-20 functionality and access control (7.2 Code Security). The logic for minting and pausing is correctly implemented with… |
| **Governance / Economics** | 6/10 | Medium | The economic model is highly centralized, allowing the minter role to increase supply at will (7.4 Economic). Governance is currently managed via simple role-based access without decentralized… |
| **Upgrades** | 6/10 | Medium | The contract is not a proxy and does not support upgrades (7.7 Upgrades). This ensures the code logic is immutable, which provides security against malicious logic changes. Operations are limited to… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 95.3% |
| **Top-3 Unlocked** | ⚠️ 98.2% |

## Security Findings

_🟡 4 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows a designated minter to create new tokens, which can dilute the value of existing holdings.

**Recommendation:** Implement a multi-signature requirement for minting or establish a hard-coded supply limit that cannot be adjusted by privileged roles.


### `CP-04` — Centralized Pause Mechanism  *(Severity: Medium · Status: Unresolved)*

The pause and unpause functions allow an administrator to halt all token transfers, effectively locking all user funds at will.

**Recommendation:** Restrict the pause functionality to emergency scenarios only and consider adding a time-lock to the pause/unpause actions.


### `CP-06` — Blacklisting Capability  *(Severity: Medium · Status: Unresolved)*

The freeze and defrost functions allow a blacklister to prevent specific addresses from transferring their tokens, creating a censorship risk.

**Recommendation:** Define clear, transparent criteria for blacklisting and require multi-party approval for any address to be frozen.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 8 address(es) other than the owner/deployer. One of them — a wallet, 0xdfaf…5034 — holds 95.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 44% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 85.1% of supply. Of that, 4.0% burned — not holders that can sell, so excluded from the concentration score. What remains: 9.7% in wallets, 71.4% in other contracts. 16,877 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Geodnet (GEOD), market cap $126M, rank #240. 16,877 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $1.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $148K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 16 pools. Launch: 1601 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xac0f...9adb`](https://polygonscan.com/address/0xac0f66379a6d7801d7726d5a943356a172549adb) |
| **Network** | Polygon |
| **Price** | $0.2722 |
| **24h Volume** | $105.0K |
| **Liquidity** | $524.7K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4y |
| **Top-10 Holders** | 85.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 415 buys / 332 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x5fe84b85ba7dea0fbc8c4571491aca80d97f5e01)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/geodnet-token-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
