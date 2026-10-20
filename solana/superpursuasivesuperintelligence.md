---
token: SuperPursuasiveSuperIntelligence
ticker: SPSI
network: solana
risk_score: 15
status: low
date: 2026-10-19
---

# SuperPursuasiveSuperIntelligence (SPSI) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superpursuasivesuperintelligence-sol)

---

## Audit Summary

The SuperPursuasiveSuperIntelligence (SPSI) token mint exhibits strong security configurations with both mint and freeze authorities revoked, and immutable metadata. However, DEX market data indicates a high volume/liquidity ratio of 25.11, suggesting potential wash trading. Holder distribution and third-party risk registry data were unavailable for this assessment.

> **Final Recommendation:** Given the strong wash trading signal, users should exercise extreme caution and verify trading activity independently. Monitor the token's liquidity and volume patterns over time to confirm genuine market interest and organic trading. While core mint authorities are revoked, the lack of holder distribution data means concentration risk cannot be assessed; consider this a blind spot and proceed with awareness of this unknown.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority are revoked, meaning no new tokens can be minted and no accounts can be frozen. There is no… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $11,773. The 24-hour trading volume is $295,597, resulting in a Volume/Liquidity Ratio of 25.11. This ratio is significantly above 20, which is a strong… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority have both been revoked, preventing any future changes to the token's supply or the ability to freeze holder accounts. The token's metadata is immutable… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume is 25.11x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the possibility of artificial volume when evaluating market interest and liquidity. Verify trading activity independently.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $293K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BVpFpk...pump`](https://solscan.io/account/BVpFpksfdEwDgaUhZxdG8kSyfAekeYfKV4BdUfNJpump) |
| **Network** | Solana |
| **Price** | $0.0000822 |
| **24h Volume** | $186.9K |
| **Liquidity** | $23.3K |
| **Volume / Liquidity** | 8.0× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2056 buys / 1811 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2p3ngpodd5genag6mmoxjsmmkct2tz5d9mwu2djjeube)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superpursuasivesuperintelligence-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
