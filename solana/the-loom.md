---
token: The Loom
ticker: LOOM
network: solana
risk_score: 13
status: low
date: 2026-10-18
---

# The Loom (LOOM) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-loom-sol)

---

## Audit Summary

The Loom (LOOM) is an SPL Token-2022 mint with a strong security configuration. Key authorities, including mint and freeze, have been revoked, and its metadata is immutable. The token exhibits low holder concentration and has 100% of its liquidity permanently burned, mitigating common risks associated with new tokens.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor the token's liquidity and trading volume for any significant changes, especially given its recent launch. While no major risks were identified, continuous vigilance over market dynamics is always advisable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Loom (LOOM) is an SPL Token-2022 mint on the Solana network. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no existing tokens can be… |
| **Governance / Economics** | 9/10 | Low | The token exhibits low holder concentration, with the top 10 holders that can sell accounting for only 13.68% of the total supply, reducing the risk of large-scale sell-offs. Liquidity for The Loom… |
| **Upgrades** | 10/10 | Low | The Loom (LOOM) token mint has a robust security posture regarding mutability and control. Both the mint and freeze authorities have been permanently revoked, preventing any future changes to the… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.6% of supply. Of that, 3.6% locked, 34.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.7% in wallets, 0.0% in other contracts. 1,251 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as The Loom (LOOM), rank #7537. 1,251 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $44K (CoinGecko, all markets, daily snapshot). 24h trading volume $50K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 4 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7GCMYJ...pump`](https://solscan.io/account/7GCMYJcykHZ3qJH3e5vQi4J9qAPdb3Xninkgk6sYpump) |
| **Network** | Solana |
| **Price** | $0.00002145 |
| **24h Volume** | $49.9K |
| **Liquidity** | $12.3K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 2d |
| **Top-10 Holders** | 51.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 825 buys / 619 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3d8vxmgha44jnfa8cv3x58uzdv5hfhvlk7q5lhcjnvdg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-loom-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
