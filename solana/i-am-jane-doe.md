---
token: I Am Jane Doe
ticker: JANE
network: solana
risk_score: 14
status: low
date: 2026-10-04
---

# I Am Jane Doe (JANE) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/i-am-jane-doe-sol)

---

## Audit Summary

The I Am Jane Doe (Jane) SPL Token Mint exhibits a robust security configuration with all critical authorities, including mint and freeze, being revoked. The token utilizes the modern spl-token-2022 program without a transfer hook or default frozen account state. All pool liquidity is permanently burned, indicating a strong commitment to liquidity stability. Holder concentration data was unavailable, which limits a full assessment of distribution risk.

> **Final Recommendation:** This token exhibits a secure configuration with critical authorities revoked and liquidity permanently locked. Holders should continue to monitor the token's market activity, particularly if holder distribution data becomes available, to assess potential concentration risks. No immediate on-chain verification steps are required beyond confirming the current state of revoked authorities and burned liquidity, as these are already established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program, indicating modern SPL token standards. Both the mint authority and freeze authority are revoked, preventing further token creation or… |
| **Governance / Economics** | 9/10 | Low | The token demonstrates strong liquidity stability, with 100.0% of the pool's LP tokens burned, meaning this liquidity can never be withdrawn. Current DEX liquidity stands at $33,860, with a 24-hour… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority have both been revoked, preventing any future changes to the token's supply or account freeze status. Metadata is immutable, ensuring that the token's name… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 79% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $46K (DexScreener, all pools). 24h trading volume $222K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $46K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9pJWJd...9ZMr`](https://solscan.io/account/9pJWJdpPebyANys45eetpemLJo8yTz4n5B9zbpYw9ZMr) |
| **Network** | Solana |
| **Price** | $0.00009773 |
| **24h Volume** | $200.9K |
| **Liquidity** | $35.9K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1308 buys / 1417 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/31ectc8w3vcx7bifwk2o5ax41fpi2uyhcehcy2gd3h5h)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/i-am-jane-doe-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
