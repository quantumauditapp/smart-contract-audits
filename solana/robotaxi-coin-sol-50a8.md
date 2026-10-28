---
token: Robotaxi Coin
ticker: ROBOTAXI
network: solana
risk_score: 0
status: low
date: 2026-10-28
---

# Robotaxi Coin (ROBOTAXI) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-sol-50a8)

---

## Audit Summary

Robotaxi Coin is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully burned, ensuring the pool cannot be drained by the creator. The primary risk identified is a high holder correlation signal from third-party registries, though no specific malicious on-chain mechanisms were detected.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for coordinated movement, as the high holder correlation signal suggests potential concentration risks. No further on-chain action is required to secure the token itself, as authorities are correctly revoked and liquidity is permanently burned.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are robust due to the standard implementation… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing rug-pulls via withdrawal. 7.5 Governance is decentralized by the lack of mint authority, though 7.6 External signals indicate… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is fixed and non-mutable, ensuring branding consistency. No further authority-based changes can be applied to the token program… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries flag a high correlation between the top 10 token holders, which may indicate a single entity or coordinated group controlling a significant portion of the circulating supply.

**Recommendation:** Monitor the top 10 holder wallets for simultaneous sell-off patterns and exercise caution regarding potential price manipulation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.5% of supply. Of that, 3.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.8% in wallets, 0.0% in other contracts. 4,215 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,215 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $94K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $94K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`51gYnr...MKcq`](https://solscan.io/account/51gYnrYvbU5hbqvxovHoRbhnAZuLG7Xvsvfj9tj1MKcq) |
| **Network** | Solana |
| **Price** | $0.001286 |
| **24h Volume** | $38.8K |
| **Liquidity** | $93.8K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 8h |
| **Top-10 Holders** | 22.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19052 buys / 130 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/guj9ocb8vuzdeqab8qaui4crcyehhrhifsyhauxyrtps)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/robotaxi-coin-sol-50a8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
