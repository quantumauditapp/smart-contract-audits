---
token: playboicarti
ticker: CARTI
network: solana
risk_score: 20
status: low
date: 2026-10-26
---

# playboicarti (CARTI) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/playboicarti-sol)

---

## Audit Summary

The playboicarti (carti) token is a Token-2022 asset with revoked mint and freeze authorities, providing a secure foundation regarding supply control. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading, and holder concentration data is currently unavailable. Third-party risk registry data indicates no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the high trading volume relative to the $10,689 liquidity pool, as this often indicates artificial market activity. Monitor the token on-chain to verify that no new extensions are added if the program allows, though current settings are immutable.

Verify the current holder distribution using a block explorer to ensure that supply is not concentrated in a small number of wallets, as this data was unavailable at the time of this audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or frozen account states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints, as the mint and freeze authorities… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics are impacted by a volume/liquidity ratio of 381.45, which significantly exceeds the 20x threshold for wash-trading signals. While 100% of pool liquidity is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are stable as the token metadata is immutable and no upgradeable extensions are present. The mint address is fixed, and the absence of mutable balance or metadata… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume of $4,077,248 relative to $10,689 in liquidity results in a ratio of 381.45, which is significantly higher than the 20x threshold for suspicious trading patterns.

**Recommendation:** Exercise extreme caution; high volume-to-liquidity ratios are often indicative of wash trading or automated bot activity designed to inflate perceived interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $4.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 28 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H5UCZU...pump`](https://solscan.io/account/H5UCZUqCsuTQijwNLBX2KjwP7XJaMaESBSDzQytypump) |
| **Network** | Solana |
| **Price** | $0.00001728 |
| **24h Volume** | $4.07M |
| **Liquidity** | $10.9K |
| **Volume / Liquidity** | 371.9× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 38173 buys / 30188 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/camw24obwusgd7gvdjuh9prmeaqwcfyg1fq6rjtfgzss)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/playboicarti-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
