---
token: SAFU
ticker: SAFU
network: bsc
risk_score: 2
status: low
date: 2026-10-30
---

# SAFU (SAFU) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/safu-bsc)

---

## Audit Summary

The Token contract is a standard ERC-20 implementation with an additional transfer control mechanism. Ownership has been permanently renounced, ensuring that the privileged functions, including the transfer mode switch, are now inaccessible. The architecture is robust and follows standard practices, with no active administrative risks identified.

> **Final Recommendation:** The contract is secure and immutable due to the renounced ownership. No further action is required for the current implementation as the administrative functions are permanently disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a standard OpenZeppelin-based ERC-20 implementation, ensuring high compatibility with DeFi ecosystems. 7.1 Architecture is clean, and 7.2 Code Security is maintained through the… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance risks are mitigated by the renounced ownership, preventing any future changes to tokenomics or transfer rules. The contract operates as a trustless asset. 7.8… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a non-proxy, immutable contract. The code cannot be modified post-deployment, providing high assurance of long-term logic stability. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 6 Informational_

### `CP-05` — Dormant Transfer Control Switch  *(Severity: Informational · Status: Unresolved)*

The contract contains a 'setMode' function that previously allowed the owner to toggle transfer restrictions. Because ownership has been renounced, this function is now permanently inaccessible, rendering the switch immutable.

**Recommendation:** No action is required, as the renouncement of ownership has effectively secured the contract against unauthorized changes to the transfer logic.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 41.1% of supply. Of that, 22.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.4% in wallets, 1.7% in other contracts. 2,584 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SAFU (SAFU), rank #7732. 2,584 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $53K (DexScreener, all pools). 24h trading volume $19K (CoinGecko, all markets, daily snapshot). 24h trading volume $85K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00317 on 2024-12-04; the price is now 98.5131% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $53K of DEX liquidity across 1 pools. Launch: 695 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3433...2b0c`](https://bscscan.com/address/0x3433a5748bda2f7338bdc600be7bc716d5882b0c) |
| **Network** | BNB Chain |
| **Price** | $0.0001208 |
| **24h Volume** | $85.2K |
| **Liquidity** | $53.5K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 41.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 509 buys / 237 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x8dc5b82398decace63d15788314ab80f81d00529)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/safu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
