---
token: AltLayer Token
ticker: ALT
network: ethereum
risk_score: 41
status: medium
date: 2026-10-10
---

# AltLayer Token (ALT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/altlayer-token-eth)

---

## Audit Summary

This audit of the AltLayerToken contract identifies it as a standard ERC-20 token with additional features such as pausing, capping, burning, and permit functionality. The contract is not upgradeable and its ownership is retained by a multisig wallet. Two medium-severity findings were identified, primarily related to the owner's ability to mint new tokens and pause transfers, which introduce centralization risks. Only two findings were identified, which is fewer than the typical range of 3-8.

> **Final Recommendation:** It is crucial to ensure the security of the owner's private keys, ideally by using a robust multi-signature wallet with a high threshold for critical operations. Clear communication to the community regarding the circumstances under which minting or pausing might occur is also recommended to maintain transparency and trust. Consider implementing time-locks or community governance for sensitive functions like minting and pausing to further decentralize control and reduce single points of failure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The AltLayerToken contract implements a standard ERC-20 token with additional features like pausing, capping, burning, and permit functionality (7.1 Architecture). The code base inherits from… |
| **Governance / Economics** | 2/10 | High | Economically, the owner's ability to mint new tokens directly impacts the token supply, potentially leading to dilution for existing holders (7.4 Economic). The power to pause transfers can disrupt… |
| **Upgrades** | 4/10 | Medium | The AltLayerToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic cannot be changed after deployment, providing immutability and predictability for token… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 91.2% of supply. What remains: 10.8% in wallets, 80.4% in other contracts. The deployer/owner wallet itself holds 26.3%. A holder that also controls the contract can sell into its own liquidity. 73,347 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — Owner Can Create New Tokens  *(Severity: Medium · Status: Unresolved)*

The contract owner has the ability to create new AltLayer tokens using the `mint(address,uint256)` function. This means the total supply of tokens can be increased at any time, which could dilute the value of existing tokens held by other users.

**Recommendation:** Token holders should be aware that the owner retains the power to mint new tokens. It is recommended that the owner's key be secured with a robust multi-signature setup and that a clear policy for minting, if any, is communicated to the community.


### `CP-04` — Owner Can Stop All Token Transfers  *(Severity: Medium · Status: Unresolved)*

The contract owner can halt all token transfers by calling the `pause()` function, and resume them with `unpause()`. This capability, while potentially useful in emergencies (e.g., to stop an exploit), gives the owner significant control over the token's liquidity and usability, as they can prevent users from moving their tokens.

**Recommendation:** Token holders should understand that the owner can temporarily freeze all token movements. It is crucial that the owner's key is highly secured, ideally with a multi-signature wallet, and that the community is informed about the circumstances under which pausing might occur.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x7966…e764 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AltLayer (ALT), market cap $61M, rank #420. Traded on Binance, Coinbase. 73,347 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $8.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $36K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.677 on 2024-03-28; the price is now 98.7708% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $100K of DEX liquidity across 3 pools. Launch: 989 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8457...fbfb`](https://etherscan.io/address/0x8457ca5040ad67fdebbcc8edce889a335bc0fbfb) |
| **Network** | Ethereum |
| **Price** | $0.008044 |
| **24h Volume** | $34.4K |
| **Liquidity** | $98.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 2y |
| **Top-10 Holders** | 91.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 99 buys / 76 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x65680a987f4871a7bb865c86fae11667e6aa8068)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/altlayer-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
