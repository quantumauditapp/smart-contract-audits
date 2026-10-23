---
token: Luna Expeditions
ticker: LUNARS
network: solana
risk_score: 33
status: low
date: 2026-10-23
---

# Luna Expeditions (LUNARS) — Smart Contract Security Analysis | Solana

> **Risk Score: 33/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/luna-expeditions-sol)

---

## Audit Summary

The Luna Expeditions token (Lunars) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the token exhibits low liquidity, the pool liquidity is fully burned, preventing rug-pulls via liquidity withdrawal. Third-party registry data indicates no adverse flags.

> **Final Recommendation:** Investors should monitor the $9,286 liquidity depth before executing large trades to avoid significant price impact. No further administrative actions are required as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the spl-token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics show 24.97% concentration among the top 10 holders. 7.6 External liquidity is $9,286, which is below the $10,000 threshold, indicating potential slippage… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the immutable nature of the mint. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is final and cannot be… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,286. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation and avoid large market orders.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $200K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.0% of supply. Of that, 37.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 25.0% in wallets, 0.0% in other contracts. 123 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

123 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bju7nR...pump`](https://solscan.io/account/Bju7nRToGYP7BeBsKf9MDBZkhDGJmH3PkuH6KeeSpump) |
| **Network** | Solana |
| **Price** | $0.00001469 |
| **24h Volume** | $34.9K |
| **Liquidity** | $8.5K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 21h |
| **Top-10 Holders** | 62.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 447 buys / 442 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/2dlsva2xcnhaj3zyphmsf6aflanczftfkvmc9rnkkwul)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/luna-expeditions-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
