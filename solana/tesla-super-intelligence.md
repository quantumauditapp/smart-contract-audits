---
token: Tesla Super Intelligence
ticker: TESLA SI
network: solana
risk_score: 1
status: low
date: 2026-10-25
---

# Tesla Super Intelligence (TESLA SI) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tesla-super-intelligence-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. The primary risks identified are extremely low liquidity and a high volume-to-liquidity ratio, which are indicative of wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity, which makes the asset highly susceptible to slippage and price manipulation. Monitor the asset's volume-to-liquidity ratio on block explorers to determine if trading activity remains artificially inflated.

Verify the current supply and authority status directly on-chain using a block explorer to confirm that the mint and freeze authorities remain null. Avoid large market orders that could trigger significant price impact given the current liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.6 External factors are concerning due to $1,859 in liquidity. The volume/liquidity ratio of 131.54 suggests significant wash trading activity. 7.5 Governance is stable as 100% of… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are secure as metadata is immutable and no upgradeable extensions are active. The mint is permanently fixed, preventing future supply inflation. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $1,859. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure position sizes are small relative to the total liquidity pool to avoid excessive slippage.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 131.54x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume relative to liquidity often indicates non-organic market activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $123K (DexScreener, all pools). 24h trading volume $163K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $123K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FfXPKW...pump`](https://solscan.io/account/FfXPKWFFjx6RUFvFrUbJT8CXgWQkxcC8hsyVLashpump) |
| **Network** | Solana |
| **Price** | $0.002154 |
| **24h Volume** | $163.1K |
| **Liquidity** | $122.5K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 33177 buys / 30754 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/anslksvg7mhjkvuwlt5ltqwc3gbfrxfxdrxdgmg5qzga)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tesla-super-intelligence-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
