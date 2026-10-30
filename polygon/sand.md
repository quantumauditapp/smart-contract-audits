---
token: SAND
ticker: SAND
network: polygon
risk_score: 50
status: medium
date: 2026-10-30
---

# SAND (SAND) — Smart Contract Security Analysis | Polygon

> **Risk Score: 50/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sand-poly)

---

## Audit Summary

The PolygonSand contract is a bridge-enabled ERC-20 token on Polygon. It utilizes a highly privileged administrative structure, including 'SuperOperators' and a 'ChildChainManager', which possess extensive control over token balances, supply, and allowances. While the architecture is standard for cross-chain assets, the centralization of power presents significant trust requirements for users.

> **Final Recommendation:** Users should be aware that the 'SuperOperator' and 'ChildChainManager' roles have the technical capability to move or burn tokens from any address. It is recommended that the project maintain strict multisig requirements for these roles and provide transparent documentation regarding the operational procedures for these privileged functions.

For future iterations, consider implementing a timelock on administrative actions that affect token supply or user balances to provide a window for community oversight and incident response.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements a robust ERC-20 standard with additional extensions for meta-transactions and cross-chain bridging. 7.1 Architecture: Uses a centralized bridge manager for minting. 7.2 Code… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: The total supply is elastic and controlled by the bridge manager. 7.5 Governance: Administrative roles are held by a multisig, providing a layer of protection against… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades: The contract is not currently using a proxy pattern, making the logic immutable. 7.8 Operations: Administrative parameters like the ChildChainManager and TrustedForwarder can be updated… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.9% |
| **Top-3 Unlocked** | 55.0% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `CP-02` — Privileged Balance Manipulation  *(Severity: High · Status: Unresolved)*

The 'burnFor' function allows 'SuperOperators' to directly modify the balance of any user address. This effectively allows these operators to seize or destroy tokens from any holder without their explicit consent.

**Recommendation:** Restrict the 'SuperOperator' role to the absolute minimum number of addresses and implement a timelock for any balance-altering operations.


### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The 'deposit' function allows the 'ChildChainManager' to mint new tokens, and the 'withdraw' function allows 'SuperOperators' to burn tokens. This grants privileged addresses the ability to alter the total supply, which can dilute the value of existing holdings.

**Recommendation:** Ensure the 'ChildChainManager' address is secured by a multisig and monitor its activity for unexpected minting events.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 62.3% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $198K (DexScreener, all pools). 24h trading volume $39.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $39K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $8.40 on 2021-11-24; the price is now 99.4527% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.1% of supply. Of that, 1.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 49.2% in wallets, 19.4% in other contracts. 157,881 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as The Sandbox (SAND), market cap $135M, rank #223. Traded on Binance. 157,881 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $198K of DEX liquidity across 30 pools. Launch: 1807 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbbba...5683`](https://polygonscan.com/address/0xbbba073c31bf03b8acf7c28ef0738decf3695683) |
| **Network** | Polygon |
| **Price** | $0.0439 |
| **24h Volume** | $30.7K |
| **Liquidity** | $180.3K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 70.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 386 buys / 500 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x369582d2010b6ed950b571f4101e3bb9b554876f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sand-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
