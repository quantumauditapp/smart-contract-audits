---
token: PancakeSwap Token
ticker: CAKE
network: bsc
risk_score: 21
status: low
date: 2026-08-11
---

# PancakeSwap Token (CAKE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pancakeswap-token-bsc)

---

## Audit Summary

The CakeToken contract is a standard BEP-20 token implementation with additional minting capabilities. The architecture is straightforward, relying on OpenZeppelin's Ownable and BEP20 patterns. The primary risk is centralized control over the total supply via the minting functions, which is typical for this type of governance token.

> **Final Recommendation:** The protocol should consider transitioning ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of centralized minting. This would ensure that any increase in total supply requires community consensus rather than a single privileged address.

Additionally, ensure that the private keys associated with the owner address are stored in a secure, hardware-backed environment. Regular monitoring of the minting functions is recommended to detect any unauthorized supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 functionality. 7.1 Architecture is modular and follows standard patterns. 7.2 Code Security is robust, with no evidence of… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance risks are centered on the owner's ability to mint tokens. This allows the owner to unilaterally dilute the supply, which is a significant trust requirement. 7.6… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable, and the lack of upgradeability ensures immutability of the core logic. No upgrade-related risks are present. |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner of the contract has the ability to call mint(uint256) and mint(address, uint256) to create new tokens at will. This allows the controller to increase the total supply, which directly dilutes the value of existing tokens held by users.

**Recommendation:** Consider implementing a time-lock mechanism for minting operations or transferring ownership to a DAO-controlled contract to prevent unilateral supply inflation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.2% of supply. Of that, 94.1% burned — not holders that can sell, so excluded from the concentration score. What remains: 2.2% in wallets, 0.8% in other contracts. 1,911,330 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PancakeSwap (CAKE), market cap $668M, rank #92. On GoPlus's list of trusted tokens. Traded on Binance. 1,911,330 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19.2M (DexScreener, all pools). 24h trading volume $51.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.6M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $43.96 on 2021-04-30; the price is now 95.2158% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19.2M of DEX liquidity across 30 pools. Launch: 2011 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0e09...ce82`](https://bscscan.com/address/0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82) |
| **Network** | BNB Chain |
| **Price** | $2.1100 |
| **24h Volume** | $921.6K |
| **Liquidity** | $6.28M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5y |
| **Top-10 Holders** | 97.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 209 buys / 268 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x7f51c8aaa6b0599abd16674e2b17fec7a9f674a1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pancakeswap-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
