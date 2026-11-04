---
token: Always Moist Downstairs
ticker: AMD
network: solana
risk_score: 2
status: low
date: 2026-11-04
---

# Always Moist Downstairs (AMD) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/always-moist-downstairs-sol)

---

## Audit Summary

The Always Moist Downstairs (AMD) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, third-party registry data flags concerns regarding holder concentration and developer history. Holder distribution data was unavailable via RPC, limiting the depth of concentration analysis.

> **Final Recommendation:** Investors should monitor the token's holder distribution once on-chain data becomes available to verify if concentration risks align with third-party registry warnings. Given the immutable nature of the mint, no further administrative actions can be taken by the developer.

Verify the mint address directly on a block explorer to confirm the 'Revoked' status of authorities before interacting. Exercise caution due to the 'Copycat token' and 'High holder concentration' flags reported by external registries.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance metrics show $53,125 in liquidity, which is 100% burned, preventing rug-pulls via liquidity withdrawal. 7.6 External signals indicate potential concentration risks and… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. Metadata is immutable (metadata_mutable: False), preventing branding changes. 7.8 Operations are stable as no authority-based… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history and holder concentration patterns.

**Recommendation:** Conduct independent due diligence on the project's origin and monitor for suspicious wallet activity.


### `L-01` — Holder Concentration Uncertainty  *(Severity: Low · Status: Unresolved)*

On-chain RPC data for holder distribution is currently unavailable, preventing verification of the concentration risks flagged by third-party registries.

**Recommendation:** Use block explorers to manually inspect the top 10 token accounts for signs of excessive supply concentration.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $51K (DexScreener, all pools). 24h trading volume $360K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $51K of DEX liquidity across 22 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HjiBij...pump`](https://solscan.io/account/HjiBij1BcEwjcgPEb22K8y7imdgaf1kHGMHuEgcDpump) |
| **Network** | Solana |
| **Price** | $0.0002531 |
| **24h Volume** | $309.4K |
| **Liquidity** | $46.3K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3155 buys / 2819 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5xnneo9rhcds4mrbtxkqdfjqhnd7oemhtgwa2jx7zbjb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/always-moist-downstairs-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
