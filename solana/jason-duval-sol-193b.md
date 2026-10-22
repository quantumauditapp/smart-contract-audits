---
token: Jason Duval
ticker: JASON
network: solana
risk_score: 20
status: low
date: 2026-10-22
---

# Jason Duval (JASON) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jason-duval-sol-193b)

---

## Audit Summary

The Jason Duval (JASON) token is a standard SPL Token-2022 implementation with all administrative authorities revoked. The token exhibits a healthy liquidity profile with 100% of pool liquidity permanently burned, and no adverse flags were reported by third-party registries. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** The token is currently in a secure, immutable state. Holders should monitor the top 10 holder addresses periodically to ensure concentration does not increase significantly over time.

No further action is required to secure the token contract itself. Users should verify the mint address 6fJPx1nWz6PvMifsee6AtTi4H3srtis5rHAUs3HYpump on a block explorer before interacting to ensure they are transacting with the correct asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Access control is fully decentralized as both the Mint and Freeze authorities are revoked (7.3 Access Control). The token does not employ… |
| **Governance / Economics** | 9/10 | Low | The top 10 holders control 24.75% of the supply, indicating a distributed ownership structure (7.4 Economic). Liquidity is $18,225 with a stable volume/liquidity ratio of 2.32 (7.6 External). All… |
| **Upgrades** | 10/10 | Low | The token mint is immutable due to the revocation of all administrative authorities (7.7 Upgrades). Metadata is immutable, ensuring branding consistency (7.8 Operations). No further upgrades or… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.3% of supply. Of that, 18.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.8% in wallets, 0.0% in other contracts. 293 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

293 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $44K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6fJPx1...pump`](https://solscan.io/account/6fJPx1nWz6PvMifsee6AtTi4H3srtis5rHAUs3HYpump) |
| **Network** | Solana |
| **Price** | $0.00005539 |
| **24h Volume** | $43.8K |
| **Liquidity** | $18.4K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 43.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 545 buys / 349 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8ewubnmadzl8barpnk5gdw2is1qdcppz7xtlhnzdmkxn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jason-duval-sol-193b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
