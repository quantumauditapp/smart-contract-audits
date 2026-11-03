---
token: Grand Theft America
ticker: GTA
network: solana
risk_score: 15
status: low
date: 2026-11-03
---

# Grand Theft America (GTA) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-theft-america-sol)

---

## Audit Summary

The Grand Theft America (GTA) token is a Token-2022 asset with fully revoked mint and freeze authorities. However, the project is flagged as high-risk by a third-party registry due to the creator's history of previous rug-pulls. Liquidity is currently low and fully burned, but the developer's reputation remains a significant concern for potential investors.

> **Final Recommendation:** Investors should exercise extreme caution due to the third-party registry flag regarding the creator's history. While the on-chain authorities are revoked and liquidity is burned, these technical safeguards do not mitigate the risk of social engineering or project abandonment by the developer.

Verify the mint address directly on a block explorer to ensure it matches the address provided. Monitor the token's liquidity and volume on DEX platforms to ensure slippage remains within acceptable limits for your position size.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic analysis shows $9,781 in liquidity, which is below the $10,000 threshold for low-slippage trading. 7.5 Governance is decentralized due to revoked authorities, though 7.6 External signals… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not support proxy-based logic changes. 7.8 Operations are fixed; metadata is immutable, and balance mutability is disabled. The token configuration is… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history involving previous rug-pulls.

**Recommendation:** Do not interact with this token.


### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,781, which is below the $10,000 threshold. Slippage will be severe for large trades.

**Recommendation:** Account for high slippage in any swap calculation and avoid large positions.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $198K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`G6F6SY...pump`](https://solscan.io/account/G6F6SYSUAUxsnKLyeRW29hE5A4BGCbw91x7HMPySpump) |
| **Network** | Solana |
| **Price** | $0.00002139 |
| **24h Volume** | $48.5K |
| **Liquidity** | $10.2K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1094 buys / 634 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/yu4uk83r3sctmnnzqgqoperr2ajeny6jiwpnq1sewvt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-theft-america-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
