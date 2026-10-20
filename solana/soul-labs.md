---
token: Soul Labs
ticker: SO
network: solana
risk_score: 26
status: low
date: 2026-10-20
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol)

---

## Audit Summary

The Soul Labs token (SO) utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the token exhibits high economic risk due to a lack of locked liquidity and a volume-to-liquidity ratio indicative of wash trading. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity. Monitor the pool creator's wallet for any signs of liquidity removal, as the current 0% lock status allows for immediate withdrawal of all funds.

Verify the token's market activity independently, as the high volume-to-liquidity ratio suggests that reported trading volume may not reflect genuine organic demand. Avoid large positions that cannot be supported by the current $349,477 liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing is possible (7.3… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits significant economic risks with 0% of liquidity locked or burned (7.4 Economic). The volume-to-liquidity ratio of 127.21 suggests potential wash trading activity (7.6 External).… |
| **Upgrades** | 8/10 | Low | The token mint is immutable as the mint authority is revoked (7.7 Upgrades). Metadata is non-mutable, preventing branding changes post-launch (7.2 Code Security). No upgrade paths exist for the token… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the pool creator can withdraw all liquidity at any time.

**Recommendation:** The project team should lock the liquidity in a recognized time-locked smart contract to protect holders.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 127.21, which is significantly above the 20x threshold, indicating potential artificial volume inflation.

**Recommendation:** Perform due diligence on trading patterns and avoid relying on volume metrics as a proxy for organic interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $347K (DexScreener, all pools). 24h trading volume $44.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $347K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`72BHp9...tPmH`](https://solscan.io/account/72BHp9Ng7nPJz2jfBeK2BxBZzavbDH1ESPemLsWHtPmH) |
| **Network** | Solana |
| **Price** | $0.00001729 |
| **24h Volume** | $43.95M |
| **Liquidity** | $346.9K |
| **Volume / Liquidity** | 126.7× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21873 buys / 19741 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3yywddwezusav8xbxmpzvdmlbyzpt4bgqtnuwjv9kmae)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
