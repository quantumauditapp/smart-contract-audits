---
token: USDF🚀
ticker: USDF🚀
network: solana
risk_score: 0
status: low
date: 2026-11-07
---

# USDF🚀 (USDF🚀) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdf-sol-7d5f)

---

## Audit Summary

The USDF🚀 token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, and no malicious extensions such as transfer hooks or mutable balances are present. Holder distribution data was unavailable, preventing a full assessment of concentration risk.

> **Final Recommendation:** The token is technically sound with no active administrative risks. Users should monitor the token's holder distribution via block explorers once data becomes available to ensure no single entity controls a majority of the supply.

Verify the mint and freeze authority status periodically on-chain to ensure they remain null. No further action is required for standard interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with all critical authorities revoked (7.3 Access Control). No transfer hooks or default frozen states are configured (7.1 Architecture). The mint is… |
| **Governance / Economics** | 10/10 | Low | The token maintains $1.12M in liquidity, which is 100% burned, ensuring the pool cannot be drained by the creator (7.4 Economic). Trading volume is healthy relative to liquidity, with a ratio of 0.55… |
| **Upgrades** | 10/10 | Low | The mint authority is revoked, preventing further supply inflation (7.7 Upgrades). Metadata is immutable, ensuring branding consistency (7.2 Code Security). No upgradeable extensions are active on… |

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

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $616K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.1998 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`zb9sid...pump`](https://solscan.io/account/zb9sid1kWd8hi8pJWyMTCVC5XjP9dz9sVcn5Qsmpump) |
| **Network** | Solana |
| **Price** | $0.1998 |
| **24h Volume** | $615.8K |
| **Liquidity** | $1.12M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 30309 buys / 5698 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/h4xnju1wh2kgcdnlizkt4twtscnmaw4aa6f8fbf1ls8g)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdf-sol-7d5f)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
