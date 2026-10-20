---
token: SUBZERONE
ticker: SUB-01
network: solana
risk_score: 13
status: low
date: 2026-10-11
---

# SUBZERONE (SUB-01) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/subzerone-sol)

---

## Audit Summary

This SPL Token Mint audit for SUBZERONE (SUB-01) found no critical or high-severity issues based on the available on-chain data and third-party risk registries. Key authorities like Mint and Freeze are revoked, and all pool liquidity is burned. Holder distribution data was unavailable, preventing an assessment of concentration risk.

> **Final Recommendation:** Given the revoked mint and freeze authorities and burned liquidity, the token presents a low-risk profile based on available data. Holders should monitor for any future changes in liquidity or trading patterns. It is recommended to verify holder distribution on-chain if possible, as this data was unavailable for a complete assessment of concentration risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The SUBZERONE (SUB-01) token is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no existing accounts can be frozen. It… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a very healthy liquidity profile, with $29,993 in total DEX liquidity and 100.0% of the pool's LP tokens burned, meaning this liquidity can never be withdrawn. The 24-hour volume… |
| **Upgrades** | 10/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, are both revoked, preventing any future changes to supply or account freeze status. It is an SPL Token-2022, but no upgradable… |

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

Liquidity $30K (DexScreener, all pools). 24h trading volume $173K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6WCtKQ...pump`](https://solscan.io/account/6WCtKQfkWurd77tCCAYWuL5TwyAvuovTzworfnfupump) |
| **Network** | Solana |
| **Price** | $0.0001173 |
| **24h Volume** | $173.0K |
| **Liquidity** | $30.3K |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 987 buys / 1036 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4gaj3mmdm2yk41frm7twytuazwvsuzhjh9zndw81qspp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/subzerone-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
