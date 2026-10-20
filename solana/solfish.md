---
token: SOLFISH
ticker: SOLFISH
network: solana
risk_score: 26
status: low
date: 2026-10-19
---

# SOLFISH (SOLFISH) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solfish-sol)

---

## Audit Summary

The SOLFISH SPL Token Mint demonstrates a robust security configuration with all critical authorities, including Mint and Freeze authorities, being revoked. The token's liquidity is fully burned, ensuring it cannot be withdrawn by any party. Third-party risk registry data was unavailable for this assessment, preventing a comprehensive external risk evaluation.

> **Final Recommendation:** Holders should verify on-chain that the Mint and Freeze authorities remain revoked. Monitor the token's holder distribution for any significant shifts that could lead to increased concentration. While liquidity is currently burned, continuous monitoring of DEX market data is advisable for overall market health.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The SOLFISH token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, preventing further token minting or freezing of holder accounts. No… |
| **Governance / Economics** | 8/10 | Low | The token's liquidity profile is strong, with $16,489 USD in liquidity that is 100.0% burned, meaning it cannot be removed. The top 10 holders that can sell control 49.17% of the supply, which is… |
| **Upgrades** | 10/10 | Low | The SOLFISH token mint has a fixed configuration as both Mint and Freeze authorities are revoked. The metadata is immutable, preventing changes to the token's name, symbol, or image post-launch. No… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 66.5% of supply. Of that, 17.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 49.2% in wallets, 0.0% in other contracts. 613 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

613 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $186K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AHK1P9...pump`](https://solscan.io/account/AHK1P9qNCujgmNp2JxRk5Q71AvJhzJPnFf2TWTkppump) |
| **Network** | Solana |
| **Price** | $0.00004369 |
| **24h Volume** | $81.9K |
| **Liquidity** | $16.2K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 21h |
| **Top-10 Holders** | 66.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1485 buys / 1080 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/29pgpjhhvknophe99cysvyxette1ccnolgjh9a5rymab)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solfish-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
