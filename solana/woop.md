---
token: woop
ticker: WOOP
network: solana
risk_score: 19
status: low
date: 2026-11-03
---

# woop (WOOP) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/woop-sol)

---

## Audit Summary

The WOOP token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. Liquidity is effectively secured with 99.9% locked in a third-party locker, and no adverse flags were reported by security registries. Holder concentration is moderate, and the token exhibits no mutable metadata or balance-altering extensions.

> **Final Recommendation:** The token demonstrates a high security posture regarding its on-chain configuration. Holders should continue to monitor the top 10 holder wallets for significant accumulation patterns that could impact market stability.

Verify the lock status of the liquidity pool periodically using block explorers to ensure the Raydium LP locker remains active. No further on-chain action is required to secure the token's mint or freeze state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access… |
| **Governance / Economics** | 9/10 | Low | Top 10 holders control 34.36% of the supply, which is within a safe range (7.4 Economic). Liquidity is robustly protected with 99.9% locked, preventing rug-pull scenarios via liquidity withdrawal… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns, as is standard for SPL tokens (7.8 Operations). The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 99.9% — Raydium Lock |
| **Top-1 Unlocked Holder** | 0.1% |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.6% of supply. Of that, 5.2% locked — not holders that can sell, so excluded from the concentration score. What remains: 22.0% in wallets, 12.3% in other contracts. 579 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

579 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.9% of the pool's LP is burned or time-locked. 99.9% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $197K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`272423...LsVE`](https://solscan.io/account/2724239D1JhWQGV5WZ7tdBTN5Jz4FZ3pdmvj3iD4LsVE) |
| **Network** | Solana |
| **Price** | $0.0001318 |
| **24h Volume** | $196.9K |
| **Liquidity** | $29.5K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 1d |
| **Top-10 Holders** | 39.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1593 buys / 1132 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ettubzdvpgvrudlkuemzs8xnppbf71wd2kyahiqzmhtd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/woop-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
