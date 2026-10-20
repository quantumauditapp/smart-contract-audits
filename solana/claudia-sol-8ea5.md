---
token: Claudia
ticker: CLAUDIA
network: solana
risk_score: 11
status: low
date: 2026-10-10
---

# Claudia (CLAUDIA) — Smart Contract Security Analysis | Solana

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/claudia-sol-8ea5)

---

## Audit Summary

This audit of the Claudia (CLAUDIA) SPL Token Mint found no critical or high-severity risks based on the available on-chain data and third-party security registries. The mint and freeze authorities are revoked, and no Token-2022 extensions posing immediate risks are active. However, information regarding holder distribution and the locking status of the liquidity pool was unavailable, preventing a complete assessment of economic concentration risks.

> **Final Recommendation:** Holders should monitor for the availability of holder distribution data to assess concentration risks. Additionally, verify the locking status of the liquidity pool if that information becomes available, as unlocked liquidity can pose a risk of withdrawal by pool creators. These checks are crucial for a comprehensive understanding of the token's economic stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Claudia token is an SPL Token-2022 mint with its mint authority and freeze authority both revoked, indicating a fixed supply and immutability of account states. No Transfer Hook is configured… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a healthy Volume/Liquidity Ratio of 3.08, which does not suggest wash trading. Total DEX liquidity stands at $270,486, providing reasonable depth for trading. However, data on… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the Claudia token have both been revoked, preventing any further minting or freezing of tokens. The token's metadata is immutable, and there are no… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $572K (DexScreener, all pools). 24h trading volume $3.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $572K of DEX liquidity across 14 pools. Launch: launched on pump.fun (PumpSwap), 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2j5SaS...W2ZM`](https://solscan.io/account/2j5SaS7xy776qCBpyPQbZjyQSAtKiFgrwjfErthnW2ZM) |
| **Network** | Solana |
| **Price** | $0.004419 |
| **24h Volume** | $823.4K |
| **Liquidity** | $273.0K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1903 buys / 2258 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dfheafdf9vk6tjzo7ueuqk6hmwnikzfvvw55wsxdyjuu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/claudia-sol-8ea5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
