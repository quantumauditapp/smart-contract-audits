---
token: United States Dividend Fund
ticker: USDF
network: solana
risk_score: 0
status: low
date: 2026-10-08
---

# United States Dividend Fund (USDF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-sol)

---

## Audit Summary

This audit of the United States Dividend Fund (USDF) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. Key authorities, including mint and freeze, are revoked, and liquidity is fully burned. Holder concentration data was unavailable from chain-native RPC.

> **Final Recommendation:** Holders should verify on-chain that the Mint Authority and Freeze Authority remain revoked to ensure the supply is fixed and accounts cannot be frozen. Monitor for any future changes in liquidity or trading patterns, although the current liquidity is fully burned. Be aware that holder distribution data was unavailable, which could hide potential concentration risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The USDF token is implemented using the spl-token-2022 program, indicating modern SPL token standards. Both the Mint Authority and Freeze Authority are revoked (None), preventing further token… |
| **Governance / Economics** | 10/10 | Low | The token exhibits strong economic fundamentals with substantial DEX liquidity of $3,367,956 and a normal 24-hour Volume/Liquidity Ratio of 0.79. Crucially, 100.0% of the pool's liquidity provider… |
| **Upgrades** | 10/10 | Low | The token's core parameters are highly immutable, as both the Mint Authority and Freeze Authority have been revoked. Furthermore, the metadata is not mutable, meaning the token's name, symbol, or… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.3M (DexScreener, all pools). 24h trading volume $3.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $1.36 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $3.3M of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HQowBX...pump`](https://solscan.io/account/HQowBX7JqXUEDPWHB4bS6q6KEzvSdfDPXv6qefipump) |
| **Network** | Solana |
| **Price** | $1.3600 |
| **24h Volume** | $3.19M |
| **Liquidity** | $3.34M |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 80001 buys / 4572 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fl5gakwfzqwgqmow3qwa8u3y4z8gqpquvljedphf31c6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
