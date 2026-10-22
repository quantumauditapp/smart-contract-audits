---
token: Saviour of the Internet
ticker: SURY
network: solana
risk_score: 20
status: low
date: 2026-10-22
---

# Saviour of the Internet (SURY) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saviour-of-the-internet-sol)

---

## Audit Summary

The Saviour of the Internet (SURY) SPL Token-2022 mint exhibits secure core authority settings, with both mint and freeze authorities permanently revoked and 100% of DEX pool liquidity burned. The primary security anomaly is a 24-hour trading volume of $3,120,125 against $33,661 in DEX liquidity, producing an elevated volume-to-liquidity ratio of 92.69 indicative of wash trading. Chain-native RPC holder distribution data was unavailable during this assessment.

> **Final Recommendation:** Examine automated transaction patterns on Solana DEX swaps to identify whether repetitive wallet clusters are generating non-organic volume before committing capital. Verify individual top token accounts directly on-chain using RPC getProgramAccounts or block explorers to evaluate whale concentration since third-party holder indexing was unavailable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the standard spl-token-2022 program with a fixed raw supply of 960,444,291,662,694 across 6 decimals. Both mint authority and freeze authority are verified as revoked… |
| **Governance / Economics** | 7/10 | Low | DEX liquidity is recorded at $33,661, with 100.0% of LP tokens burned, eliminating direct liquidity withdrawal risks by the creator. However, the volume-to-liquidity ratio reached 92.69 on pair day… |
| **Upgrades** | 10/10 | Low | Administrative upgrade vectors are entirely eliminated on this mint. Mint authority, freeze authority, and metadata mutability are all permanently revoked or set to false. No transfer fee or transfer… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 92.69x liquidity ($3,120,125 volume against $33,661 liquidity) — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Analyze trade counterparties for repetitive circular swap routes across coordinated addresses before relying on market metrics.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $3.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 6 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DYR8Kq...pump`](https://solscan.io/account/DYR8KqxtvkRHxcoFSMw62335Se3UfuE8GitP2iePpump) |
| **Network** | Solana |
| **Price** | $0.0001245 |
| **24h Volume** | $3.11M |
| **Liquidity** | $32.5K |
| **Volume / Liquidity** | 95.7× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20492 buys / 17188 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bseenmuc2fgldcgkg4b1uvfppccqxtgszjf9ox5vuce1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saviour-of-the-internet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
