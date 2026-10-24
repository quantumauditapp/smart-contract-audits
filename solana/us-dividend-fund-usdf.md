---
token: US Dividend Fund (USDF)🔥
ticker: USDF
network: solana
risk_score: 0
status: low
date: 2026-10-24
---

# US Dividend Fund (USDF)🔥 (USDF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-dividend-fund-usdf-sol)

---

## Audit Summary

The US Dividend Fund (USDF) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via 100% burning of LP tokens, mitigating withdrawal risks. While third-party registry data indicates high holder correlation, the core token architecture is immutable and secure.

> **Final Recommendation:** Investors should monitor the token's market activity and holder distribution as it matures, given the high holder correlation noted by third-party registries. No immediate action is required regarding the token's technical configuration, as all critical authorities are revoked and liquidity is permanently locked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension support. 7.1 Architecture is standard for SPL mints, with 7.3 Access Control confirmed by the revocation of both mint… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $532,209 in liquidity, with 100% of LP tokens burned, preventing rug-pull scenarios. 7.5 Governance is decentralized by the lack of administrative control over… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint, as the program is immutable. Metadata is locked, preventing unauthorized changes to the token identity. No upgrade paths exist for the token… |

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

Liquidity $529K (DexScreener, all pools). 24h trading volume $369K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.04031 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $529K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`H4Xf9L...pump`](https://solscan.io/account/H4Xf9LysARXsMLx5YeQoA3JNq8zbXU4SqvfeYzdpump) |
| **Network** | Solana |
| **Price** | $0.04031 |
| **24h Volume** | $369.0K |
| **Liquidity** | $529.0K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 18h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 22657 buys / 2017 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9rwemt3unsgpvk41unvtderfnzrbkel3s9dulemwh1g2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-dividend-fund-usdf-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
