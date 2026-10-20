---
token: Uniswap (PoS)
ticker: UNI
network: polygon
risk_score: 33
status: low
date: 2026-10-20
---

# Uniswap (PoS) (UNI) — Smart Contract Security Analysis | Polygon

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uniswap-pos-poly)

---

## Audit Summary

The UChildERC20 contract functions as a bridge-compatible token on Polygon. It utilizes a standard OpenZeppelin-based access control and proxy pattern. While the core ERC-20 logic is standard, the contract includes privileged minting capabilities and a lack of mechanisms to recover accidentally sent ETH, which are common in bridge-related implementations.

> **Final Recommendation:** The protocol should implement a 'sweep' function restricted to an admin role to allow the recovery of accidentally sent native ETH. Additionally, ensure that the keys associated with the DEPOSITOR_ROLE are managed via a multi-signature wallet to mitigate the risk of unauthorized supply inflation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The architecture follows standard proxy patterns (7.1 Architecture) and utilizes well-vetted OpenZeppelin libraries for ERC-20 and AccessControl (7.2 Code Security). The implementation is clean and… |
| **Governance / Economics** | 5/10 | Medium | The economic model relies on the DEPOSITOR_ROLE to manage supply (7.4 Economic). This centralizes control over token inflation, which is expected for bridge tokens but represents a significant trust… |
| **Upgrades** | 1/10 | High | The contract utilizes a proxy pattern (7.7 Upgrades) allowing for logic updates. The implementation is verified and consistent with standard UUPS/Transparent proxy patterns. No immediate upgrade… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 21.6% |
| **Top-3 Unlocked** | 40.6% |

## Security Findings

_🟡 3 Medium · ⚪ 4 Informational_

### `CD-01` — Trapped Native ETH  *(Severity: Medium · Status: Unresolved)*

The contract accepts native ETH through meta-transactions but lacks a function to withdraw or transfer these funds out of the contract. Any ETH sent to the contract address will be permanently locked.

**Recommendation:** Add an administrative function to withdraw native ETH from the contract balance to a designated treasury address.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The deposit function allows addresses with the DEPOSITOR_ROLE to mint new tokens at will. This centralizes control over the total supply and allows the controller to dilute existing token holders.

**Recommendation:** Implement a multi-signature requirement for the DEPOSITOR_ROLE and maintain transparency regarding the minting process via public event logs.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 70.6% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 48% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 16.8% of supply. Of that, 6.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.2% in wallets, 5.9% in other contracts. 69,439 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Uniswap (UNI), market cap $4.5B, rank #26. On GoPlus's list of trusted tokens. Traded on Binance. 69,439 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $349K (DexScreener, all pools). 24h trading volume $301.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $72K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $349K of DEX liquidity across 30 pools. Launch: 2200 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb33e...180f`](https://polygonscan.com/address/0xb33eaad8d922b1083446dc23f610c2567fb5180f) |
| **Network** | Polygon |
| **Price** | $7.3100 |
| **24h Volume** | $36.0K |
| **Liquidity** | $166.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 6y |
| **Top-10 Holders** | 16.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 124 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x357faf5843c7fd7fb4e34fbeabdac16eabe8a5bc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uniswap-pos-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
