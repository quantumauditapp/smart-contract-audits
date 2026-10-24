---
token: trump wif sword
ticker: SWORDTRUMP
network: solana
risk_score: 16
status: low
date: 2026-10-24
---

# trump wif sword (SWORDTRUMP) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trump-wif-sword-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. However, the asset exhibits extreme trading volatility with a volume-to-liquidity ratio indicating potential wash trading and very low total liquidity. Holder distribution data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity and high volume-to-liquidity ratio, which are indicative of high-risk trading environments. Before interacting, verify the current liquidity depth on a decentralized exchange to ensure order execution is viable.

Monitor the token's market activity for sustained liquidity growth. Since holder concentration data is unavailable, avoid large positions that could be subject to significant price impact or liquidity exhaustion.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.6 External factors present significant risks. Liquidity is extremely low at $2,306, leading to severe slippage. The volume-to-liquidity ratio of 887.17 is highly suspicious and… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. Metadata is immutable, and no balance-mutating authorities are present. The configuration is locked, providing high assurance… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,306. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation and avoid large trade sizes.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 887.17x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as the reported volume may not represent genuine market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $2.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (wif); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`1hy4Vv...pump`](https://solscan.io/account/1hy4VvRmw6iFkZwBAgpkuRTQn6KokLbqxjDGBSxpump) |
| **Network** | Solana |
| **Price** | $0.0004567 |
| **24h Volume** | $1.96M |
| **Liquidity** | $58.8K |
| **Volume / Liquidity** | 33.3× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 47685 buys / 26372 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gdjbanjsbnhrhce2g2zwma5etuxank5yvbs6ospgcnwb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trump-wif-sword-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
