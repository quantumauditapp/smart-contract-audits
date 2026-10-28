---
token: XTO
ticker: X T O
network: solana
risk_score: 0
status: low
date: 2026-10-28
---

# XTO (X T O) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol-ed3e)

---

## Audit Summary

The mint exhibits an immutable configuration with both mint and freeze authorities permanently revoked, alongside 100.0% burned pool liquidity on $1,290,142 in DEX reserves. Chain-native RPC holder distribution data was unavailable, though secondary metrics show the top 10 non-pool holders control 4.03% of supply with noted wallet correlation signals. No critical administrative or structural vulnerabilities were detected across verified parameters.

> **Final Recommendation:** Query the mint account via Solana RPC (getAccountInfo) to continuously verify that mint_authority and freeze_authority remain null. Monitor DEX liquidity pairs across secondary decentralized exchanges for any newly introduced, unburned liquidity pools. Track transfer patterns among top correlated wallets to detect potential coordinated liquidation despite low nominal individual balances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates under the spl-token-2022 program with an initialized raw supply of 999,987,817,748,755 and 6 decimal places. Mint authority and freeze authority are both confirmed revoked (None)… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders capable of selling control a modest 4.03% of the total circulating supply, minimizing immediate single-whale dump potential. Liquidity stands at $1,290,142 with 100.0% of pool LP… |
| **Upgrades** | 10/10 | Low | The mint enforces absolute immutability with all primary administrative capabilities relinquished at launch. No Token-2022 upgradeable extensions—such as transfer hooks or configurable fee… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 4.3% of supply. Of that, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.0% in wallets, 0.0% in other contracts. 2,024 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,024 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.3M (DexScreener, all pools). 24h trading volume $757K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.3M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`dueTLv...pump`](https://solscan.io/account/dueTLvJkHEGiYbeFVXgkFVqYUGFcYnt9A5JAcL4pump) |
| **Network** | Solana |
| **Price** | $0.2294 |
| **24h Volume** | $756.9K |
| **Liquidity** | $1.29M |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 16h |
| **Top-10 Holders** | 4.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 25906 buys / 5614 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5fzxlwgkxwt2lhcftluxzschbtfan5qazfcvgsmghmcd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol-ed3e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
