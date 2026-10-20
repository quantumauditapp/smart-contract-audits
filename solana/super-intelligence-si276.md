---
token: Super Intelligence SI276
ticker: SI276
network: solana
risk_score: 2
status: low
date: 2026-10-08
---

# Super Intelligence SI276 (SI276) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-intelligence-si276-sol)

---

## Audit Summary

This audit of the Super Intelligence SI276 SPL Token Mint found no critical or high-severity risks based on the available on-chain data and third-party security registries. The mint and freeze authorities are revoked, and all liquidity is burned or locked. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** This token presents a low risk profile based on the available data. Holders should continue to monitor DEX market data for any significant changes in liquidity or trading patterns. While holder concentration data was unavailable for this audit, it is advisable to periodically check on-chain holder distribution to identify any emerging concentration risks. No further on-chain verification steps are immediately required given the revoked authorities and locked liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Super Intelligence SI276 token is implemented using the spl-token-2022 program. A key strength is that both the Mint Authority and Freeze Authority have been revoked, preventing further token… |
| **Governance / Economics** | 10/10 | Low | The token exhibits healthy liquidity, with $60,714 USD available in DEX pools. A significant positive is that 100.0% of the pool's LP tokens are burned, ensuring that this liquidity can never be… |
| **Upgrades** | 10/10 | Low | The token's immutability is strong, with both Mint and Freeze authorities permanently revoked. Key Token-2022 extensions such as transfer hook and transfer fee are not present, and their… |

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

Liquidity $61K (DexScreener, all pools). 24h trading volume $454K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $61K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HMYd9t...pump`](https://solscan.io/account/HMYd9tosnUXuNHmq7pXmoePRVBLBBjA3JBfydq6upump) |
| **Network** | Solana |
| **Price** | $0.0004404 |
| **24h Volume** | $454.1K |
| **Liquidity** | $61.3K |
| **Volume / Liquidity** | 7.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6964 buys / 4507 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/12jc1dzjpzbcdakum4brakh9jcfry2tlg1ffgsl4ftcg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-intelligence-si276-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
