---
token: Lido DAO Token (PoS)
ticker: LDO
network: polygon
risk_score: 34
status: low
date: 2026-10-29
---

# Lido DAO Token (PoS) (LDO) — Smart Contract Security Analysis | Polygon

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lido-dao-token-pos-poly)

---

## Audit Summary

The UChildERC20 contract functions as a bridge-compatible token on Polygon. It utilizes standard OpenZeppelin access control and proxy patterns. While the core ERC-20 logic is standard, the contract contains centralized minting capabilities and a lack of mechanisms to recover accidentally sent ETH, which are common in bridge-token implementations.

> **Final Recommendation:** The protocol should implement a 'sweep' function to allow the owner to recover accidentally sent ETH, preventing permanent loss of funds. Additionally, the minting authority should be monitored via multi-signature wallets or timelocks to mitigate the risk of unauthorized supply inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture follows standard proxy patterns (7.1) and utilizes well-vetted OpenZeppelin libraries for access control (7.3). Code security (7.2) is high due to the use of established standards… |
| **Governance / Economics** | 5/10 | Medium | Economic risk (7.4) is centered on the minting authority held by the DEPOSITOR_ROLE. Governance (7.5) is centralized, allowing the owner or designated roles to influence supply. This is typical for… |
| **Upgrades** | 1/10 | High | The contract utilizes a proxy pattern (7.7) allowing for logic updates. Upgrades are managed via standard administrative roles, ensuring a controlled path for maintenance. No issues were identified… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 24.2% |
| **Top-3 Unlocked** | 35.8% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH through meta-transactions or direct transfers but lacks a withdrawal function to move these funds out, leading to permanent loss of any ETH sent to the contract address.

**Recommendation:** Implement a function that allows the owner to withdraw any ETH accidentally sent to the contract.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The deposit function allows addresses with the DEPOSITOR_ROLE to mint new tokens, which increases the total supply and dilutes existing holders. This is a powerful administrative privilege.

**Recommendation:** Restrict the DEPOSITOR_ROLE to a multi-signature wallet or a time-locked contract to prevent single-point-of-failure risks.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 59.4% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 49% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 40.1% of supply. Of that, 19.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.3% in wallets, 5.3% in other contracts. 29,274 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Lido DAO (LDO), market cap $302M, rank #137. Traded on Binance. 29,274 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $161K (DexScreener, all pools). 24h trading volume $37.9M (CoinGecko, all markets, daily snapshot). 24h trading volume $73K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $7.30 on 2021-08-20; the price is now 95.0136% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $161K of DEX liquidity across 28 pools. Launch: 1699 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xc3c7...8756`](https://polygonscan.com/address/0xc3c7d422809852031b44ab29eec9f1eff2a58756) |
| **Network** | Polygon |
| **Price** | $0.3389 |
| **24h Volume** | $35.8K |
| **Liquidity** | $78.3K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 4y |
| **Top-10 Holders** | 40.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 235 buys / 305 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0xda908c0bf14ad0b61ea5ebe671ac59b2ce091cbf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lido-dao-token-pos-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
