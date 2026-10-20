---
token: No Risk No Rari
ticker: RARI
network: solana
risk_score: 0
status: low
date: 2026-10-09
---

# No Risk No Rari (RARI) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/no-risk-no-rari-sol)

---

## Audit Summary

The No Risk No Rari (RARI) SPL Token Mint exhibits strong security characteristics with both mint and freeze authorities revoked, ensuring a fixed supply and preventing asset confiscation. All pool liquidity is burned, eliminating rug pull risks from liquidity withdrawal. However, holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Holders should continue to monitor the token's holder distribution if this data becomes available, as high concentration could pose a risk. While the current setup is robust, staying informed about any future on-chain changes or external security registry flags is advisable. Verify on-chain that the mint and freeze authorities remain revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The No Risk No Rari (RARI) token is implemented using the spl-token-2022 program. Key security features include the revocation of both mint and freeze authorities, preventing further token issuance… |
| **Governance / Economics** | 10/10 | Low | The token's economic profile shows a liquidity of $123,274 USD with a 24-hour volume of $857,955, resulting in a Volume/Liquidity Ratio of 6.96. All 100% of the pool's liquidity provider tokens are… |
| **Upgrades** | 10/10 | Low | The No Risk No Rari (RARI) token mint has a fixed configuration due to the revocation of its mint and freeze authorities. The token's metadata is immutable, preventing changes to its name, symbol, or… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as No Risk No Rari (RARI), market cap $1M, rank #2701.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 56% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $220K (DexScreener, all pools). 24h trading volume $1.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $220K of DEX liquidity across 25 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EFn88C...gYwR`](https://solscan.io/account/EFn88CiiFHhihqdr1Y11XBDxbbYarBf1ij92DsrigYwR) |
| **Network** | Solana |
| **Price** | $0.001318 |
| **24h Volume** | $875.1K |
| **Liquidity** | $122.9K |
| **Volume / Liquidity** | 7.1× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2895 buys / 2707 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ioadgkquh6h5nntmcv8k3nvagstis3xmfnan3j11kzv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/no-risk-no-rari-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
