---
token: Saindra
ticker: SAINDRA
network: solana
risk_score: 7
status: low
date: 2026-10-17
---

# Saindra (SAINDRA) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saindra-sol)

---

## Audit Summary

The Saindra SPL token mint exhibits strong security characteristics, with both mint and freeze authorities revoked. Liquidity is fully burned, and holder concentration is low. No adverse flags were reported by third-party risk registries, and no critical or high-severity issues were identified based on the provided on-chain facts.

> **Final Recommendation:** Given the revoked authorities and fully burned liquidity, this token presents a low-risk profile from a smart contract and liquidity rug-pull perspective. Holders should continue to monitor market dynamics and trading volume, as well as any future announcements from the token's creators. No specific on-chain verification steps are required beyond confirming the current state of revoked authorities and burned liquidity, which are already established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Saindra token is an SPL Token-2022 mint with its mint and freeze authorities permanently revoked, ensuring a fixed supply and preventing account freezing. No transfer hook is active, and new… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 22.29% of the supply. DEX liquidity is $49,568, and 100% of the pool's LP tokens are burned, preventing liquidity… |
| **Upgrades** | 10/10 | Low | Both the mint and freeze authorities are revoked, meaning no further tokens can be minted and no accounts can be frozen. The token's metadata is immutable, preventing changes to its name, symbol, or… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.5% of supply. Of that, 9.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.3% in wallets, 0.0% in other contracts. 2,141 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Saindra (SAINDRA), rank #4791. 2,141 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 82% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $285K (CoinGecko, all markets, daily snapshot). 24h trading volume $355K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 7 pools. Launch: launched on pump.fun (PumpSwap), 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`A2yA6A...kA9T`](https://solscan.io/account/A2yA6AFtfKkfVkfsnGpvsKoUV5kQPpMYboZsBPvmkA9T) |
| **Network** | Solana |
| **Price** | $0.0002338 |
| **24h Volume** | $327.4K |
| **Liquidity** | $48.6K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 3d |
| **Top-10 Holders** | 31.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2837 buys / 3075 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9hjkmterujufrayursteheyjzg83lq52behux54lsef6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saindra-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
