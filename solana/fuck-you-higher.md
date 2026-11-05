---
token: fuck you higher
ticker: HIGHER
network: solana
risk_score: 20
status: low
date: 2026-11-05
---

# fuck you higher (HIGHER) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fuck-you-higher-sol)

---

## Audit Summary

The token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. Liquidity is fully burned, preventing rug-pulls via liquidity withdrawal. Holder concentration data is unavailable, and the high volume-to-liquidity ratio suggests potential wash trading activity.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high activity is organic or artificial. Given the lack of holder distribution data, users should exercise caution regarding potential whale activity.

Verify the current mint and freeze authority status using a block explorer to confirm they remain null. Monitor the liquidity pool for any unusual activity despite the current burned status.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully burned (100%), eliminating withdrawal risk for the creator (7.4 Economic). The pair is 1 day old with a volume-to-liquidity ratio of 26.82, which exceeds the threshold for… |
| **Upgrades** | 10/10 | Low | The mint is immutable with no upgrade paths for authorities or metadata (7.7 Upgrades). All authority flags are set to null, providing a stable operational environment (7.8 Operations). |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 26.82, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting market activity and volume metrics for this asset.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $28K of DEX liquidity across 3 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6Kphvj...qPrJ`](https://solscan.io/account/6KphvjhrxCUyQAtcAYg4HDoSwsj4qfn1uP2KDEg8qPrJ) |
| **Network** | Solana |
| **Price** | $0.0001016 |
| **24h Volume** | $1.03M |
| **Liquidity** | $27.9K |
| **Volume / Liquidity** | 36.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8029 buys / 6429 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8vbd5ui7ri55v6nviedifozpjattcvsnobffwsxluidz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fuck-you-higher-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
