---
token: Pluto
ticker: PLUTO
network: solana
risk_score: 36
status: medium
date: 2026-10-18
---

# Pluto (PLUTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pluto-sol)

---

## Audit Summary

The Pluto token is flagged as high-risk by an independent third-party registry due to the creator's history of rugged tokens. Additionally, the token exhibits very low liquidity, with total DEX liquidity at $9,942, making large positions difficult to exit without significant slippage. Third-party risk registry data was available, but chain-native RPC data on holder distribution was not fully available.

> **Final Recommendation:** Given the critical flag from a third-party risk registry, it is strongly advised to avoid any interaction with this token. If considering engagement despite the high-risk flag, verify the current liquidity on DEXs immediately before any transaction, as the current level is extremely low and subject to rapid change. Monitor the third-party risk registry for any updates to its assessment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Pluto token is an SPL Token-2022 mint with a total supply of 953,987,687.545485 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can… |
| **Governance / Economics** | 7/10 | Low | The token exhibits very low liquidity, with total DEX liquidity at $9,942, which can lead to severe slippage for trades. Despite this, 100.0% of the pool's LP tokens are burned, ensuring that… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing any future changes to the token's supply or account freeze status. The token does not have a transfer hook or default account… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset, specifically citing a creator history of rugged tokens.

**Recommendation:** Do not interact with this token.


### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,942. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the severe slippage when considering any trade.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $121K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.6% of supply. Of that, 25.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.7% in wallets, 0.0% in other contracts. 306 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

306 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6jijW4...pump`](https://solscan.io/account/6jijW4Ne924kqj8XYLKXFrhpeHy5y2qxoKgGzJHQpump) |
| **Network** | Solana |
| **Price** | $0.00001848 |
| **24h Volume** | $63.3K |
| **Liquidity** | $9.8K |
| **Volume / Liquidity** | 6.5× |
| **Token Age** | 3d |
| **Top-10 Holders** | 48.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1002 buys / 853 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5frtjsz43ms1kz2zrha9qlhteehemn7hpk43ntrbpd4u)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pluto-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
