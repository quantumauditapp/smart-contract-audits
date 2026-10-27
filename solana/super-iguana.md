---
token: Super Iguana
ticker: SI
network: solana
risk_score: 17
status: low
date: 2026-10-27
---

# Super Iguana (SI) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-iguana-sol)

---

## Audit Summary

The Super Iguana token is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading, and holder concentration data is currently unavailable. Third-party registry data indicates no adverse flags.

> **Final Recommendation:** Investors should monitor the token's trading activity closely, as the high volume-to-liquidity ratio may indicate artificial market manipulation. Given the lack of holder distribution data, users should exercise caution regarding potential whale activity.

Verify the current supply and authority status directly via a block explorer to confirm that no changes have occurred since this audit. Prior to trading, ensure that the liquidity pool remains stable and that the volume metrics align with organic market participation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or default… |
| **Governance / Economics** | 8/10 | Low | Liquidity is fully secured with 100% of LP tokens burned, preventing creator withdrawal (7.4 Economic). The 24-hour volume-to-liquidity ratio of 23.94 exceeds the 20x threshold, indicating potential… |
| **Upgrades** | 10/10 | Low | The mint authority is revoked, preventing further supply inflation (7.7 Upgrades). Metadata is immutable, ensuring branding consistency (7.2 Code Security). No upgrade paths exist for the token… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 23.94, which exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when trading; monitor for organic volume growth and verify market depth before executing large orders.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $110K (DexScreener, all pools). 24h trading volume $2.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $110K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3yM6w9...pump`](https://solscan.io/account/3yM6w93HMUZSHrMSGVPR2cW4Wvubvkscht1541i6pump) |
| **Network** | Solana |
| **Price** | $0.001502 |
| **24h Volume** | $2.26M |
| **Liquidity** | $109.7K |
| **Volume / Liquidity** | 20.6× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 70255 buys / 25497 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3kgvpft91e1e3yedmodfn1gwcldsmerfdfhlgha65lcj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-iguana-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
