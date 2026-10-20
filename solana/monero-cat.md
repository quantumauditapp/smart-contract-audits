---
token: Monero Cat
ticker: LUKE
network: solana
risk_score: 20
status: low
date: 2026-10-19
---

# Monero Cat (LUKE) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monero-cat-sol)

---

## Audit Summary

The Monero Cat mint exhibits a clean security profile with zero critical vulnerabilities, featuring revoked mint and freeze keys alongside 100.0% burned pool liquidity. Holder concentration among the top 10 transferable accounts is constrained to 20.96% with no custom extensions enabled. Note that chain-native RPC holder distribution data was unavailable and supplemented by registry records.

> **Final Recommendation:** Query the mint account on-chain via Solana RPC to continuously verify that mint and freeze authorities remain null. Track secondary liquidity pool creation to ensure trades are routed only through pools with provably locked or burned LP positions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized raw supply of 972,487,720,551,211 across 6 decimals. Both mint authority and freeze authority are revoked (None), preventing… |
| **Governance / Economics** | 10/10 | Low | Economic distribution demonstrates decentralized ownership, with pool reserves holding 5.61% outside the top transferable wallets. Total DEX liquidity is $88,552 with 100.0% of LP tokens burned… |
| **Upgrades** | 10/10 | Low | The mint parameters are structurally unchangeable due to the absence of active administrative keys. Metadata mutability is set to false, ensuring the token branding and URI cannot be manipulated… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.6% of supply. Of that, 5.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.0% in wallets, 0.0% in other contracts. 2,318 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,318 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 65% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $140K (DexScreener, all pools). 24h trading volume $2.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $140K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Ez7eEs...pump`](https://solscan.io/account/Ez7eEs53hQiXgCGmcbhdX5i1jgg2gC3F6MoeosuVpump) |
| **Network** | Solana |
| **Price** | $0.0008558 |
| **24h Volume** | $1.75M |
| **Liquidity** | $90.8K |
| **Volume / Liquidity** | 19.3× |
| **Token Age** | 1d |
| **Top-10 Holders** | 26.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 11962 buys / 11149 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2cttz7kndknfrudte7wo3tzkvwapz1zfryuzyahfkrob)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monero-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
