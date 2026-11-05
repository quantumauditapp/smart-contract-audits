---
token: Call
ticker: CALL
network: solana
risk_score: 21
status: low
date: 2026-11-05
---

# Call (CALL) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/call-sol)

---

## Audit Summary

The Call (CALL) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's trading activity on DEX platforms to verify if the high volume is organic or artificial. Given the lack of holder distribution data, avoid large market orders that could be impacted by low liquidity slippage.

Verify the current mint and freeze authority status using a block explorer to ensure they remain null. Do not rely on the token for long-term value storage until organic trading volume is established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics show 100% of pool liquidity is burned, preventing rug-pulls via liquidity withdrawal. However, 7.6 External market data indicates a volume/liquidity ratio of… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are restricted by the revocation of all authorities. Metadata is immutable, and no upgrade paths exist for transfer hooks or fees. The token state is fixed and cannot… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 62.00, which exceeds the 20 threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive, small-value circular transactions.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7Uooap...pump`](https://solscan.io/account/7UooapEDmXmP5hRJPoYvXqYDWMVh15Gi59gYu7hopump) |
| **Network** | Solana |
| **Price** | $0.00003384 |
| **24h Volume** | $1.25M |
| **Liquidity** | $14.8K |
| **Volume / Liquidity** | 84.3× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16573 buys / 12470 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/77hsvm1d3fu4mpodcvl4cwxg7kgmrvyjrnxfnoe9cybx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/call-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
