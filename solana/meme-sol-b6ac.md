---
token: Meme
ticker: MEME
network: solana
risk_score: 36
status: medium
date: 2026-10-21
---

# Meme (MEME) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meme-sol-b6ac)

---

## Audit Summary

The MEME token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits high-risk trading patterns and low liquidity, which may impede exit strategies. Holder concentration data is unavailable.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity and high volume-to-liquidity ratio, which suggest significant price volatility and potential difficulty in executing large trades. Monitor the token's market activity on DEX platforms before committing capital.

Verify the current supply and authority status using a block explorer to ensure no unexpected changes have occurred. Given the lack of holder distribution data, avoid large positions that could be impacted by sudden market shifts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture is standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic stability is compromised by low liquidity of $6,035 and a high volume/liquidity ratio of 100.54, indicating potential wash trading. 7.6 External market data confirms the liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to SPL token mints. Metadata is immutable, and the token program extensions are configured to prevent future changes to transfer hooks or fees. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $6,035. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 100.54x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as the trading volume may not reflect genuine market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $638K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (meme); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 7 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`65ruvk...pump`](https://solscan.io/account/65ruvkKxdqmR2aaohdLykPQ9GmYQkjrVcWhX8Lcrpump) |
| **Network** | Solana |
| **Price** | $0.00001444 |
| **24h Volume** | $576.7K |
| **Liquidity** | $9.0K |
| **Volume / Liquidity** | 64.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7511 buys / 5950 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7x23c9sgje3sn229gmpsxpgctsgfsxuhjhvhgg42o4ic)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meme-sol-b6ac)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
