---
token: CRAWLNET
ticker: CRAWL
network: solana
risk_score: 9
status: low
date: 2026-10-06
---

# CRAWLNET (CRAWL) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crawlnet-sol)

---

## Audit Summary

This audit of the CRAWLNET (CRAWL) SPL Token Mint found no critical or high-severity issues based on the available on-chain data and external security signals. Both mint and freeze authorities are revoked, indicating a fixed supply and unfreezable accounts. Holder concentration data and liquidity locking status were unavailable, preventing a full assessment of economic risks related to distribution and pool stability.

> **Final Recommendation:** Before engaging with this token, users should monitor for updates regarding holder distribution to assess potential concentration risks. It is also crucial to verify the status of the pool's liquidity, specifically whether it is locked or burned, to mitigate risks associated with liquidity withdrawal by pool creators. Continue to monitor the token's trading activity and liquidity over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CRAWLNET (CRAWL) token is an SPL Token-2022 mint. Its mint authority is revoked, ensuring no new tokens can be created, and its freeze authority is also revoked, preventing any account from being… |
| **Governance / Economics** | 7/10 | Low | The token has a total DEX liquidity of $314,641, with a 24-hour volume of $1,187,623. The Volume/Liquidity Ratio is 3.77, which is considered normal and does not indicate wash trading. The pair is… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the CRAWLNET token are both revoked, meaning these core functionalities cannot be altered or re-enabled. The token's metadata is immutable, preventing… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CRAWLNET (CRAWL), market cap $4M, rank #1961.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $709K (DexScreener, all pools). 24h trading volume $7.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $6.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $709K of DEX liquidity across 9 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BXoHJd...pump`](https://solscan.io/account/BXoHJddsWJLHtAopeiSbKUSELsu8hSFMs8baGMDkpump) |
| **Network** | Solana |
| **Price** | $0.004878 |
| **24h Volume** | $1.19M |
| **Liquidity** | $317.4K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1827 buys / 1977 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4s2bzym1cstvwcuc1r1q8maoj6umkqnbqnwbeftdtpko)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crawlnet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
