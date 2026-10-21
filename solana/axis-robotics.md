---
token: Axis Robotics
ticker: AXIS
network: solana
risk_score: 29
status: low
date: 2026-10-21
---

# Axis Robotics (AXIS) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/axis-robotics-sol)

---

## Audit Summary

The Axis Robotics token (AXIS) has successfully revoked both mint and freeze authorities, mitigating risks of supply inflation and account freezing. However, the token suffers from extremely low liquidity and a lack of locked pool assets, with 100% of the liquidity held by a single, non-creator wallet. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the concentration of pool assets in a single, non-creator wallet. Verify the current liquidity pool status on-chain before attempting any trades to ensure the pool has not been drained.

Monitor the wallet address 'AzqKbg…nHB4' for any movement of liquidity, as this entity currently controls the entirety of the token's market depth. Avoid large orders to prevent excessive slippage given the current low-volume environment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL-Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high risk due to liquidity fragmentation. 100% of liquidity is held by a single wallet (AzqKbg…nHB4) and is not locked, allowing for immediate… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. The metadata is immutable, and no transfer hooks or fee-upgradable extensions are present. The token state is fixed and cannot be… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked. 100% of the liquidity is held by a single wallet (AzqKbg…nHB4), which can withdraw these funds at any time.

**Recommendation:** The liquidity provider should lock or burn the LP tokens to ensure market stability for holders.


### `M-01` — Very Low Liquidity  *(Severity: Medium · Status: Unresolved)*

The token exhibits extremely low liquidity and minimal 24-hour trading volume, making it difficult to execute trades without significant price impact.

**Recommendation:** Monitor liquidity levels on-chain before interacting with the token.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $365K (DexScreener, all pools). 24h trading volume $28.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $365K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8wATzN...Bb8W`](https://solscan.io/account/8wATzNsH7MmdReZ6T7Z6KfHP8PtZH1NpQFv55jzsBb8W) |
| **Network** | Solana |
| **Price** | $0.00001391 |
| **24h Volume** | $28.49M |
| **Liquidity** | $364.6K |
| **Volume / Liquidity** | 78.1× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14527 buys / 13084 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/e8hvvjkb1r3zcycfctp7zmuw3fcmbd59ci7rmwlxqrwv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/axis-robotics-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
