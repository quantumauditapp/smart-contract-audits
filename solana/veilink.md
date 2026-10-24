---
token: Veilink
ticker: VELK
network: solana
risk_score: 2
status: low
date: 2026-10-24
---

# Veilink (VELK) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/veilink-sol)

---

## Audit Summary

Veilink (VELK) is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong baseline security for token supply and transferability. The primary risk identified is a high volume-to-liquidity ratio suggesting potential wash trading, alongside the unavailability of holder concentration data. All liquidity is permanently locked, mitigating risks of rug-pulls via liquidity withdrawal.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial trading activity rather than organic demand. Monitor the asset for significant price volatility given the limited liquidity depth.

Verify the current holder distribution using block explorers to ensure supply is not overly concentrated among a few wallets. As the mint and freeze authorities are revoked, the token's core mechanics are secure from administrative interference.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with all critical authorities (mint and freeze) successfully revoked. 7.1 Architecture and 7.2 Code Security are standard for SPL-2022 assets. 7.3 Access… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic analysis indicates $15,594 in liquidity, which is fully burned, ensuring 7.5 Governance and liquidity safety. However, the 24h volume-to-liquidity ratio of 35.47 exceeds the 20x… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL mint as it is an immutable on-chain record. Metadata is immutable, and no upgradeable extensions are configured. The token configuration is finalized and… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 35.47, which exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading patterns for signs of manipulation and verify organic volume sources.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $264K (DexScreener, all pools). 24h trading volume $534K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $264K of DEX liquidity across 8 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BzoYWZ...pump`](https://solscan.io/account/BzoYWZL3fXC5KkzkA6dEh9pBKcv9NAqwkTxJReNxpump) |
| **Network** | Solana |
| **Price** | $0.001042 |
| **24h Volume** | $534.2K |
| **Liquidity** | $263.8K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8832 buys / 6347 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/74ukppdnqmnbou91h9fncprggtfdkvgojd9n6sdcqx1f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/veilink-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
