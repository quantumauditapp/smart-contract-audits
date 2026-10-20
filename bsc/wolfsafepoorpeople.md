---
token: WolfSafePoorPeople
ticker: WSPP
network: bsc
risk_score: 72
status: high
date: 2026-10-10
---

# WolfSafePoorPeople (WSPP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wolfsafepoorpeople-bsc)

---

## Audit Summary

The WolfSafePoorPeople contract is an ERC-20 token with retained ownership. The owner has significant control over token distribution and individual balances through functions like `getAirdrop` and `tokenSale`. A high-severity issue was identified where the owner can directly manipulate user balances, alongside a low-severity issue related to potential rounding losses in token calculations during sales.

> **Final Recommendation:** Token holders should be fully aware of the extensive control retained by the contract owner, particularly the ability to directly modify token balances and manage all aspects of token distribution and sales. It is recommended to thoroughly understand the implications of this centralized control on the project's long-term security and economic stability. For future contracts, consider implementing more decentralized control mechanisms or multi-signature wallets for critical operations to mitigate single points of failure and enhance trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract implements standard ERC-20 token functionalities (7.1 Architecture). However, it grants the owner direct control over user balances via `getAirdrop` and `tokenSale` functions, which… |
| **Governance / Economics** | 3/10 | High | The economic model is heavily centralized, with the owner having full control over airdrop and token sale parameters (7.4 Economic). The owner can set start/end blocks, amounts, and prices for both… |
| **Upgrades** | 6/10 | Medium | The contract is not designed with an upgrade mechanism (7.7 Upgrades), meaning its logic cannot be modified after deployment. This eliminates upgrade-related risks but also removes any flexibility… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 45.3% |
| **Top-3 Unlocked** | 78.3% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `CP-02` — Owner can directly change token balances  *(Severity: High · Status: Unresolved)*

The contract owner possesses the ability to directly modify token balances of any holder through the `getAirdrop` and `tokenSale` functions. This means the owner can increase or decrease anyone's token holdings without their consent, effectively burning or moving tokens out of any address they target.

**Recommendation:** Token holders should be aware that the contract owner possesses significant control over token distribution and individual balances. This centralized control introduces a high level of trust in the owner's actions. Consider if this level of control aligns with the project's decentralization goals.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 94.7% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. This assessment covers the main pool, which holds 88% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CD-01` — Potential for minor token loss due to calculation order  *(Severity: Low · Status: Unresolved)*

In the `tokenSale` function, the calculation for the number of tokens to be distributed involves division before multiplication (`_eth / sPrice` then `sChunk * _price`). This order can lead to rounding down, resulting in a small loss of tokens for the buyer, especially with small `_eth` values or high `sPrice`.

**Recommendation:** While the impact might be minor, it's generally safer to perform multiplication before division to preserve precision (`_eth * sChunk / sPrice`). This ensures that no fractional tokens are lost due to integer division.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 87.0% of supply. Of that, 77.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.4% in wallets, 8.7% in other contracts. 202,793 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as WolfSafePoorPeople (WSPP), market cap $6M, rank #1552. 202,793 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $82K (DexScreener, all pools). 24h trading volume $41K (CoinGecko, all markets, daily snapshot). 24h trading volume $41K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $82K of DEX liquidity across 21 pools. Launch: 1962 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x46d5...d36f`](https://bscscan.com/address/0x46d502fac9aea7c5bc7b13c8ec9d02378c33d36f) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $37.7K |
| **Liquidity** | $72.4K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 5y |
| **Top-10 Holders** | 87.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 408 buys / 565 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x31fdf4333d2edcadcebd25edd7dabcb73b27e851)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wolfsafepoorpeople-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
