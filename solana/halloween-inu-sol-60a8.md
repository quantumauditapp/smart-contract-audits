---
token: Halloween Inu
ticker: INUWEEN
network: solana
risk_score: 37
status: medium
date: 2026-10-27
---

# Halloween Inu (INUWEEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/halloween-inu-sol-60a8)

---

## Audit Summary

The Halloween Inu token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. However, the token is flagged as high-risk by a third-party registry due to the creator's history of deploying rugged tokens. Liquidity is extremely low, and the project exhibits signs of potential wash trading.

> **Final Recommendation:** Investors should exercise extreme caution due to the third-party registry's high-risk classification regarding the creator's history. Before interacting, verify the current liquidity depth on-chain to ensure it meets personal risk tolerance for slippage.

Monitor the token's trading volume relative to liquidity; if the volume/liquidity ratio continues to climb, it may indicate unsustainable or manipulated market conditions. Do not rely on the token's branding, as the project's history is the primary security concern.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is initialized on the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics indicate significant risk. Liquidity is $4,997, which is below the $10,000 threshold for stable trading. While 100% of LP tokens are burned, the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades and 7.8 Operations are secure as metadata is immutable and no upgradeable extensions are present. The token configuration is fixed, preventing future changes to branding or transfer… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history.

**Recommendation:** Do not interact with this token.


### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $4,997. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 9.53x liquidity, a pattern associated with artificially inflated trade volume.

**Recommendation:** Monitor trading patterns for signs of manipulation.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $134K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.9% of supply. Of that, 33.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.1% in wallets, 0.0% in other contracts. 363 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

363 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7fjDm6...pump`](https://solscan.io/account/7fjDm6ZTCLX7PuPH5cPdyfYUVyNa5huYcwuaDcEEpump) |
| **Network** | Solana |
| **Price** | $0.00001535 |
| **24h Volume** | $42.0K |
| **Liquidity** | $8.7K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | 56.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 802 buys / 499 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5as6lwbwzh8guyghinoaaxfshjrmx6mcrgqtitpgmdul)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/halloween-inu-sol-60a8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
