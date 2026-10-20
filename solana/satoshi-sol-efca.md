---
token: Satoshi
ticker: SATOSHI
network: solana
risk_score: 29
status: low
date: 2026-10-17
---

# Satoshi (SATOSHI) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/satoshi-sol-efca)

---

## Audit Summary

This audit of the Satoshi SPL token mint found no critical or high-severity issues based on the available on-chain data and third-party risk registries. The mint authority and freeze authority are both revoked, ensuring a fixed supply and preventing asset freezing. Holder concentration is moderate, and DEX liquidity is fully burned, providing stability. Chain-native RPC data for some holder distribution details was unavailable.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature. Monitor the token's trading volume and liquidity over time, especially given its young age, to assess market stability. While current holder concentration is moderate, continued observation of distribution patterns is advisable for long-term holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Satoshi token operates on the spl-token-2022 program, indicating modern SPL token standards. Both the mint authority and freeze authority have been revoked, which means no new tokens can be… |
| **Governance / Economics** | 8/10 | Low | The token exhibits moderate holder concentration, with the top 10 holders that can sell accounting for 35.22% of the total supply. DEX liquidity stands at $18,003 USD, and importantly, 100.0% of the… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters, such as supply and transferability, cannot be altered by any single entity. The token does not utilize a… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.0% of supply. Of that, 20.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 35.2% in wallets, 0.0% in other contracts. 343 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

343 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $109K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (toshi); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 3 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SAtoZG...SHi1`](https://solscan.io/account/SAtoZGJkh4Eid9EQZYXWnCNVn5asZrWZLouBMX1SHi1) |
| **Network** | Solana |
| **Price** | $0.00004698 |
| **24h Volume** | $109.0K |
| **Liquidity** | $17.8K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 56.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1258 buys / 892 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7jtcpyho9rjhcn9zyrlpjwgwkacghjvdzl2czni3uduh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/satoshi-sol-efca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
