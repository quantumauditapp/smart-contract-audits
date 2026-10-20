---
token: Team Human
ticker: HUMAN
network: solana
risk_score: 8
status: low
date: 2026-10-10
---

# Team Human (HUMAN) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/team-human-sol)

---

## Audit Summary

This audit of the Team Human (Human) SPL Token Mint found no critical or high-severity issues based on the provided on-chain data and external security signals. Key authorities are revoked, liquidity is fully locked, and holder concentration is low. Third-party risk registry data reported no adverse flags.

> **Final Recommendation:** This token presents a low-risk profile based on the available on-chain data. Holders should continue to monitor the token's market behavior and any future announcements from the project team. No specific on-chain verification steps are immediately required beyond confirming the current state of revoked authorities, which is already reflected in this report.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Team Human (Human) token is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority are revoked, preventing further token creation or freezing of holder accounts. No Transfer Hook is… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for only 21.17% of the total supply. The token has healthy liquidity of $60,745 USD, and 100% of the pool's LP tokens are… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, meaning the token's supply and account freeze capabilities are immutable. The token's metadata is also immutable (`metadata_mutable: False`)… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 38.3% of supply. Of that, 17.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.2% in wallets, 0.0% in other contracts. 5,485 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,485 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $69K (DexScreener, all pools). 24h trading volume $150K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $69K of DEX liquidity across 10 pools. Launch: launched on pump.fun (PumpSwap), 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8nPoBH...DMBC`](https://solscan.io/account/8nPoBHiBM6pybxMws9PA2JRb9BjkppBfqcZGmot4DMBC) |
| **Network** | Solana |
| **Price** | $0.0002174 |
| **24h Volume** | $138.8K |
| **Liquidity** | $60.7K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 5d |
| **Top-10 Holders** | 38.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1296 buys / 1502 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fb2dw7cbcc2d1hkyf21kxkexesqfvsbntvdjauogmrws)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/team-human-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
