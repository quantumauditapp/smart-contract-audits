---
token: Memento
ticker: MEMENTO
network: solana
risk_score: 41
status: medium
date: 2026-10-21
---

# Memento (MEMENTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/memento-sol)

---

## Audit Summary

The Memento token is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. While liquidity is fully burned, the token exhibits moderate holder concentration and high trading activity relative to its liquidity pool. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs, as they control over 50% of the circulating supply. Given the high volume-to-liquidity ratio, users should execute trades in smaller increments to minimize slippage impact on the $21,890 liquidity pool.

Verify the current holder distribution periodically via block explorers to ensure no single entity accumulates a dominant position. No further on-chain administrative actions are required as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or mutable balance… |
| **Governance / Economics** | 7/10 | Low | The top 10 holders control 53.18% of the supply (7.4 Economic). Liquidity is $21,890 and is 100% burned, ensuring it cannot be withdrawn (7.6 External). The volume-to-liquidity ratio of 11.60… |
| **Upgrades** | 8/10 | Low | The mint is immutable as the mint authority is revoked (7.7 Upgrades). Metadata and extension configurations are locked, preventing post-launch modifications (7.8 Operations). No upgrade paths exist… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell control 53.18% of the total supply. This level of concentration increases the risk of price volatility if these holders coordinate a sell-off.

**Recommendation:** Monitor the top 10 holder wallets for significant movements and maintain awareness of potential market impact from large individual positions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.8% of supply. Of that, 46.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 53.2% in wallets, 0.0% in other contracts. 15 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

15 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $260K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (meme); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7yZp5z...pump`](https://solscan.io/account/7yZp5zBBHsEiieKnjiMjk9iZF1gyeg1VZpSYaPf1pump) |
| **Network** | Solana |
| **Price** | $0.00007483 |
| **24h Volume** | $254.0K |
| **Liquidity** | $21.9K |
| **Volume / Liquidity** | 11.6× |
| **Token Age** | 4d |
| **Top-10 Holders** | 99.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23331 buys / 9569 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/brwglnkqsmxjyv9tzeckuyaug6m5nvwprtwemwseifny)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/memento-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
