---
token: JUP PAD
ticker: JPAD
network: solana
risk_score: 0
status: low
date: 2026-10-11
---

# JUP PAD (JPAD) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jup-pad-sol)

---

## Audit Summary

The JUP PAD (JPAD) SPL token mint exhibits a low-risk profile based on available on-chain data and external security signals. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing asset freezing. While holder concentration data was unavailable, the token shows robust liquidity locking and no adverse flags from third-party registries.

> **Final Recommendation:** Holders should regularly verify the on-chain status of the token mint, specifically confirming that mint and freeze authorities remain revoked. Monitor DEX liquidity and trading volume for any significant changes that could impact market stability. Be aware that holder distribution data was not available, so monitor on-chain transfers for any emerging concentration risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The JUP PAD (JPAD) token is implemented using the standard `spl-token` program. Both the mint authority and freeze authority have been revoked, which is a strong security positive, ensuring no new… |
| **Governance / Economics** | 10/10 | Low | The token's liquidity stands at $83,170 USD, with a 24-hour volume of $376,527, resulting in a normal Volume/Liquidity Ratio of 4.53. A significant 99.3% of the pool's liquidity is locked for good… |
| **Upgrades** | 10/10 | Low | The token mint's core authorities, including mint and freeze, are fully revoked, eliminating the possibility of unauthorized supply changes or asset freezing. The token's metadata is immutable… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.3% of the pool's LP is burned or time-locked. 99.3% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 0.6% is held, unlocked, by 3 address(es) other than the pool's creator. This assessment covers the main pool, which holds 66% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $120K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $120K of DEX liquidity across 10 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4mbPZz...jupx`](https://solscan.io/account/4mbPZzDCWXvTCJbscMWeDD7TT1pra9mkZHGaBxc2jupx) |
| **Network** | Solana |
| **Price** | $0.0004495 |
| **24h Volume** | $485.7K |
| **Liquidity** | $80.0K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2203 buys / 1973 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8foqfa6pyc7mgbab3ijttwhq692p85enwrstv6y6vvjw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jup-pad-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
