---
token: Soul Labs
ticker: SO
network: solana
risk_score: 25
status: low
date: 2026-10-25
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-e581)

---

## Audit Summary

The Soul Labs token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high economic risk due to extreme wash-trading signals and the lack of locked liquidity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high volume-to-liquidity ratio. Monitor the liquidity pool for sudden withdrawals, as the pool creator retains the ability to remove all funds.

Verify the current liquidity status on-chain before executing any trades. Avoid large positions that cannot be supported by the current $391,371 liquidity depth to minimize slippage impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume/liquidity ratio of 92.27, which is a strong indicator of wash trading (7.4 Economic). 100% of the pool liquidity remains unlocked, posing a significant risk to holders… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns inherent to this SPL mint (7.7 Upgrades). Operations… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — High Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 92.27, significantly exceeding the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for high slippage.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool liquidity is burned or locked, meaning the pool creator or current LP holders can withdraw all liquidity at any time.

**Recommendation:** Treat the liquidity pool as temporary and subject to removal by the creator.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $384K (DexScreener, all pools). 24h trading volume $33.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $384K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2yivbN...ZS6s`](https://solscan.io/account/2yivbN8oNm8ZdhY1BeYE85hmAzT7it5AMorArZrUZS6s) |
| **Network** | Solana |
| **Price** | $0.00001476 |
| **24h Volume** | $33.38M |
| **Liquidity** | $384.1K |
| **Volume / Liquidity** | 86.9× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16409 buys / 14751 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7bvftedfdrn7nrqzkhuh6kexmbda5zmnb5jyszqzsdyh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-e581)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
