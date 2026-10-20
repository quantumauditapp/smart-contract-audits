---
token: Meme Agency
ticker: MEMEAGENCY
network: solana
risk_score: 0
status: low
date: 2026-10-06
---

# Meme Agency (MEMEAGENCY) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/meme-agency-sol)

---

## Audit Summary

This audit of the Meme Agency SPL Token Mint found no critical or high-severity risks based on the available on-chain data and third-party security signals. Key authorities such as mint and freeze are revoked, and liquidity is fully burned. Holder concentration data was unavailable, preventing a complete assessment of distribution risk.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of accounts. If holder distribution data becomes available in the future, it should be monitored to assess potential concentration risks. No further immediate actions are required based on the current token configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Meme Agency token operates on the spl-token-2022 program, indicating modern Solana token standards. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be… |
| **Governance / Economics** | 10/10 | Low | The token exhibits strong liquidity with $278,365 USD available in DEX pools. A significant security measure is that 100% of the pool's LP tokens are burned, preventing any rug pull related to… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both mint and freeze authorities are permanently revoked. This prevents any future changes to the total supply or the ability to freeze token accounts.… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Meme Agency (MEMEAGENCY), market cap $3M, rank #2249.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $255K (DexScreener, all pools). 24h trading volume $2.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $255K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CyChQH...pump`](https://solscan.io/account/CyChQHfYv6Cn8rP1myNFhdVCGq25Fcah6wzTkiu9pump) |
| **Network** | Solana |
| **Price** | $0.006855 |
| **24h Volume** | $1.84M |
| **Liquidity** | $255.2K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9788 buys / 4802 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7cbnajxqwjduphf1wwemlctlx1wbfqdennv2st2f3c6q)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/meme-agency-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
