---
token: Doge Pepe
ticker: DOPE
network: solana
risk_score: 8
status: low
date: 2026-10-12
---

# Doge Pepe (DOPE) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doge-pepe-sol)

---

## Audit Summary

This audit of the Doge Pepe (DOPE) SPL Token Mint found no critical or high-severity issues based on available on-chain data and third-party risk registries. The mint and freeze authorities are revoked, and no Token-2022 extensions posing immediate risks are active. Holder distribution and pool liquidity locking status were unavailable for analysis.

> **Final Recommendation:** Holders should monitor the token's liquidity pool for any changes in its locking status, as this information was not available during the audit. Additionally, while holder concentration data was unavailable, it is always prudent to observe on-chain distribution patterns for any significant shifts. Verify the continued revocation of mint and freeze authorities on-chain to confirm the fixed supply and unfreezable nature of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Doge Pepe (DOPE) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a healthy liquidity of $149,791 USD. The 24-hour volume is $1,525,500, resulting in a Volume/Liquidity Ratio of 10.18. This ratio, while noted as high (>5), does not exceed the… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the Doge Pepe (DOPE) token are both revoked, meaning no further administrative actions can be taken to alter the token's supply or freeze accounts. The… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $337K (DexScreener, all pools). 24h trading volume $8.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (doge, pepe); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $337K of DEX liquidity across 29 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`33jENU...pump`](https://solscan.io/account/33jENUQnjoitkMFpvNJcSHyLAHFWJuHwT6E3E8CNpump) |
| **Network** | Solana |
| **Price** | $0.001142 |
| **24h Volume** | $1.52M |
| **Liquidity** | $165.3K |
| **Volume / Liquidity** | 9.2× |
| **Token Age** | 19h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7142 buys / 5277 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/j2xbzkpc7ygbqipw2mwwcqivjn9i44b8gwttrofv1ijj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doge-pepe-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
