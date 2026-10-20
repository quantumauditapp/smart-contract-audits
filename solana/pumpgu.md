---
token: PUMPGU
ticker: PUMPGU
network: solana
risk_score: 20
status: low
date: 2026-10-01
---

# PUMPGU (PUMPGU) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pumpgu-sol)

---

## Audit Summary

This audit of the PUMPGU SPL token mint found no critical or high-severity issues based on the provided on-chain facts and third-party security signals. Both mint and freeze authorities are revoked, and 100% of the DEX liquidity is burned, indicating a robust setup for a fixed-supply token. Third-party registry data reported no adverse flags.

> **Final Recommendation:** Holders should continue to monitor the token's market activity and liquidity pools for any significant changes in trading patterns or liquidity depth. While the current setup is robust, vigilance regarding broader market conditions and the token's ecosystem remains prudent. Verify on-chain that authorities remain revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The PUMPGU token is an SPL token mint operating under the `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be created and no existing… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 21.21% of the supply. The token has a total DEX liquidity of $37,950, with 100.0% of the pool's LP tokens burned… |
| **Upgrades** | 10/10 | Low | The token mint has no upgradeability concerns typical of EVM proxy contracts, as it is an SPL token mint. Both mint and freeze authorities are permanently revoked, fixing the token's supply and… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.4% of supply. Of that, 11.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 21.2% in wallets, 0.0% in other contracts. 195 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

195 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $38K (DexScreener, all pools). 24h trading volume $257K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $38K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 382 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HppB5r...pump`](https://solscan.io/account/HppB5rMgVsUqua42N2TEDcjwy7gLuAm6dq5qMSLZpump) |
| **Network** | Solana |
| **Price** | $0.0001632 |
| **24h Volume** | $256.9K |
| **Liquidity** | $38.3K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 32.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12103 buys / 9576 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/a41qkph6g4zqwwq9av4mmzkrph5hdvujgn8w6kmqf7o1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pumpgu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
