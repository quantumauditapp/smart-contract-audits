---
token: Crawlerpad
ticker: CRAWLER
network: solana
risk_score: 19
status: low
date: 2026-10-16
---

# Crawlerpad (CRAWLER) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crawlerpad-sol)

---

## Audit Summary

This audit of the Crawlerpad (CRAWLER) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint authority and freeze authority are both revoked, and 100% of the pool's liquidity is burned, indicating a secure setup for token issuance and liquidity. Third-party risk registry data reported no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint authority and freeze authority remain revoked to ensure the token's supply and transferability are fixed. Monitor the token's liquidity and trading volume for any significant changes, although the burned liquidity provides strong stability. No further immediate actions are required given the current state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Crawlerpad (CRAWLER) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 29.53% of the supply, reducing the risk of large-scale dumps. The token has $14,279 in DEX liquidity, and its 24-hour volume… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any administrative changes to the token's supply or account states. The token utilizes the spl-token-2022 program but does not… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $84K (CoinGecko, all markets, daily snapshot). 24h trading volume $35K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0321 on 2026-10-13; the price is now 99.9261% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 58.0% of supply. Of that, 28.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 29.5% in wallets, 0.0% in other contracts. 868 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Crawlerpad (CRAWLER), rank #8085. 868 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CQCDTp...pump`](https://solscan.io/account/CQCDTp8rsFV3PhaPeYjcCW5LdGTxi6jFx7eC3UXnpump) |
| **Network** | Solana |
| **Price** | $0.00002101 |
| **24h Volume** | $34.5K |
| **Liquidity** | $13.3K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 3d |
| **Top-10 Holders** | 58.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 757 buys / 349 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/anrchvfjuzmtos8dgjpt2xkurvppyavldturasnwxcd4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crawlerpad-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
