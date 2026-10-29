---
token: Instadapp (PoS)
ticker: INST
network: polygon
risk_score: 41
status: medium
date: 2026-10-29
---

# Instadapp (PoS) (INST) — Smart Contract Security Analysis | Polygon

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/instadapp-pos-poly)

---

## Audit Summary

The UChildERC20 contract serves as a bridge-compatible token implementation on Polygon. The architecture relies on standard OpenZeppelin-style access control and ERC20 logic. While the core token functionality is robust, the contract includes privileged minting capabilities and lacks a mechanism to recover accidentally sent ETH, which are common patterns for bridge-linked assets but introduce specific trust requirements.

> **Final Recommendation:** The protocol should implement a 'rescue' function to allow the recovery of accidentally sent native tokens (ETH/MATIC) to the contract address. Additionally, ensure that the DEPOSITOR_ROLE is held by a multi-signature wallet or a time-locked governance contract to mitigate the risk of unauthorized minting events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC20 and AccessControl, ensuring standard compliance. 7.1 Architecture follows a proxy pattern for upgradeability, while 7.2 Code… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is primarily driven by the centralized minting authority, which can impact token supply. 7.5 Governance is handled via role-based access control, allowing for granular permission… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are managed via a proxy pattern, allowing for logic updates without state migration. 7.8 Operations are stable, with no complex logic dependencies that would complicate future upgrades.… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — Locked Native Tokens  *(Severity: Medium · Status: Unresolved)*

The contract can receive native tokens (ETH/MATIC) but lacks any function to withdraw them. Any funds sent to the contract address will be permanently locked.

**Recommendation:** Implement a withdrawal function restricted to the contract owner to allow for the recovery of accidentally sent native assets.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The deposit function allows a privileged address to mint new tokens at will. This increases the total supply and can dilute the value of existing holdings if the privileged account is compromised.

**Recommendation:** Restrict the DEPOSITOR_ROLE to a multi-signature wallet or a decentralized governance contract to prevent single-point-of-failure risks.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a contract, 0x362d…7994 — holds 99.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.5% of supply. Of that, 57.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.3% in wallets, 15.6% in other contracts. 4,516 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Fluid (FLUID), market cap $177M, rank #191. 4,516 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $752K (DexScreener, all pools). 24h trading volume $1.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $42K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $24.40 on 2021-06-16; the price is now 91.3328% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $752K of DEX liquidity across 13 pools. Launch: 1961 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf50d...7dee`](https://polygonscan.com/address/0xf50d05a1402d0adafa880d36050736f9f6ee7dee) |
| **Network** | Polygon |
| **Price** | $1.9100 |
| **24h Volume** | $40.9K |
| **Liquidity** | $744.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 80.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 76 buys / 132 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0xe30e4dfdbb10949c27501922f845e20cfa579f09)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/instadapp-pos-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
