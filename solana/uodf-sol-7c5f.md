---
token: UODF
ticker: UODF
network: solana
risk_score: 9
status: low
date: 2026-11-07
---

# UODF (UODF) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/uodf-sol-7c5f)

---

## Audit Summary

The UODF token is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully burned, preventing rug-pulls via liquidity withdrawal. Holder distribution data is unavailable, and third-party registries indicate high holder correlation, which may suggest concentrated ownership.

> **Final Recommendation:** Investors should monitor the token's price action and volume, as the high holder correlation flagged by third-party registries may lead to significant volatility. Since holder distribution data is currently unavailable, users should exercise caution regarding potential whale activity.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain null. No further administrative actions are required for this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are revoked.… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, ensuring the pool cannot be drained by the creator. 7.5 Governance is decentralized due to authority revocation. 7.6 External signals… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not use proxy patterns. Metadata is immutable, preventing branding changes. The token configuration is finalized and cannot be altered by any… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

Third-party risk registries have flagged the token for high holder correlation, suggesting that a significant portion of the supply may be held by a small number of related entities.

**Recommendation:** Monitor on-chain wallet movements for signs of coordinated selling or dumping.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $297K (DexScreener, all pools). 24h trading volume $3.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $297K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BvqKMJ...pump`](https://solscan.io/account/BvqKMJ4bwnDaSxQrDE9hsfz8397kNF1u2mRppNtipump) |
| **Network** | Solana |
| **Price** | $0.01403 |
| **24h Volume** | $3.89M |
| **Liquidity** | $296.7K |
| **Volume / Liquidity** | 13.1× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 34382 buys / 13885 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gsedqkyavucby6n3gexdvew7fnu4orfsbnva2dsjd78c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/uodf-sol-7c5f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
