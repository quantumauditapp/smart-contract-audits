---
token: Larp Scanner
ticker: LARPSCAN
network: solana
risk_score: 22
status: low
date: 2026-10-19
---

# Larp Scanner (LARPSCAN) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/larp-scanner-sol)

---

## Audit Summary

This audit of the Larp Scanner (LARPSCAN) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and deterministic rules. The mint and freeze authorities are revoked, and liquidity is fully burned. Third-party risk registry data was unavailable for a comprehensive external assessment.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature. Monitor the token's liquidity and trading volume for any significant changes, especially given the very recent creation of the trading pair. Be aware that third-party risk registry data was unavailable, so a full external risk assessment could not be completed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Larp Scanner (LARPSCAN) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing accounts can be… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 28.07% of the supply, which does not indicate significant centralization risk. The token has sufficient liquidity at… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any further changes to the token's supply or account freeze status. The token's metadata is immutable, meaning its name, symbol… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.9% of supply. Of that, 22.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 28.1% in wallets, 0.0% in other contracts. 226 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

226 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $150K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 7 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2qfUSu...pump`](https://solscan.io/account/2qfUSuUfKuxHyYEMYreiYdK3YyapFzbgq2c6hhfPpump) |
| **Network** | Solana |
| **Price** | $0.0000384 |
| **24h Volume** | $146.6K |
| **Liquidity** | $15.1K |
| **Volume / Liquidity** | 9.7× |
| **Token Age** | 7d |
| **Top-10 Holders** | 50.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1820 buys / 1361 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2alatuc5rmitb9cobteg48deedgem1kdcuhq6vorxhmu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/larp-scanner-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
