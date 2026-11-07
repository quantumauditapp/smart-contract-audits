---
token: Squirrelcoin
ticker: SQRL
network: solana
risk_score: 22
status: low
date: 2026-11-07
---

# Squirrelcoin (SQRL) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/squirrelcoin-sol)

---

## Audit Summary

Squirrelcoin (SQRL) is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong baseline security for token supply and transferability. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading, and holder concentration data is currently unavailable. Third-party risk registry data indicates no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial trading activity rather than organic market demand. Monitor the token's liquidity depth over time to ensure that slippage remains manageable for intended trade sizes.

Verify the current holder distribution via block explorers once data becomes available to ensure that supply is not overly concentrated among a few wallets. No further on-chain action is required regarding authority management as they are already permanently revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by the absence of… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is impacted by a volume/liquidity ratio of 168.28, which exceeds the 20x threshold for wash-trading signals. 7.6 External liquidity is fully secured, with 100% of LP tokens… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. Metadata is immutable, and no extension-based upgrade paths for fees or hooks are enabled. The token configuration is… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 168.28, significantly exceeding the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for potential liquidity gaps during high-volatility events.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 95% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 16 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AD2TBq...pump`](https://solscan.io/account/AD2TBq5fP6mmGFnciRbofH93PJwkpd2mYTFBY3eRpump) |
| **Network** | Solana |
| **Price** | $0.00002173 |
| **24h Volume** | $1.70M |
| **Liquidity** | $12.3K |
| **Volume / Liquidity** | 137.5× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16346 buys / 13657 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8iytxwgj3dad6ev9ptw5vtthixsjjrdheqcojtag6mdh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/squirrelcoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
