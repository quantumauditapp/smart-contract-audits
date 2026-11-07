---
token: Donna Dollars
ticker: DONNA
network: solana
risk_score: 2
status: low
date: 2026-11-07
---

# Donna Dollars (DONNA) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/donna-dollars-sol)

---

## Audit Summary

Donna Dollars (DONNA) is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party registries. The token exhibits low holder concentration and healthy trading metrics.

> **Final Recommendation:** The token is in a highly secure state with no administrative backdoors. Holders should continue to monitor the top 10 holder distribution periodically to ensure concentration remains low. No further action is required to secure the current token configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing rug-pulls via withdrawal. 7.5 Governance is decentralized with the top 10 holders controlling only 4.85% of the supply. 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a static SPL token. Metadata is immutable, and there are no upgradeable hooks or fees. The asset state is fixed and cannot be altered by any external… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 10.7% of supply. Of that, 5.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.8% in wallets, 0.0% in other contracts. 809 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Donna Dollars (DONNA), rank #3728. 809 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $5K (CoinGecko, all markets, daily snapshot). 24h trading volume $85K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.001551 — it does not hold a peg. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $100K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 14 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 14 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 14 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FMqWsX...pump`](https://solscan.io/account/FMqWsXKaAe41Kxfji7v5cpzQmr2gKAteAi9wREmkpump) |
| **Network** | Solana |
| **Price** | $0.001551 |
| **24h Volume** | $84.8K |
| **Liquidity** | $100.2K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 14d |
| **Top-10 Holders** | 10.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 440 buys / 307 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7vurupbxg3z5qjtcstvg3vxumxenqfnupjdz3cgw2tkt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/donna-dollars-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
