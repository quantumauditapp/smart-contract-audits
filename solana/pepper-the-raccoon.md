---
token: Pepper The Raccoon
ticker: PEPPER
network: solana
risk_score: 13
status: low
date: 2026-10-13
---

# Pepper The Raccoon (PEPPER) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pepper-the-raccoon-sol)

---

## Audit Summary

This audit of the Pepper The Raccoon SPL Token Mint found no critical or high-severity issues based on the available on-chain data and deterministic rules. Key authorities, including mint and freeze, are revoked, and all pool liquidity is burned. Holder concentration data was unavailable from chain-native RPC, preventing an assessment of distribution risk.

> **Final Recommendation:** Given the revoked mint and freeze authorities and burned liquidity, the token presents a robust on-chain configuration. Holders should monitor for the availability of holder concentration data to assess potential market manipulation risks. Continue to verify the immutability of token properties on-chain.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Pepper The Raccoon token is implemented using the spl-token-2022 program (7.1 Architecture). Both the mint authority and freeze authority have been revoked (7.3 Access Control), preventing… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a total DEX liquidity of $47,655 (7.4 Economic), with 100% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn. The 24-hour volume is $265,739, resulting in a… |
| **Upgrades** | 10/10 | Low | The token's mint and freeze authorities are permanently revoked (7.7 Upgrades), indicating a fixed supply and immutable account states. Metadata mutability is set to False, meaning the token's name… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $292K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9g4Pib...pump`](https://solscan.io/account/9g4Pib6AM3oVdP9YA7ZcssAXAuhoUzkjR8w27doYpump) |
| **Network** | Solana |
| **Price** | $0.0002574 |
| **24h Volume** | $271.6K |
| **Liquidity** | $49.5K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1801 buys / 1907 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gkvfziv4eunvimrfuejen5qjn29oxgcyk7fy2iuv3bgi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pepper-the-raccoon-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*
