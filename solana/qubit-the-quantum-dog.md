---
token: Qubit The Quantum Dog
ticker: QUBIT
network: solana
risk_score: 38
status: medium
date: 2026-10-29
---

# Qubit The Quantum Dog (QUBIT) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/qubit-the-quantum-dog-sol)

---

## Audit Summary

The QUBIT token is a Token-2022 asset with fully revoked mint and freeze authorities, providing a secure foundation for supply and transfer integrity. However, the token exhibits high-risk economic indicators, specifically very low liquidity and a volume-to-liquidity ratio suggestive of wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity environment, which may prevent exiting positions without substantial price impact. Monitor the asset for organic volume growth before considering significant exposure.

Verify the current liquidity pool status periodically via block explorers to ensure the burned LP tokens remain inaccessible. Do not rely on high 24-hour volume metrics as a proxy for market depth, as the current ratio suggests artificial activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default frozen states… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is critically low at $8,265, posing significant slippage risks (7.4 Economic). The volume-to-liquidity ratio of 119.68 indicates potential wash trading (7.6 External). Positively, 100% of… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable extensions or transfer fees (7.8 Operations). The mint state is finalized and cannot… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,265. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 119.68x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; volume may not represent genuine market interest.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 12 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HDwZkN...pump`](https://solscan.io/account/HDwZkNNh8Bt9oPP51xrPwGyKxDUR2YorHiAHGuiypump) |
| **Network** | Solana |
| **Price** | $0.00001334 |
| **24h Volume** | $988.8K |
| **Liquidity** | $8.7K |
| **Volume / Liquidity** | 113.8× |
| **Token Age** | 16h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12780 buys / 9138 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/a2hsrrn5dc5nbbz4qv1zgkeqpjeo3eboz9kdypw3zf6t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/qubit-the-quantum-dog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
