---
token: Chunkee The Manatee
ticker: CHUNKEE
network: solana
risk_score: 20
status: low
date: 2026-10-23
---

# Chunkee The Manatee (CHUNKEE) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chunkee-the-manatee-sol)

---

## Audit Summary

The CHUNKEE token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the registry.

> **Final Recommendation:** Investors should exercise caution due to the extremely low liquidity and high volume-to-liquidity ratio, which may lead to significant slippage and difficulty in exiting positions. Monitor the token on-chain to ensure no unexpected changes to the token program state occur.

Verify the current liquidity pool depth before executing any trades. Given the lack of holder distribution data, avoid large market orders that could be impacted by low depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is built on the SPL Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). No… |
| **Governance / Economics** | 9/10 | Low | Liquidity is $2,039, which is fully burned and inaccessible to the creator (7.4 Economic). However, the 24h volume of $357,054 results in a volume/liquidity ratio of 175.08, which is a strong signal… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgradeable extensions are present (7.7 Upgrades). The mint configuration is finalized (7.8 Operations). |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 175.08, significantly exceeding the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for high slippage when trading.


### `H-02` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,039, which is insufficient for large transactions without causing extreme price impact.

**Recommendation:** Only trade in small sizes commensurate with the available liquidity depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $340K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7rN6DL...pump`](https://solscan.io/account/7rN6DLfo2bo8T5JFzy9P7iSNvUiqydwVXsqVNub6pump) |
| **Network** | Solana |
| **Price** | $0.0001417 |
| **24h Volume** | $335.7K |
| **Liquidity** | $31.0K |
| **Volume / Liquidity** | 10.8× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4818 buys / 2020 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/34fnblukuhylsdhprtgmk6zyoqajvgbhuj6vmloquwpi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chunkee-the-manatee-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
