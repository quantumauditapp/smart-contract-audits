---
token: QuickSwap
ticker: QUICK
network: polygon
risk_score: 36
status: medium
date: 2026-10-20
---

# QuickSwap (QUICK) — Smart Contract Security Analysis | Polygon

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quickswap-poly)

---

## Audit Summary

The Quick token is a standard ERC-20 implementation with additional minting and burning capabilities. The architecture is straightforward, utilizing a gateway-based minting mechanism. While the code is functional, it lacks a standard totalSupply() function, which may cause compatibility issues with some DeFi protocols. The primary risk involves the centralized control over token supply via the gateway address.

> **Final Recommendation:** It is recommended to implement the standard totalSupply() function to ensure full compatibility with external DeFi aggregators and wallets. Additionally, consider transitioning the gateway control to a multi-signature wallet or a decentralized governance contract to mitigate the risk of centralized minting authority.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 transfer logic with safe arithmetic checks. 7.1 Architecture is simple and modular, relying on a gateway for minting. 7.2 Code Security is maintained through… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic risk is tied to the minting authority held by the gateway. 7.5 Governance is currently centralized, as the gateway address has the power to increase supply. This allows for potential… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against unauthorized logic changes. 7.8 Operations are stable due to the lack of complex… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The deposit(address,bytes) function allows a privileged 'gateway' address to mint new tokens at will. This increases the total supply and dilutes the value of existing holdings for all token holders.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or a time-locked governance contract to prevent single-point-of-failure risks.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.5% of supply. Of that, 12.2% burned — not holders that can sell, so excluded from the concentration score. What remains: 23.3% in wallets, 46.0% in other contracts. 54,433 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Quickswap (QUICK), market cap $4M, rank #1771. On GoPlus's list of trusted tokens. Traded on Binance. 54,433 holders. Verified by: GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $387K (DexScreener, all pools). 24h trading volume $957K (CoinGecko, all markets, daily snapshot). 24h trading volume $325K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.23 on 2022-05-05; the price is now 97.1881% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: gateway — a role-controlled contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $387K of DEX liquidity across 30 pools. Launch: 1631 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb5c0...ee17`](https://polygonscan.com/address/0xb5c064f955d8e7f38fe0460c556a72987494ee17) |
| **Network** | Polygon |
| **Price** | $0.006269 |
| **24h Volume** | $120.1K |
| **Liquidity** | $191.1K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 4y |
| **Top-10 Holders** | 81.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 844 buys / 1058 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0xde2d1fd2e8238aba80a5b80c7262e4833d92f624)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quickswap-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
