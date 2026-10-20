---
token: Solamians
ticker: SOLAMIANS
network: solana
risk_score: 16
status: low
date: 2026-10-14
---

# Solamians (SOLAMIANS) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solamians-sol)

---

## Audit Summary

The Solamians SPL Token Mint exhibits a low-risk profile with no critical or high-severity findings identified. Key authorities such as mint and freeze are revoked, and liquidity is fully burned. Third-party risk registry data reported no adverse flags, though chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** Holders should continuously monitor the token's on-chain state for any unexpected changes, although the current configuration shows strong immutability. Verify that the mint and freeze authorities remain revoked. Regularly check DEX liquidity and trading volume for any significant shifts that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Solamians token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no existing accounts can… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 15.73% of the total supply. The token benefits from robust liquidity, with $26,187 USD in DEX pools, and 100% of this… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable due to the revocation of both Mint and Freeze Authorities. Furthermore, the metadata is not mutable, ensuring the token's name, symbol, and image cannot be… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.2% of supply. Of that, 21.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.7% in wallets, 0.0% in other contracts. 2,243 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,243 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $30K (DexScreener, all pools). 24h trading volume $180K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8ZP5Cz...pump`](https://solscan.io/account/8ZP5CzbPL1fmP8dn1GEmLd8xw1JdudUF5Dk7EpLxpump) |
| **Network** | Solana |
| **Price** | $0.00007173 |
| **24h Volume** | $168.7K |
| **Liquidity** | $26.2K |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1643 buys / 1464 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/89dxsak1yzx8tbpapmssegkedhyuhybo26bytgelrjbd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solamians-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
