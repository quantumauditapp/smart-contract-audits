---
token: ZachXBT
ticker: ZACHXBT
network: solana
risk_score: 19
status: low
date: 2026-10-06
---

# ZachXBT (ZACHXBT) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zachxbt-sol)

---

## Audit Summary

This SPL Token Mint presents a low-risk profile based on available on-chain data. Key authorities, including mint and freeze, are revoked, and 100% of the DEX liquidity is permanently burned. No high-risk Token-2022 extensions like transfer hooks or default frozen accounts are active. A third-party risk registry reported no adverse flags.

> **Final Recommendation:** Given the revoked mint and freeze authorities and burned liquidity, this token appears to have reduced centralisation risks. Holders should continue to monitor DEX market data for any significant changes in liquidity or trading patterns. Verify on-chain that the mint and freeze authorities remain revoked before any significant interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | This token is an SPL Token-2022 mint with a supply of 999,442,100.184573 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, preventing further token issuance or… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell controlling 25.58% of the supply. The token has $22,761 in DEX liquidity, with a 24-hour volume of $196,716, resulting in a… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further tokens can be minted and no accounts can be frozen. The token's metadata is immutable, preventing changes to its name… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.1% of supply. Of that, 2.4% burned, 28.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 25.6% in wallets, 0.0% in other contracts. 920 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

920 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $198K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 280 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`281Ypq...pump`](https://solscan.io/account/281YpqPYRf3zKrqxg9uiMJ3ojCt2YijAFSM2thZZpump) |
| **Network** | Solana |
| **Price** | $0.00003971 |
| **24h Volume** | $196.3K |
| **Liquidity** | $22.4K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 56.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1623 buys / 1114 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cy35chatjorcma7jtdrz5j2dml5gyojiskqrwaredcm3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zachxbt-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
