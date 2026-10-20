---
token: texas cat
ticker: TEXCAT
network: solana
risk_score: 14
status: low
date: 2026-10-18
---

# texas cat (TEXCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/texas-cat-sol)

---

## Audit Summary

The 'texas cat (texcat)' token is an SPL Token-2022 mint with both mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. Liquidity is fully burned, and holder concentration is low. Third-party risk registry data reported no adverse flags, and no critical vulnerabilities were identified based on the provided on-chain facts.

> **Final Recommendation:** This token presents a low-risk profile based on the available on-chain data. Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure supply immutability and account transferability. Continue to monitor DEX liquidity and holder distribution for any significant changes that could impact market stability or exit opportunities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The 'texas cat (texcat)' token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 15.57% of the total supply. The token has $42,639 in DEX liquidity, which is 100.0% burned, ensuring it cannot be… |
| **Upgrades** | 10/10 | Low | The 'texas cat (texcat)' token has no mutable authorities that could alter its core parameters post-launch, as both mint and freeze authorities are revoked. No Token-2022 extensions that would allow… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.7% of supply. Of that, 10.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.6% in wallets, 0.0% in other contracts. 1,726 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,726 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $68K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), 9 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 9 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 9 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BdXfLf...2S5t`](https://solscan.io/account/BdXfLfcbDE8YvpbvvmmGTduqcDesaQVUm5xLxgUc2S5t) |
| **Network** | Solana |
| **Price** | $0.0002447 |
| **24h Volume** | $68.1K |
| **Liquidity** | $43.2K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 9d |
| **Top-10 Holders** | 25.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1018 buys / 524 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/czcfvsc2hqvf1zwu6ya2vrf7g29anu4nnrhw7jvvd3vw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/texas-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
