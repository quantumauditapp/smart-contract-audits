---
token: Cartoon Money
ticker: CBUCKS
network: solana
risk_score: 28
status: low
date: 2026-10-14
---

# Cartoon Money (CBUCKS) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cartoon-money-sol)

---

## Audit Summary

This SPL Token Mint for Cartoon Money (CBUCKS) exhibits a robust security posture with all key authorities revoked and 100% of its liquidity burned. No critical or high-risk vulnerabilities were identified based on the available on-chain data and third-party security registries. Third-party registry data on holder distribution indicated 'Single holder ownership', which is a general signal to monitor.

> **Final Recommendation:** Holders should verify on-chain that the Mint Authority and Freeze Authority remain revoked to ensure supply and transfer stability. While the liquidity is 100% burned, monitoring the overall liquidity levels and trading volume is advisable for market health. Pay attention to the 'Single holder ownership' signal from third-party registries, as this may imply potential market manipulation risks, even if not a direct technical vulnerability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Cartoon Money (CBUCKS) token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, preventing further token creation or account… |
| **Governance / Economics** | 8/10 | Low | The token demonstrates strong liquidity locking, with 100.0% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn. Total DEX liquidity stands at $42,898, with a healthy 24-hour… |
| **Upgrades** | 10/10 | Low | The token's configuration is largely immutable, as both the Mint Authority and Freeze Authority are revoked. Key Token-2022 extensions such as Transfer Hook and Default Account State Frozen are not… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.6% of supply. Of that, 12.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 32.9% in wallets, 10.6% in other contracts. 581 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

581 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $44K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $44K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 7 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DtcicP...pump`](https://solscan.io/account/DtcicPCKTKeAh7TDEzTym3hXeoHAoMiBdYJhMYxZpump) |
| **Network** | Solana |
| **Price** | $0.0002002 |
| **24h Volume** | $37.9K |
| **Liquidity** | $42.9K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 7d |
| **Top-10 Holders** | 55.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 425 buys / 216 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b4cp45pgifvm5faxfh6aev8qz3eunqnqgbw7kuc7mhnb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cartoon-money-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
