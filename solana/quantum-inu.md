---
token: Quantum Inu
ticker: QI
network: solana
risk_score: 8
status: low
date: 2026-10-10
---

# Quantum Inu (QI) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quantum-inu-sol)

---

## Audit Summary

The Quantum Inu (QI) SPL Token Mint exhibits a robust security posture with no critical or high-risk findings identified from the available on-chain data. Both the mint and freeze authorities have been revoked, preventing further token issuance or account freezing. However, information regarding holder concentration and liquidity lock status was unavailable, which limits a complete economic risk assessment.

> **Final Recommendation:** Holders should monitor for any future changes in the token's on-chain state, particularly regarding liquidity provision and distribution, if that data becomes available. While current authorities are revoked, the absence of holder distribution data means potential concentration risks cannot be fully assessed. Verify the continued revocation of mint and freeze authorities periodically.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Quantum Inu (QI) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 7/10 | Low | The token has a total DEX liquidity of $245,770. The 24-hour trading volume is $1,604,097, resulting in a Volume/Liquidity Ratio of 6.53. The trading pair is very new, with an age of 0 days.… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority have both been revoked, meaning the token's supply and account freeze status cannot be altered. The token's metadata (name, symbol, image) is immutable… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $526K (DexScreener, all pools). 24h trading volume $9.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $526K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8TiMkg...iXaQ`](https://solscan.io/account/8TiMkgvsrat9tM2esko8zVTt99LZLpefUM4SnZaziXaQ) |
| **Network** | Solana |
| **Price** | $0.002742 |
| **24h Volume** | $1.56M |
| **Liquidity** | $239.8K |
| **Volume / Liquidity** | 6.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4259 buys / 4217 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/57jmg2uos4wgftbuergs2azhepbbnp8fjrgelmnx8uxv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quantum-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*
