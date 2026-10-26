---
token: NeuralAI
ticker: NEURAL
network: ethereum
risk_score: 72
status: high
date: 2026-09-13
---

# NeuralAI (NEURAL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/neuralai-eth)

---

## Audit Summary

The NeuralAI contract is a standard ERC-20 token with integrated trading restrictions, fee mechanisms, and liquidity management features. The contract relies heavily on centralized control via an owner and a treasury address, which possess significant power over token economics and transferability. While the code follows standard patterns for such tokens, the high degree of centralization presents a notable risk to token holders.

> **Final Recommendation:** It is recommended to transition the privileged roles to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single point of failure. Additionally, implementing a timelock on sensitive functions like fee updates or trading enablement would provide transparency and protection to token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows a standard ERC-20 implementation with added hooks for automated market maker (AMM) interactions. 7.1 Architecture is modular, utilizing OpenZeppelin's Ownable for access… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic parameters are entirely controlled by the owner and treasury address. 7.5 Governance is non-existent, as all changes are executed by privileged EOA addresses without community oversight.… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are limited to the functions provided in the source code. The lack of upgradeability ensures the logic remains immutable… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.6% |
| **Top-3 Unlocked** | ⚠️ 94.4% |
| **Lock Expiry** | Expired 540d ago |

## Security Findings

_🟡 4 Medium · 🟢 1 Low · ⚪ 3 Informational_

### `CP-05` — Centralized Control Over Trading Status  *(Severity: Medium · Status: Unresolved)*

The owner and treasury address have the authority to enable or disable trading, effectively freezing the token's utility. Functions like enableTrading and manualSwap allow these roles to halt or resume transfers at their discretion.

**Recommendation:** Implement a timelock mechanism for trading-related changes or renounce ownership if the protocol is intended to be fully decentralized.


### `CP-07` — Centralized Control Over Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The owner can modify buy and sell fees at any time using updateBuyFee and updateSellFee. This allows for potential economic manipulation of the token's liquidity and value.

**Recommendation:** Set a hard cap on the maximum possible fee that can be set by the owner to protect users from sudden, extreme fee increases.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a contract, 0xefe9…7445 — holds 63.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $6K (DexScreener, all pools). 24h trading volume $5K (CoinGecko, all markets, daily snapshot). 24h trading volume $3K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $17.29 on 2024-12-06; the price is now 95.9667% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CP-08` — Centralized Control Over Transaction Limits  *(Severity: Low · Status: Unresolved)*

Privileged addresses can change transaction and wallet limits (maxBuyAmount, maxSellAmount, maxWalletAmount) via dedicated setter functions. This allows the owner to restrict or permit specific wallet behaviors.

**Recommendation:** Consider making these limits immutable or subject to a community-governed voting process to increase trust.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.1% of supply. Of that, 58.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 2.1% in wallets, 5.1% in other contracts. 15,861 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NEURALAI (NEURAL), market cap $7M, rank #1422. 15,861 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: 4% on buy, 3.99% on sell. Market: $6K of DEX liquidity across 2 pools. Launch: 949 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x32b0...e6e1`](https://etherscan.io/address/0x32b053f2cba79f80ada5078cb6b305da92bde6e1) |
| **Network** | Ethereum |
| **Price** | $0.7723 |
| **24h Volume** | $2.2K |
| **Liquidity** | $5.8K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 66.1% of supply |
| **Buy / Sell Tax** | 4.0% / 4.0% |
| **24h Transactions** | 69 buys / 48 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x1112956589a2bea1b038732db4ea6b0c416ef130)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/neuralai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
