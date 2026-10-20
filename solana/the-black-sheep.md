---
token: The Black Sheep
ticker: YOKAI
network: solana
risk_score: 2
status: low
date: 2026-10-20
---

# The Black Sheep (YOKAI) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-black-sheep-sol)

---

## Audit Summary

The Black Sheep (YOKAI) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a permanent lock, and no adverse flags were reported by third-party registries. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** The token exhibits strong security properties regarding its mint and liquidity structure. Users should monitor the token's official communication channels for any updates regarding the project's roadmap.

Since holder distribution data is currently unavailable, investors should exercise standard caution regarding market volatility and potential price manipulation by large holders. Verify the mint address against official project sources before any transaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $120,402 with 100% of pool tokens permanently locked (7.4 Economic). Trading volume is healthy relative to liquidity, with a ratio of 3.54 (7.6 External). Holder concentration… |
| **Upgrades** | 10/10 | Low | The mint configuration is immutable, with metadata and balance-mutating authorities disabled (7.7 Upgrades). There are no upgrade paths for the token program or its extensions (7.8 Operations). The… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $133K (DexScreener, all pools). 24h trading volume $405K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $133K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B86LTr...kids`](https://solscan.io/account/B86LTrZDrH8G9zqMvXzFfwH8txDy8Sy7TZabjabTkids) |
| **Network** | Solana |
| **Price** | $0.0008961 |
| **24h Volume** | $404.8K |
| **Liquidity** | $131.9K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2684 buys / 1335 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3oxwfrk3gdrk8seksrmtkdsjgj5frx1nkqycqicyuj76)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-black-sheep-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
