---
token: United States Power Reserve
ticker: USPR
network: solana
risk_score: 2
status: low
date: 2026-11-05
---

# United States Power Reserve (USPR) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-power-reserve-sol-e73d)

---

## Audit Summary

The United States Power Reserve (USPR) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating rug-pull risks associated with creator withdrawals. Holder concentration data is unavailable, and third-party registries indicate high holder correlation, which warrants caution regarding potential market manipulation.

> **Final Recommendation:** Investors should monitor the token's market activity given the high holder correlation flagged by third-party registries. Since holder distribution data is currently unavailable, users should exercise caution regarding potential price volatility caused by concentrated ownership.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected changes occur. Given the lack of transparency in holder distribution, avoid large market orders that could be impacted by slippage from concentrated sell-side pressure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize… |
| **Governance / Economics** | 10/10 | Low | Liquidity is healthy at $290,600 with a stable volume/liquidity ratio of 0.63 (7.4 Economic). 100% of pool liquidity is burned, ensuring permanent availability (7.6 External). Holder concentration… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding metadata and authority settings (7.7 Upgrades). Metadata is non-mutable, preventing branding changes post-launch. No upgrade paths exist for transfer fees or hooks… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

Third-party risk registries have flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small number of entities.

**Recommendation:** Monitor on-chain wallet movements for signs of coordinated sell-offs and maintain a cautious position size.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $294K (DexScreener, all pools). 24h trading volume $182K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $294K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Twf1V6...pump`](https://solscan.io/account/Twf1V6kBQj9YRYwYfTjSZxoMVgg61s2jv27xBYipump) |
| **Network** | Solana |
| **Price** | $0.01356 |
| **24h Volume** | $181.9K |
| **Liquidity** | $293.8K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21516 buys / 2647 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7aahjzgv9eexzd5hmtfeorhxnhhnmkh45zqpc52y6y9r)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-power-reserve-sol-e73d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
