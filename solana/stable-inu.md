---
token: Stable Inu
ticker: SI
network: solana
risk_score: 24
status: low
date: 2026-10-29
---

# Stable Inu (SI) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stable-inu-sol)

---

## Audit Summary

Stable Inu is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against supply inflation and account freezing. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate artificial market activity rather than organic demand. Verify the current market depth before executing large trades to avoid excessive slippage.

Since holder concentration data is unavailable, perform a manual check of the top token accounts on a block explorer to ensure supply is not heavily centralized among a few wallets before committing capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as both mint and freeze authorities are… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $30,433 in liquidity, which is fully burned, preventing rug pulls via liquidity withdrawal. 7.5 Governance is decentralized due to authority revocation. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints. 7.8 Operations are stable as metadata is immutable and no balance-mutating authorities exist. The token configuration is fixed. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 28.30, exceeding the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics and account for potential liquidity gaps during high volatility.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $29K (DexScreener, all pools). 24h trading volume $939K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $8.728e-05 — it does not hold a peg. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $29K of DEX liquidity across 19 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6zuDiA...pump`](https://solscan.io/account/6zuDiAw3NviBwcLZfTztHJgtCmeNWfyFxYVoXtNYpump) |
| **Network** | Solana |
| **Price** | $0.00008728 |
| **24h Volume** | $726.1K |
| **Liquidity** | $28.9K |
| **Volume / Liquidity** | 25.2× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8092 buys / 5677 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5dvbpfhebf9hbcsdcsoaczermycdzmi4x7dxksuprhnl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stable-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
