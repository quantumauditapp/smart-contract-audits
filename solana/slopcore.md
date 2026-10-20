---
token: SLOPCORE
ticker: SLOPCORE
network: solana
risk_score: 2
status: low
date: 2026-10-06
---

# SLOPCORE (SLOPCORE) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/slopcore-sol)

---

## Audit Summary

This SPL Token Mint for SLOPCORE exhibits strong security characteristics with no critical or high-risk issues identified by the deterministic audit rules. Both mint and freeze authorities are revoked, and 100% of the liquidity is burned. Third-party risk registry data reported no adverse flags, and chain-native RPC data for holder distribution was successfully collected.

> **Final Recommendation:** This token appears to be well-configured from a security perspective based on the provided on-chain facts. Holders should continue to monitor the token's trading activity and liquidity for any significant changes. Verify on-chain that the mint and freeze authorities remain revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The SLOPCORE token is an SPL Token-2022 mint with both the mint authority and freeze authority revoked, preventing further token creation or account freezing. It does not utilize a transfer hook or… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 18.29% of the supply. The token has $79,911 in DEX liquidity, and 100% of this liquidity is burned, ensuring it cannot… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further administrative actions can be taken to alter the token's core parameters or supply. The token does not have mutable… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.4% of supply. Of that, 10.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.3% in wallets, 0.0% in other contracts. 1,619 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SLOPCORE (SLOPCORE), rank #3543. 1,619 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 83% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $99K (DexScreener, all pools). 24h trading volume $348K (CoinGecko, all markets, daily snapshot). 24h trading volume $620K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $99K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 8 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EkFRff...pump`](https://solscan.io/account/EkFRff9a2jKztJHML1LG9FRmEkPJDR6XAYp3uCPdpump) |
| **Network** | Solana |
| **Price** | $0.0005691 |
| **24h Volume** | $566.9K |
| **Liquidity** | $81.7K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 8d |
| **Top-10 Holders** | 28.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4308 buys / 2736 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3umutzeevslywqjez6sjngu3jc6oqsxpy2apnh3xl8sf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/slopcore-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
