---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 25
status: low
date: 2026-10-25
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-775b)

---

## Audit Summary

The AlloX token exhibits significant economic risks due to extreme wash-trading signals and the lack of locked liquidity. While the mint and freeze authorities are correctly revoked, the high volume-to-liquidity ratio and the absence of locked LP tokens suggest potential for market manipulation. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the pool for sudden liquidity withdrawals, as the current structure allows for the removal of all pool assets by the creator.

Verify the current liquidity status on-chain before executing any trades. Avoid large positions that exceed the available liquidity depth to prevent significant slippage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are revoked.… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic indicators show extreme volatility with a volume/liquidity ratio of 198.30, indicating potential wash trading. 7.5 Governance is limited as no holder concentration data is available. 7.6… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, ensuring branding consistency. No further upgrade paths exist for the token program logic. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 198.30, which significantly exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for high slippage.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the liquidity provider can withdraw all assets at any time.

**Recommendation:** Verify if the liquidity provider intends to lock the pool assets to ensure market stability.


### `M-01` — High Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

Third-party registry signals indicate a large amount of LP is unlocked and there is a low number of LP providers.

**Recommendation:** Exercise caution when providing liquidity or trading large amounts.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $292K (DexScreener, all pools). 24h trading volume $56.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $292K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ELLkkU...1qSZ`](https://solscan.io/account/ELLkkU9G15Jr3KdEfSV6FKQC8UVWqaAZLjFefdjP1qSZ) |
| **Network** | Solana |
| **Price** | $0.00001887 |
| **24h Volume** | $56.49M |
| **Liquidity** | $292.3K |
| **Volume / Liquidity** | 193.3× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27634 buys / 25019 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ja7os7eg9rueasya3md9dnsz9xrerlupx4xfxnn4sh4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-775b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
