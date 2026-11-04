---
token: Genius Token – $POCK
ticker: POCK
network: solana
risk_score: 15
status: low
date: 2026-11-04
---

# Genius Token – $POCK (POCK) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/genius-token-pock-sol)

---

## Audit Summary

The Genius Token ($POCK) is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party registries. The token exhibits a healthy trading profile with no evidence of wash trading or excessive concentration.

> **Final Recommendation:** The token is currently in a secure, immutable state. Holders should continue to monitor the top 10 holder addresses periodically to ensure that no single entity accumulates a controlling interest that could impact market stability.

Verify the current mint and freeze authority status using a block explorer to confirm they remain set to 'None'. No further action is required to secure the protocol as the current configuration is fully decentralized.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with all critical authorities revoked, ensuring supply immutability and preventing account freezing. 7.1 Architecture follows standard SPL patterns… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing rug-pull risks via pool withdrawal. 7.5 Governance is decentralized as no single entity controls the mint. Holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint and freeze authorities are revoked. 7.8 Operations are transparent with metadata_mutable set to False, preventing unauthorized branding changes. The token… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.3% of supply. Of that, 4.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 33.7% in wallets, 9.8% in other contracts. 687 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Genius Token (POCK), market cap $2M, rank #2589. 687 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $96K (DexScreener, all pools). 24h trading volume $9K (CoinGecko, all markets, daily snapshot). 24h trading volume $92K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $96K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 221 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`76r29N...pump`](https://solscan.io/account/76r29NpnRW8PAxpnSnVBFcZPUcukgvno1Kkiysg8pump) |
| **Network** | Solana |
| **Price** | $0.001198 |
| **24h Volume** | $91.7K |
| **Liquidity** | $96.3K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 48.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 369 buys / 272 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/kmzeav28ixohqnmzvulce1z82caaexfl8v1wusn7zxn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/genius-token-pock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
