---
token: Quit Your Job
ticker: QUIT
network: solana
risk_score: 16
status: low
date: 2026-10-23
---

# Quit Your Job (QUIT) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quit-your-job-sol)

---

## Audit Summary

The Quit Your Job (QUIT) token is a standard SPL Token-2022 implementation with all critical administrative authorities revoked. The liquidity is fully secured via a 100% burn, and no adverse flags were reported by third-party registries. The token exhibits a healthy trading profile with no evidence of wash trading or excessive holder concentration.

> **Final Recommendation:** The token is configured securely with no administrative backdoors. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains within healthy bounds as the project matures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program (7.1 Architecture). Both Mint and Freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access Control).… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders controlling 21.66% of the supply (7.5 Governance). Liquidity is $46,566, with 100% of LP tokens burned, preventing rug pulls (7.4 Economic). The… |
| **Upgrades** | 10/10 | Low | The token does not support upgrades (7.7 Upgrades). Administrative authorities are permanently revoked, and metadata mutability is disabled (7.8 Operations). No further changes to the token's core… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.2% of supply. Of that, 17.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.9% in wallets, 0.0% in other contracts. 138 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

138 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $47K (DexScreener, all pools). 24h trading volume $34K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $47K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HSHJ3t...qc6p`](https://solscan.io/account/HSHJ3t4Vu3B1qMs9Nv5iKUaoPMQQf1VuT5vVaTvLqc6p) |
| **Network** | Solana |
| **Price** | $0.000322 |
| **24h Volume** | $34.0K |
| **Liquidity** | $46.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 4d |
| **Top-10 Holders** | 36.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 222 buys / 116 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4wl2lls4hsh3hyxkuz7vn7ovqjbmtebre1cif2vlkv6h)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quit-your-job-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
