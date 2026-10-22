---
token: Pullback
ticker: PULLBACK
network: solana
risk_score: 21
status: low
date: 2026-10-22
---

# Pullback (PULLBACK) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pullback-sol)

---

## Audit Summary

The Pullback (PULLBACK) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the chain-native RPC.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high activity is organic or artificial. Given the lack of holder concentration data, users should exercise caution regarding potential whale activity that may not be visible in current market metrics.

Verify the current supply and authority status directly on-chain using a block explorer to confirm that no new tokens can be minted and no freeze actions can be initiated.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, ensuring compatibility with modern SPL extensions. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are set… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is supported by 100% of pool liquidity being burned, preventing rug-pulls via liquidity withdrawal. However, 7.8 Operations show a volume/liquidity ratio of 59.31, which… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints; however, the token metadata is immutable, preventing future branding changes. 7.3 Access Control is finalized through the revocation of all… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 59.31, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive patterns.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $44K (DexScreener, all pools). 24h trading volume $3.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $44K of DEX liquidity across 19 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`96AsCW...pump`](https://solscan.io/account/96AsCWA8TjVcZDqVfMMPT2J3BfMYjYhyyMdYLjg3pump) |
| **Network** | Solana |
| **Price** | $0.0001891 |
| **24h Volume** | $2.18M |
| **Liquidity** | $39.6K |
| **Volume / Liquidity** | 55.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17646 buys / 13052 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c1mvc74o3cdzeuvxsosxhc262crlwgrckidkh8av2xgm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pullback-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
