---
token: Altai the Tiger
ticker: ALTAI
network: solana
risk_score: 10
status: low
date: 2026-10-14
---

# Altai the Tiger (ALTAI) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/altai-the-tiger-sol)

---

## Audit Summary

The Altai the Tiger SPL Token Mint audit reveals no critical or high-severity vulnerabilities based on the available on-chain data and third-party security registries. Key authorities such as mint and freeze are revoked, and no permanent delegate or transfer hook is active. Information regarding the locking status of the pool's liquidity was not available for this assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure supply and account immutability. Monitor the token's liquidity pool for any changes, especially regarding the locking status of liquidity, which was not available for this audit. While no immediate risks were identified, continuous monitoring of market dynamics and holder behavior is advisable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Altai the Tiger token operates on the spl-token-2022 program. Its mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states. No Token-2022… |
| **Governance / Economics** | 7/10 | Low | Holder concentration for Altai the Tiger is low, with the top 10 holders that can sell accounting for 14.78% of the supply. The token has a total DEX liquidity of $233,429. The 24-hour volume is… |
| **Upgrades** | 8/10 | Low | The Altai the Tiger token mint has both its mint and freeze authorities revoked, preventing further supply issuance or freezing of accounts. No Token-2022 extensions that allow for upgradability of… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 20.7% of supply. Of that, 6.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.8% in wallets, 0.0% in other contracts. 6,702 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,702 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $478K (DexScreener, all pools). 24h trading volume $7.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $478K of DEX liquidity across 25 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Gyk9Z9...pump`](https://solscan.io/account/Gyk9Z93Ri2JUjqES9HTpc7pxCJTLD7vhBhEjBhyApump) |
| **Network** | Solana |
| **Price** | $0.002063 |
| **24h Volume** | $1.29M |
| **Liquidity** | $241.2K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 3d |
| **Top-10 Holders** | 20.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3006 buys / 3668 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ffmbxjye1urznehdtzgrmjwngxrumlsc17hq9rdrdhyo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/altai-the-tiger-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
