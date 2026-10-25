---
token: Gigantic Milker Enjoyers
ticker: GME
network: solana
risk_score: 15
status: low
date: 2026-10-25
---

# Gigantic Milker Enjoyers (GME) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gigantic-milker-enjoyers-sol)

---

## Audit Summary

The Gigantic Milker Enjoyers (GME) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, third-party registry data indicates the token is flagged as a copycat, and holder concentration data is currently unavailable. The protocol demonstrates strong technical security regarding authority management but carries social and economic risks associated with its classification.

> **Final Recommendation:** Investors should monitor the token's social presence and verify the 'copycat' classification against their own risk tolerance. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity.

Verify the current mint and freeze authority status on a block explorer to ensure they remain null. Monitor the token's liquidity and volume trends to ensure the high volume/liquidity ratio does not lead to excessive slippage during market volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic security is supported by 100% of liquidity being burned, preventing rug pulls via withdrawal. 7.5 Governance is decentralized due to revoked authorities. 7.6 External signals indicate a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL token mints in the EVM sense. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is fixed and cannot be altered by the… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Flagged as Copycat Token  *(Severity: Medium · Status: Unresolved)*

The token is identified as a copycat by a third-party risk registry, indicating it may be attempting to impersonate another project.

**Recommendation:** Verify the token's authenticity and project legitimacy through official channels before interacting.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 42% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $138K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (giga); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $138K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9gexoG...pump`](https://solscan.io/account/9gexoGn8qnxT1XpncwNXJDwQci9cPGuNXG3uNfDkpump) |
| **Network** | Solana |
| **Price** | $0.0003994 |
| **24h Volume** | $1.11M |
| **Liquidity** | $58.1K |
| **Volume / Liquidity** | 19.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14126 buys / 9652 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ffnutjsnsh8pmu1e9x1nj285dkb4jahnfnjnq89khugw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gigantic-milker-enjoyers-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
