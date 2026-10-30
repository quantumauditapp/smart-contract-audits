---
token: The Black Swan
ticker: SWAN
network: solana
risk_score: 23
status: low
date: 2026-10-30
---

# The Black Swan (SWAN) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-black-swan-sol)

---

## Audit Summary

The Black Swan (SWAN) is a Token-2022 asset with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Monitor the token's market activity closely, as the high volume-to-liquidity ratio indicates artificial trading patterns that may lead to extreme price volatility. 

Verify the current supply and holder distribution using a block explorer to ensure the lack of concentration data does not mask whale activity before committing capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture is standard for SPL mints. 7.2 Code Security is inherent to the… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show 100% of liquidity is burned, preventing rug pulls via withdrawal. 7.5 Governance is decentralized due to revoked authorities. However, 7.6 External market data indicates a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are secure since metadata is immutable and balance mutability is disabled. No further changes can be made to the token's core… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 63.25, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when relying on volume metrics for liquidity assessment.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 27 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EFaQg2...pump`](https://solscan.io/account/EFaQg27P3c3PHob2mFw4mHCUcWBHHDdatAEsXq2xpump) |
| **Network** | Solana |
| **Price** | $0.00004416 |
| **24h Volume** | $972.5K |
| **Liquidity** | $16.7K |
| **Volume / Liquidity** | 58.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15807 buys / 11176 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8bxfqf7dhsgjgaw7tfjjq1lc4bevjbk5ivnbfb4xsqaj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-black-swan-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
