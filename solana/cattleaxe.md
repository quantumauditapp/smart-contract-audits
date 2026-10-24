---
token: Cattleaxe
ticker: CATTLEAXE
network: solana
risk_score: 15
status: low
date: 2026-10-24
---

# Cattleaxe (CATTLEAXE) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cattleaxe-sol)

---

## Audit Summary

The Cattleaxe token (SPL Token-2022) demonstrates strong security posture regarding authority control, with both mint and freeze authorities successfully revoked. The primary risk identified is a high volume-to-liquidity ratio, suggesting potential wash trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading volume relative to liquidity to ensure market activity is organic. Given the high volume-to-liquidity ratio, exercise caution regarding potential price volatility.

Verify the current supply and authority status periodically using a block explorer to confirm that no unexpected changes have occurred, although the current revocation status is definitive.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with all critical authorities (Mint and Freeze) revoked, ensuring supply immutability and preventing account freezing. 7.1 Architecture and 7.2 Code Security… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance metrics indicate a high volume-to-liquidity ratio of 25.30, which exceeds the 20x threshold for wash-trading signals. 7.6 External liquidity is fully secured, with… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL token mints as they lack proxy patterns. Metadata is immutable, and no upgradeable extensions are configured, ensuring the token's current state is permanent. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 25.30, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading patterns for signs of inorganic volume before executing large orders.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $71K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $71K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H7VZNC...pump`](https://solscan.io/account/H7VZNCBynDK5ikBS9krDJ2Tx8CUr1wxedV19ZgkWpump) |
| **Network** | Solana |
| **Price** | $0.0006602 |
| **24h Volume** | $1.53M |
| **Liquidity** | $70.6K |
| **Volume / Liquidity** | 21.6× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23972 buys / 9877 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3p3uya9ayzv7w2nhejeo8ankuuwhyuonqvhhs8lyrqjy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cattleaxe-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
