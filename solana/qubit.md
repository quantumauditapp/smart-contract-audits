---
token: QUBIT
ticker: QUBIT
network: solana
risk_score: 15
status: low
date: 2026-10-12
---

# QUBIT (QUBIT) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/qubit-sol)

---

## Audit Summary

This audit of the QUBIT SPL Token Mint found no critical or high-severity issues based on the available on-chain data and external security signals. Both mint and freeze authorities are revoked, and all pool liquidity is burned. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

> **Final Recommendation:** Holders should verify on-chain that the mint authority and freeze authority remain revoked to ensure supply and account immutability. Monitor DEX liquidity and trading volume for any significant changes, especially given the unavailability of holder concentration data. While current liquidity is burned, continuous monitoring of market dynamics is prudent for any token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The QUBIT token is an SPL Token-2022 mint with both Mint Authority and Freeze Authority revoked, indicating a fixed supply and immutability of account states. No Token-2022 extensions such as… |
| **Governance / Economics** | 9/10 | Low | The token exhibits healthy liquidity characteristics with $20,924 in total DEX liquidity, which is sufficient for its current trading volume. A significant positive is that 100.0% of the pool's LP… |
| **Upgrades** | 10/10 | Low | The QUBIT token mint is configured with a high degree of immutability, as both the Mint Authority and Freeze Authority have been revoked. This ensures that no new tokens can be minted and no accounts… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as QUBIT (QUBIT), rank #6545.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $113K (CoinGecko, all markets, daily snapshot). 24h trading volume $71K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.000692 on 2026-10-10; the price is now 91.0032% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 9 pools. Launch: launched on pump.fun (PumpSwap), 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ERkmk5...uBit`](https://solscan.io/account/ERkmk5rs8KKD9u2fxoDZUmwwuVc7rT3sSeowGTrQuBit) |
| **Network** | Solana |
| **Price** | $0.00004449 |
| **24h Volume** | $65.9K |
| **Liquidity** | $20.2K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 589 buys / 579 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9d6fbbtagjm6efho4npsprdgnwhzndetgewhmupztvjv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/qubit-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
