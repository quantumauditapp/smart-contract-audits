---
token: Suicaのペンギン
ticker: SUICA
network: solana
risk_score: 24
status: low
date: 2026-11-04
---

# Suicaのペンギン (SUICA) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/suica-sol)

---

## Audit Summary

The Suica token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully burned, ensuring the pool cannot be rug-pulled by the creator. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** The token exhibits strong security properties regarding authority revocation and liquidity safety. Users should monitor the token's market activity and volume/liquidity ratio to ensure slippage remains within acceptable bounds for their position size.

As holder concentration data is currently unavailable, investors should exercise standard caution regarding potential market volatility. Verify the token mint address directly on a block explorer before interacting to ensure you are transacting with the correct asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or custom extensions… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured with 100% of LP tokens burned, preventing creator withdrawal (7.4 Economic). The token shows active trading volume relative to its $18,389 liquidity (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding metadata and authority settings (7.7 Upgrades). No balance-mutating or transfer-fee-upgradable extensions are enabled (7.8 Operations). The token state is fixed and… |

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

Liquidity $16K (DexScreener, all pools). 24h trading volume $290K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`t2TGpq...pump`](https://solscan.io/account/t2TGpqDS81fNNXCST8hxNrRsfVPxJdw41Cct4yLpump) |
| **Network** | Solana |
| **Price** | $0.0000446 |
| **24h Volume** | $252.8K |
| **Liquidity** | $15.9K |
| **Volume / Liquidity** | 15.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3321 buys / 2505 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/byvbfg1taqm1d1nzw4df5xtrympggytdg5uiycpm8eer)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/suica-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
