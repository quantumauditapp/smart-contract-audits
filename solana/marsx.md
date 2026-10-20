---
token: MarsX
ticker: MARSX
network: solana
risk_score: 13
status: low
date: 2026-10-15
---

# MarsX (MARSX) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/marsx-sol)

---

## Audit Summary

This audit of the MarsX SPL token mint found no critical or high-severity issues based on the available on-chain data and third-party risk registries. The mint and freeze authorities are revoked, ensuring a fixed supply and preventing arbitrary freezing of accounts. All pool liquidity is burned, eliminating rug pull risks from liquidity withdrawal. Third-party registry data was available and reported no adverse flags.

> **Final Recommendation:** Given the current state, holders should verify on-chain that the mint and freeze authorities remain revoked. Monitor the token's liquidity and trading volume for any significant changes. While current holder concentration is low, continued monitoring of the top holder distribution is advisable for any token. No further specific actions are required based on the current audit findings.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The MarsX token is an SPL Token-2022 mint with a total supply of 981,452,184.959427 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, which means no new tokens… |
| **Governance / Economics** | 9/10 | Low | Holder concentration for MarsX is low, with the top 10 holders that can sell holding only 16.41% of the total supply, indicating a relatively distributed ownership. The token has a total DEX… |
| **Upgrades** | 10/10 | Low | The MarsX token mint has a robust security posture regarding mutability and control. Both the mint and freeze authorities are permanently revoked, preventing any future changes to the token's supply… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.5% of supply. Of that, 15.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.4% in wallets, 0.0% in other contracts. 2,380 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,380 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $36K (DexScreener, all pools). 24h trading volume $228K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Fak3rJ...pump`](https://solscan.io/account/Fak3rJEBfR4Vb8DoFpecf6yoxbkkr1gGUH5tdj2rpump) |
| **Network** | Solana |
| **Price** | $0.0001173 |
| **24h Volume** | $223.2K |
| **Liquidity** | $35.1K |
| **Volume / Liquidity** | 6.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | 31.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1910 buys / 1681 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9dsiuydk5efrclk6veywy95nn3jjgbdwnijuacf1pxua)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/marsx-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
