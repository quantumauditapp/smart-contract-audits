---
token: DODO bird
ticker: DODO
network: bsc
risk_score: 40
status: medium
date: 2026-10-26
---

# DODO bird (DODO) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dodo-bird-bsc)

---

## Audit Summary

The DODOBscToken contract is a standard ERC-20 implementation with an ownership-based minting mechanism. The code is concise and follows established patterns for token management. The primary risk involves the centralized authority to mint new tokens, which impacts tokenomics.

> **Final Recommendation:** The protocol should consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. Additionally, implementing a timelock on the mint function would provide transparency and protection for token holders against sudden supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard Ownable pattern for administrative tasks. 7.1 Architecture is straightforward, utilizing OpenZeppelin-style ownership. 7.2 Code Security is high, with standard… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is centered on the minting capability, which allows for supply inflation. 7.5 Governance is currently centralized under the owner address. 7.6 External dependencies are minimal… |
| **Upgrades** | 2/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are stable, with no complex state transitions. The contract logic is immutable once deployed. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 77.7% |
| **Top-3 Unlocked** | ⚠️ 85.9% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint function allows the owner to create new tokens at will. This increases the total supply and dilutes the value of existing holdings, as the owner has unilateral control over the token's inflation.

**Recommendation:** Restrict the minting capability by implementing a multi-signature requirement or a timelock, or document the minting schedule clearly to ensure transparency for all token holders.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 92.7% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x73fe…e24e — holds 77.7% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 77% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $57K (DexScreener, all pools). 24h trading volume $42.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $132K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $8.38 on 2021-02-20; the price is now 99.7192% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 42.5% of supply. Of that, 1.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 36.5% in wallets, 4.2% in other contracts. 62,377 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as DODO (DODO), market cap $24M, rank #749. On GoPlus's list of trusted tokens. Traded on Binance. 62,377 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: owner_ — a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $57K of DEX liquidity across 30 pools. Launch: 2011 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x67ee...29e2`](https://bscscan.com/address/0x67ee3cb086f8a16f34bee3ca72fad36f7db929e2) |
| **Network** | BNB Chain |
| **Price** | $0.02329 |
| **24h Volume** | $124.4K |
| **Liquidity** | $44.3K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 5y |
| **Top-10 Holders** | 42.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4312 buys / 4177 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xa9986fcbdb23c2e8b11ab40102990a08f8e58f06)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dodo-bird-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
