---
token: Plume
ticker: PLUME
network: ethereum
risk_score: 35
status: medium
date: 2026-10-12
---

# Plume (PLUME) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/plume-eth)

---

## Audit Summary

The audit found no critical or high-severity vulnerabilities in the provided contract code. The Plume token utilizes standard OpenZeppelin libraries for ERC-20, UUPS upgradeability, and access control, demonstrating a robust architectural foundation. Centralized roles for minting, pausing, and upgrades are present, which is typical for a controlled token supply.

> **Final Recommendation:** It is recommended to implement robust multi-signature wallet controls for all privileged roles, including `MINTER_ROLE`, `PAUSER_ROLE`, and the upgrade administrator role. This decentralizes control and significantly reduces the risk associated with a single point of failure. Additionally, consider establishing clear governance procedures and transparency around the exercise of these powerful roles to build community trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The Plume token (7.1 Architecture) is built upon well-audited OpenZeppelin contracts, inheriting ERC-20, UUPS upgradeability, Pausable, Burnable, and AccessControl features. This provides a solid and… |
| **Governance / Economics** | 2/10 | High | The contract implements standard ERC-20 token functionality, including `mint` and `burn` capabilities, allowing for flexible supply management (7.4 Economic). Access to these critical functions is… |
| **Upgrades** | 1/10 | High | The contract utilizes the UUPS proxy pattern, enabling secure and controlled upgrades to the contract logic (7.7 Upgrades). This allows for bug fixes, feature enhancements, and adaptation to future… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 33.9% |
| **Top-3 Unlocked** | 72.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — an owner that could not be resolved — mint new supply; pause all transfers. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.1% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 32% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 63.7% of supply. What remains: 17.5% in wallets, 46.2% in other contracts. 25,268 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Plume (PLUME), market cap $152M, rank #226. Traded on Coinbase. 25,268 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $116K (DexScreener, all pools). 24h trading volume $73.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $217K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.248 on 2025-03-19; the price is now 90.7163% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $116K of DEX liquidity across 10 pools. Launch: 629 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4c17...a5f1`](https://etherscan.io/address/0x4c1746a800d224393fe2470c70a35717ed4ea5f1) |
| **Network** | Ethereum |
| **Price** | $0.02313 |
| **24h Volume** | $139.4K |
| **Liquidity** | $37.0K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 63.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 199 buys / 140 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf0cd01da66753629340436cee3b26dc4a7d63cbee01e2f2d7c8230a8210526cc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/plume-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
