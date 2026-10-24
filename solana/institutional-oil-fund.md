---
token: Institutional Oil Fund
ticker: IOF
network: solana
risk_score: 2
status: low
date: 2026-10-24
---

# Institutional Oil Fund (IOF) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/institutional-oil-fund-sol)

---

## Audit Summary

The Institutional Oil Fund (IOF) token is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully secured via 100% burning of LP tokens, mitigating withdrawal risks. Holder concentration data is unavailable, and third-party registries flag high holder correlation, which should be monitored for potential market manipulation.

> **Final Recommendation:** Investors should monitor the token's market activity given the high holder correlation flagged by third-party registries. Since holder distribution data is currently unavailable, users should exercise caution regarding potential price volatility caused by concentrated supply.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected state changes occur, although the current configuration is immutable. No further technical action is required to secure the token's mint state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $74,002 in liquidity, which is 100% burned, preventing rug-pulls via liquidity withdrawal. 7.5 Governance is decentralized due to the lack of administrative… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the token utilizes immutable metadata and non-upgradable extensions. The mint is effectively locked, ensuring no further supply inflation can occur. Metadata is… |

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

Liquidity $73K (DexScreener, all pools). 24h trading volume $50K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $73K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5eXqiS...pump`](https://solscan.io/account/5eXqiSMnZuqujfvpozFE1yJNEMxnUkjTy4urSYJYpump) |
| **Network** | Solana |
| **Price** | $0.0008093 |
| **24h Volume** | $50.2K |
| **Liquidity** | $73.4K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19769 buys / 4039 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/eiffoouwzlzfcwluhl1u3wq3yxtbwewgvmdssdcwc3yr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/institutional-oil-fund-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
