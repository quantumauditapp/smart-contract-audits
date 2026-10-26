---
token: SpaceX
ticker: SPACEX
network: solana
risk_score: 1
status: low
date: 2026-10-26
---

# SpaceX (SPACEX) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-sol-788e)

---

## Audit Summary

The SpaceX token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls by the creator. Holder concentration data is unavailable, and the token is flagged as a copycat by a third-party registry.

> **Final Recommendation:** Investors should verify the token mint address against official sources to ensure it is not a copycat asset. Monitor the token's liquidity on-chain to confirm the burn status remains intact.

Users should exercise caution due to the lack of holder distribution data. Before trading, confirm the token's identity on block explorers to avoid potential impersonation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture is standard for SPL mints. 7.2 Code Security is inherent to the audited Solana program. 7.3 Access Control is robust as both… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic factors show $31,389 in liquidity, which is fully burned, ensuring 7.5 Governance cannot withdraw pool funds. 7.6 External signals indicate the token is a copycat, though trading volume… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not support proxy-based logic updates. Metadata is immutable, and extension configurations such as transfer fees or hooks are not upgradable. The token… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — Copycat Token Risk  *(Severity: Low · Status: Unresolved)*

The token is flagged by a third-party risk registry as a copycat, indicating it may be attempting to impersonate a different, established project.

**Recommendation:** Verify the token's identity and official website before interacting.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $127K (DexScreener, all pools). 24h trading volume $109K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $127K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`J5mvME...pump`](https://solscan.io/account/J5mvMEGyQpeVSXGGkXUAETjE2FPQaTM8Mb2H8tgApump) |
| **Network** | Solana |
| **Price** | $0.0001284 |
| **24h Volume** | $100.2K |
| **Liquidity** | $127.5K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 23h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11946 buys / 13438 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/atj47idj42abkzmzgkpjqza2g11mfoequrqhbwsfeajg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-sol-788e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
