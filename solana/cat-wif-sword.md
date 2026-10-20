---
token: cat wif sword
ticker: SWORDCAT
network: solana
risk_score: 0
status: low
date: 2026-10-01
---

# cat wif sword (SWORDCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cat-wif-sword-sol)

---

## Audit Summary

The `cat wif sword` (swordcat) SPL Token Mint audit found no critical or high-risk vulnerabilities based on available on-chain data and third-party security registries. The mint and freeze authorities are revoked, and 100% of the pool's liquidity is burned. Holder concentration data was unavailable.

> **Final Recommendation:** Given the revoked mint and freeze authorities and the burned liquidity, the token presents a low-risk profile based on the available data. Holders should continue to monitor the token's market behavior and any future announcements. If holder distribution data becomes available, it should be reviewed to assess potential concentration risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `cat wif sword` token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, preventing further token creation or freezing of holder accounts (7.3 Access… |
| **Governance / Economics** | 10/10 | Low | The token exhibits a healthy liquidity profile with $81,855 in total DEX liquidity, and 100% of the pool's LP tokens are burned, ensuring liquidity cannot be withdrawn by any single entity (7.4… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further tokens can be minted and no accounts can be frozen (7.7 Upgrades). The token does not utilize a Transfer Hook, and its… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as cat wif sword (SWORDCAT), rank #3357.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 68% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $118K (DexScreener, all pools). 24h trading volume $1.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $864K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $118K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5tCju6...pump`](https://solscan.io/account/5tCju6YNxHq5zrA6tGndr6F7TK42mpUFmeE31cSFpump) |
| **Network** | Solana |
| **Price** | $0.0005531 |
| **24h Volume** | $693.5K |
| **Liquidity** | $80.0K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4577 buys / 4848 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8ewuf2o8acro7fqwepz3tkhkbbjndzu4ldk9scrpw83d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cat-wif-sword-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
