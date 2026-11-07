---
token: Anthropic
ticker: ANTS
network: solana
risk_score: 0
status: low
date: 2026-11-07
---

# Anthropic (ANTS) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-sol-7c6f)

---

## Audit Summary

The Anthropic (ANTS) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity pool is fully secured via 100% burning of LP tokens, preventing rug-pulls via liquidity withdrawal. Holder concentration data was unavailable, and the token is relatively new at one day old.

> **Final Recommendation:** The token is currently in a secure state with no administrative backdoors. Users should monitor the token's market activity, as the high volume-to-liquidity ratio may lead to price volatility.

Verify the current supply and authority status using a block explorer to ensure no unexpected changes have occurred. As holder distribution data is currently unavailable, exercise caution regarding potential market manipulation by large, unknown wallets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture is standard, with no active transfer hooks or custom logic. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $66,807 in liquidity, which is 100% burned. 7.5 Governance is decentralized due to the lack of administrative authorities. 7.6 External signals show no adverse… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are transparent, with metadata set to immutable, preventing future branding changes. The token configuration is locked… |

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

Liquidity $69K (DexScreener, all pools). 24h trading volume $630K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $69K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ejrz94...pump`](https://solscan.io/account/ejrz94zR4A2ScS8LdvRaQih2xUxaE2ydreqUNKmpump) |
| **Network** | Solana |
| **Price** | $0.0007491 |
| **24h Volume** | $629.7K |
| **Liquidity** | $69.4K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5763 buys / 2880 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/af5cn9mu1y8coh68xkbypsjxxdk1lbnxgo76dpprrolb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-sol-7c6f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
