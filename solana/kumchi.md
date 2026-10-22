---
token: kumchi
ticker: KUMCHI
network: solana
risk_score: 21
status: low
date: 2026-10-22
---

# kumchi (KUMCHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kumchi-sol)

---

## Audit Summary

The kumchi token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The primary risks identified are low liquidity and a high volume-to-liquidity ratio, which may indicate artificial trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise caution due to the low liquidity, which may cause significant slippage during trades. Monitor the token's trading volume on decentralized exchanges to ensure price stability before executing large orders.

Verify the current liquidity status on-chain to confirm that the LP tokens remain burned. Avoid relying on high volume metrics as a signal of organic demand, given the current volume-to-liquidity ratio.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program, ensuring compatibility with modern extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis reveals a liquidity depth of $7,437, which is below the $10,000 threshold. 7.6 External data shows a volume/liquidity ratio of 96.80, suggesting potential wash trading. 7.5… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint, as it is an immutable on-chain record. 7.8 Operations are secure due to the lack of mutable metadata and the inability to modify balances or… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,437. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation and avoid large market orders.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 96.80x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as trading volume may not reflect genuine market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $786K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 4 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Di3YBH...pump`](https://solscan.io/account/Di3YBHLp5hwnq2CrJBFRgcynWFwozKGRFT95coPnpump) |
| **Network** | Solana |
| **Price** | $0.0000203 |
| **24h Volume** | $705.0K |
| **Liquidity** | $10.9K |
| **Volume / Liquidity** | 65.0× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8621 buys / 6998 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/mufdywxykt7rmhfvbmfmybjaf1y5r4dz92zhpdat2bb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kumchi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
