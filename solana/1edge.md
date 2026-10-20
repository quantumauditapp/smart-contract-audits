---
token: 1EDGE
ticker: 1EDGE
network: solana
risk_score: 29
status: low
date: 2026-10-20
---

# 1EDGE (1EDGE) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/1edge-sol)

---

## Audit Summary

The 1EDGE token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The project exhibits healthy liquidity management with 99.8% of pool liquidity locked. No adverse flags were reported by third-party registries, and the token configuration is immutable.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for significant sell-side activity, as the current concentration of 64.32% could lead to price slippage. No further action is required regarding authority management as the mint is fully renounced.

Verify the current holder distribution periodically using block explorers to ensure that concentration levels do not increase significantly. The token is technically sound and follows best practices for immutable SPL tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture is standard, and 7.2 Code Security is inherent to the audited SPL program. 7.3… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show a concentration of 64.32% among the top 10 holders, which warrants monitoring for potential volatility. 7.5 Governance is decentralized due to the revocation of minting… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata and balance-mutating authorities are disabled, preventing post-launch changes to token identity or user balances. The token… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 64.32% of the total supply. Coordinated sell-offs by these entities could result in significant price impact.

**Recommendation:** Monitor large wallet movements and diversify holdings to mitigate exposure to individual whale activity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 64.3% of supply. What remains: 16.0% in wallets, 48.3% in other contracts. 530 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as 1EDGE (1EDGE), rank #5643. 530 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 0.2% is held, unlocked, by 1 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $53K (CoinGecko, all markets, daily snapshot). 24h trading volume $119K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 2 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`1EwcGE...EDGE`](https://solscan.io/account/1EwcGE6WrssiY2sKSadB5E5DE9WhPDQvBC6kev1EDGE) |
| **Network** | Solana |
| **Price** | $0.0001648 |
| **24h Volume** | $118.8K |
| **Liquidity** | $31.7K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 5d |
| **Top-10 Holders** | 64.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 839 buys / 559 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8sacr5tmpmufk8kcggbxhz517yqg1m2xj2jca7bzpcut)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/1edge-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
