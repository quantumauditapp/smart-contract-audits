---
token: Politburo or Parrot
ticker: POP
network: solana
risk_score: 24
status: low
date: 2026-10-23
---

# Politburo or Parrot (POP) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/politburo-or-parrot-sol)

---

## Audit Summary

The Politburo or Parrot (POP) token is an SPL Token-2022 asset with revoked mint and freeze authorities, ensuring supply immutability and preventing account freezing. However, the token exhibits high-risk trading patterns, including a volume-to-liquidity ratio indicative of wash trading and very low total liquidity. All third-party risk registry data is clear of adverse flags.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity and high volume-to-liquidity ratio, which suggest potential price manipulation or wash trading. Ensure all trades are executed with strict slippage controls to mitigate the impact of the thin order book.

Monitor the token's liquidity depth on-chain before entering or exiting large positions. Since the mint and freeze authorities are revoked, the token's supply and transfer mechanics are fixed, but market volatility remains a significant risk factor.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for the program. 7.3 Access Control is robust… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis reveals a volume-to-liquidity ratio of 133.39, significantly exceeding the 20x threshold for suspicious trading activity. 7.5 Governance is decentralized due to the lack of mint… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not support proxy-based logic updates. Metadata is immutable, and authority revocation is permanent. No further administrative changes can be… |

## Security Findings

_🟠 2 High · ⚪ 6 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,873. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure trades are sized appropriately for the available liquidity to avoid excessive price impact.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 133.39x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume relative to liquidity often indicates non-organic trading activity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.8% of supply. Of that, 65.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.5% in wallets, 0.0% in other contracts. 453 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

453 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FxwWTz...eSUo`](https://solscan.io/account/FxwWTze7qwWM8GMRcdyHWpocmCw8Th8QLRGETBJbeSUo) |
| **Network** | Solana |
| **Price** | $0.00001864 |
| **24h Volume** | $1.05M |
| **Liquidity** | $10.6K |
| **Volume / Liquidity** | 98.5× |
| **Token Age** | 15h |
| **Top-10 Holders** | 79.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11491 buys / 8694 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6u7uxf6lcn2sss4zmwypqfzmpskxr8upuhwjmxa9fnjv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/politburo-or-parrot-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
