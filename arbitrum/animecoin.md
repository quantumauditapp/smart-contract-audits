---
token: Animecoin
ticker: ANIME
network: arbitrum
risk_score: 62
status: medium
date: 2026-10-16
---

# Animecoin (ANIME) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 62/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/animecoin-arb)

---

## Audit Summary

The Animecoin contract is an ERC-20 token with voting capabilities. It includes privileged functions, `bridgeMint` and `bridgeBurn`, controlled by an `l2gateway` address. These functions allow the `l2gateway` to create new tokens or destroy existing tokens from any holder's balance, posing significant centralization and economic risks.

> **Final Recommendation:** It is crucial to ensure the `l2gateway` address, which controls the `bridgeMint` and `bridgeBurn` functions, is secured with the highest possible standards. Implement robust multi-signature controls, time-locks, or a decentralized governance mechanism for this address to mitigate the risks of centralized control and potential misuse. Token holders should be fully aware of the extensive powers granted to the `l2gateway`.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Animecoin contract implements standard ERC-20 functionality, including `transfer`, `transferFrom`, and `approve`, along with ERC-20 Votes extensions, ensuring broad compatibility (7.1… |
| **Governance / Economics** | 1/10 | High | The contract integrates ERC-20 Votes, enabling decentralized governance mechanisms for future protocol decisions (7.5 Governance). However, the `l2gateway` address holds significant economic power… |
| **Upgrades** | 3/10 | High | The Animecoin contract is not implemented as a proxy and does not include any self-upgrade mechanisms, providing immutability (7.7 Upgrades). As a non-upgradeable contract, any discovered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `CP-02` — Centralized Control Over Token Balances  *(Severity: High · Status: Unresolved)*

The `bridgeBurn` function grants the `l2gateway` controller the ability to reduce the balance of any Animecoin holder. This means the `l2gateway` can effectively remove tokens from any address without their consent, posing a significant risk of censorship or asset seizure.

**Recommendation:** Token holders should be aware that the `l2gateway` address can directly burn tokens from their accounts. Investigate the governance and security measures surrounding the `l2gateway` to ensure it is controlled by trusted parties and robust security practices.


### `CP-01` — Centralized Token Minting Capability  *(Severity: Medium · Status: Unresolved)*

The `bridgeMint` function allows the `l2gateway` controller to create new Animecoin tokens at will. This means the total supply of Animecoin can be increased by a single entity, potentially diluting the value of tokens held by other users.

**Recommendation:** Token holders should be aware that the `l2gateway` address has the power to mint new tokens. It is critical to understand who controls this `l2gateway` address and what safeguards are in place to prevent arbitrary minting.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x7a98…4bc0 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.9% of supply. What remains: 70.8% in wallets, 11.1% in other contracts. 102,889 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Animecoin (ANIME), market cap $17M, rank #918. Traded on Binance. 102,889 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $68K (DexScreener, all pools). 24h trading volume $51.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $185K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.186 on 2025-01-23; the price is now 98.3062% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: mintable with no on-chain cap found. Control: l2gateway — a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $68K of DEX liquidity across 5 pools. Launch: 631 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x37a6...b4b3`](https://arbiscan.io/address/0x37a645648df29205c6261289983fb04ecd70b4b3) |
| **Network** | Arbitrum |
| **Price** | $0.003091 |
| **24h Volume** | $184.0K |
| **Liquidity** | $66.9K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 81.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1693 buys / 1716 sells |

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

- [View on DexScreener](https://dexscreener.com/arbitrum/0xbbf3209130df7d19356d72eb8a193e2d9ec5c234)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/animecoin-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
