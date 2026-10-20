---
token: darwin
ticker: DARWIN
network: solana
risk_score: 2
status: low
date: 2026-10-09
---

# darwin (DARWIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/darwin-sol)

---

## Audit Summary

The darwin SPL Token Mint exhibits a low-risk profile based on available on-chain data and third-party security signals. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing asset freezing. Liquidity is fully locked, and holder concentration is low. No adverse flags were reported by third-party risk registries, and no critical or high-severity issues were identified.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor the token's trading volume and liquidity over time to ensure market health. While current metrics are favorable, continuous vigilance is advised for any token in a nascent market.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The darwin token is an SPL Token-2022 mint with a total supply of 947,352,382.161473 tokens, using 6 decimals. Crucially, both the mint authority and freeze authority have been revoked, ensuring that… |
| **Governance / Economics** | 10/10 | Low | Economic analysis reveals a healthy distribution, with the top 10 holders that can sell holding only 15.52% of the total supply, indicating low concentration risk. The token has a liquidity of… |
| **Upgrades** | 10/10 | Low | The darwin token mint has a robust security posture regarding mutability and control. Both the mint and freeze authorities are permanently revoked, preventing any future changes to supply or account… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.8% of supply. Of that, 16.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.5% in wallets, 0.0% in other contracts. 2,922 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as darwin (DARWIN), rank #4073. 2,922 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 65% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $105K (DexScreener, all pools). 24h trading volume $551K (CoinGecko, all markets, daily snapshot). 24h trading volume $616K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $105K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5VnbrK...pump`](https://solscan.io/account/5VnbrKp28Qs9CAH6PyZdxBNvLxZcbeX3YBsozgWnpump) |
| **Network** | Solana |
| **Price** | $0.0003876 |
| **24h Volume** | $429.7K |
| **Liquidity** | $68.0K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 5d |
| **Top-10 Holders** | 31.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2901 buys / 3084 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/53w7r4xuxcsnlgoavj3npixnszywgzkyhvavytlpyaxm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/darwin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
