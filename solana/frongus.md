---
token: Frongus
ticker: FRONGUS
network: solana
risk_score: 13
status: low
date: 2026-10-27
---

# Frongus (FRONGUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/frongus-sol)

---

## Audit Summary

The Frongus token is a standard SPL-2022 mint with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is unavailable, and third-party registry data indicates no adverse flags.

> **Final Recommendation:** Investors should monitor the token's trading activity closely, as the high volume-to-liquidity ratio may indicate artificial market manipulation. Verify the current supply and holder distribution via a block explorer to assess the risk of whale-driven volatility.

Since the mint and freeze authorities are revoked, the token's core supply and transfer mechanics are immutable. No further on-chain actions are required to secure the token's configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis shows $82,294 in liquidity, which is 100% burned, ensuring the pool cannot be drained by the creator. However, 7.6 External market data reveals a volume/liquidity ratio of… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a fixed-supply asset. Metadata is immutable, and extension configurations are locked, preventing future changes to token behavior. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 67.87, significantly exceeding the 20x threshold, which is a strong indicator of wash trading.

**Recommendation:** Exercise caution when interpreting market volume; prioritize liquidity depth over reported trading volume.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 44% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $192K (DexScreener, all pools). 24h trading volume $6.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $192K of DEX liquidity across 29 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2BJDwU...pump`](https://solscan.io/account/2BJDwUdMbnJhRRfhacFDjrDNhxUWdzE9H6LEND89pump) |
| **Network** | Solana |
| **Price** | $0.0007416 |
| **24h Volume** | $5.18M |
| **Liquidity** | $83.7K |
| **Volume / Liquidity** | 62.0× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 51379 buys / 44077 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/deb7ybe2lhf242bxqwd4hbqxkgfaolswfwxpgehenseq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/frongus-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
