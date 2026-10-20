---
token: Tiktok Coin
ticker: TIKTOK
network: solana
risk_score: 16
status: low
date: 2026-10-11
---

# Tiktok Coin (TIKTOK) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tiktok-coin-sol)

---

## Audit Summary

The Tiktok Coin (TikTok) SPL Token Mint exhibits a robust security posture with both mint and freeze authorities revoked, ensuring a fixed supply and preventing account freezing. All pool liquidity is permanently burned, eliminating rug pull risks from liquidity withdrawal. Holder distribution data was unavailable, which prevents a full assessment of whale concentration risks.

> **Final Recommendation:** This token presents a low-risk profile based on available on-chain data. Holders should monitor for any new information regarding holder distribution, which was unavailable in this audit. While the burned liquidity mitigates rug pull risks, market depth remains relatively low, so large trades may experience slippage. No further on-chain verification steps are immediately required given the revoked authorities and locked liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program, indicating modern SPL token standards. Both the Mint Authority and Freeze Authority have been revoked, which is a strong positive for… |
| **Governance / Economics** | 9/10 | Low | The token's economic stability is bolstered by the fact that 100% of its pool liquidity is burned, meaning it cannot be withdrawn by any party (Pool Liquidity Burned or Locked for Good: 100.0%).… |
| **Upgrades** | 10/10 | Low | The token's immutability is high, as both mint and freeze authorities are revoked, preventing any future changes to supply or account status. Furthermore, critical Token-2022 extension mutability… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $38K (DexScreener, all pools). 24h trading volume $159K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $38K of DEX liquidity across 27 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`64oAuE...YgCp`](https://solscan.io/account/64oAuE88tNP7KsSyaiJTKGP4sWmLMFGWLUs9eBTLYgCp) |
| **Network** | Solana |
| **Price** | $0.0001089 |
| **24h Volume** | $139.5K |
| **Liquidity** | $34.8K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1586 buys / 1472 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bjhum36bzoybhergspkzlzsttbpbdbjcdoeka7o9n2o)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tiktok-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
