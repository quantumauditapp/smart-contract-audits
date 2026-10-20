---
token: Baby Super Inu
ticker: BSI
network: solana
risk_score: 0
status: low
date: 2026-10-01
---

# Baby Super Inu (BSI) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baby-super-inu-sol)

---

## Audit Summary

This SPL Token Mint for Baby Super Inu (BSI) has critical risks due to being flagged as high-risk by an independent third-party registry, citing a creator history of rugged tokens. While core mint authorities are revoked and liquidity is locked, the external risk signal is paramount. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Given the critical flag from a third-party risk registry, it is strongly recommended to avoid any interaction with this token. While the on-chain technical and economic parameters appear sound (authorities revoked, liquidity locked), the external signal of a creator history of rugged tokens overrides these positive aspects. Do not purchase or hold this token. Monitor the third-party risk registry for any changes in its assessment, but proceed with extreme caution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL Token-2022 mint with a total supply of 918,253,530,503,225 units and 6 decimals. Both the Mint Authority and Freeze Authority have been revoked, preventing further token creation… |
| **Governance / Economics** | 10/10 | Low | The token exhibits a healthy liquidity profile with $141,983 in total DEX liquidity, and 100.0% of the pool's LP tokens are burned, ensuring liquidity cannot be withdrawn. The 24-hour volume of… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, meaning no further changes to supply or account freeze status can be made. The token's metadata is immutable, preventing post-launch changes… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset, specifically citing a creator history of rugged tokens. This external signal indicates a significant risk of malicious intent or rug pull, despite the token's on-chain parameters appearing secure. (Fact: Third-party risk registry signals: Creator history of rugged tokens, Low Liquidity)

**Recommendation:** Do not interact with this token. The presence of a high-risk flag from a reputable third-party registry is a strong indicator of potential fraud or significant loss.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $142K (DexScreener, all pools). 24h trading volume $346K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $142K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`mXrsF4...pump`](https://solscan.io/account/mXrsF4j1M4SoLvUzq9MiPN2xpGE21kDR2bTSdZipump) |
| **Network** | Solana |
| **Price** | $0.0002772 |
| **24h Volume** | $202.6K |
| **Liquidity** | $142.4K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 16h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9917 buys / 2587 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/aqcfvbnb8b3hbtxdz6sm7fppswpwrm25rfldf1zetpke)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/baby-super-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
