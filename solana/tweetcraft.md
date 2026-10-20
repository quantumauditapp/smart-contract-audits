---
token: Tweetcraft
ticker: TWEETCRAFT
network: solana
risk_score: 11
status: low
date: 2026-10-08
---

# Tweetcraft (TWEETCRAFT) — Smart Contract Security Analysis | Solana

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tweetcraft-sol)

---

## Audit Summary

This audit of the Tweetcraft SPL Token Mint found no critical or high-severity issues based on the available on-chain data and third-party security registries. Key authorities, such as mint and freeze, are revoked, and metadata is immutable. However, data on holder concentration and liquidity locking was unavailable, preventing a full assessment of these aspects.

> **Final Recommendation:** Holders should monitor the token's liquidity pool for any changes, especially regarding its locked status, which was not available for this assessment. While no major risks were identified, the absence of holder distribution data means potential concentration risks cannot be fully assessed. Verify on-chain that the reported authority revocations remain unchanged.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Tweetcraft token is an SPL Token-2022 mint on Solana. Its mint authority and freeze authority are both revoked, meaning no new tokens can be created and no existing tokens can be frozen. The… |
| **Governance / Economics** | 7/10 | Low | The token has a total DEX liquidity of $146,284. The 24-hour trading volume is $2,018,885, resulting in a Volume/Liquidity Ratio of 13.80. Information regarding holder concentration and whether the… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing further changes to the token's supply or the freezing of holder accounts. The token's metadata is immutable, meaning its name… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $472K (DexScreener, all pools). 24h trading volume $9.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $472K of DEX liquidity across 11 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HzYCHq...MZQy`](https://solscan.io/account/HzYCHqAN2uoHGRnL9v2ChCfFQX3bvJuJd5zu2Hd5MZQy) |
| **Network** | Solana |
| **Price** | $0.002403 |
| **24h Volume** | $1.81M |
| **Liquidity** | $202.1K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4702 buys / 3863 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3fct5evpwmtsmwwpocrwg7jamknrkcbt6qdzxkwj9gpf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tweetcraft-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
