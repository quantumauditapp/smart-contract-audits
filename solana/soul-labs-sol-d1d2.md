---
token: Soul Labs
ticker: SO
network: solana
risk_score: 29
status: low
date: 2026-10-24
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-d1d2)

---

## Audit Summary

The Soul Labs token exhibits significant economic risks due to extreme wash-trading signals and the lack of locked liquidity. While the mint and freeze authorities are correctly revoked, the high volume-to-liquidity ratio and the fact that 100% of pool liquidity remains withdrawable present a high risk of rug-pull. Holder distribution data was unavailable from the source.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the pool's liquidity levels on-chain to detect sudden withdrawals.

Verify the current liquidity provider's wallet activity before interacting with the pool. Avoid large positions as the high volume-to-liquidity ratio indicates that the reported market depth may not support significant sell orders without extreme price impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are robust as both Mint and Freeze authorities are revoked. 7.2 Code Security is standard for the SPL… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high volatility. The volume/liquidity ratio of 136.46 suggests significant wash-trading. 7.6 External signals confirm that 100% of pool liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. 7.8 Operations are stable, with metadata and balance mutability disabled, ensuring the token configuration remains immutable. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 136.46, which significantly exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Account for potential liquidity manipulation when evaluating the token's market health.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked; the entire liquidity pool is withdrawable by anonymous holders.

**Recommendation:** Treat the pool as removable until liquidity is provably burned or locked in a time-locked contract.


### `M-01` — High-Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags the token for a large amount of unlocked LP and a low number of LP providers.

**Recommendation:** Perform independent due diligence on the liquidity provider's history.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $373K (DexScreener, all pools). 24h trading volume $49.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $373K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B68DmS...D2pY`](https://solscan.io/account/B68DmS6KsYcNpEifba6mptE8rgSV5s6Uuaeo3piND2pY) |
| **Network** | Solana |
| **Price** | $0.00001865 |
| **24h Volume** | $49.53M |
| **Liquidity** | $373.3K |
| **Volume / Liquidity** | 132.7× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24583 buys / 22174 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/j6sx2a6hgt8s3pb7zd4bmpdmwdqeabibndtfozbq55ku)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-d1d2)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
