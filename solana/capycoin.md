---
token: Capycoin
ticker: CAPY
network: solana
risk_score: 38
status: medium
date: 2026-10-22
---

# Capycoin (CAPY) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/capycoin-sol)

---

## Audit Summary

Capycoin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong baseline security for token supply and transferability. The primary risks identified are very low liquidity and a high volume-to-liquidity ratio, which suggests potential wash trading. Holder concentration data is unavailable, and third-party registry data shows no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the low liquidity, as large market orders will incur significant slippage. Monitor the asset for sustained organic volume to confirm that current trading patterns are not purely artificial.

Verify the token mint address directly on a block explorer to confirm the 'Revoked' status of authorities before interacting. Given the lack of holder distribution data, avoid large positions that could be impacted by sudden liquidity shifts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen account states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints, with no mutable balance or… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high risk due to low liquidity ($7,878) and a volume/liquidity ratio of 75.47, which exceeds the 20x threshold for wash-trading signals. 7.6 External… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades and 7.8 Operations are effectively locked for this asset. Metadata is immutable, and there are no upgradeable transfer hooks or fees. The token state is fixed, providing long-term… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $7,878. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 75.47x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity may not represent genuine market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $611K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 6 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`G9xrNb...pump`](https://solscan.io/account/G9xrNbBBYBsGFL2XiHdXDy56gWfAMnefD6L8ZKHLpump) |
| **Network** | Solana |
| **Price** | $0.00001461 |
| **24h Volume** | $572.6K |
| **Liquidity** | $9.0K |
| **Volume / Liquidity** | 63.6× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7909 buys / 5635 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/675q1iktqq4ijhbvsghvbc2crepcjrdueq3ydtiu8hyp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/capycoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
