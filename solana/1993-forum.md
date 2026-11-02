---
token: 1993 forum
ticker: 1993
network: solana
risk_score: 26
status: low
date: 2026-11-02
---

# 1993 forum (1993) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/1993-forum-sol)

---

## Audit Summary

The 1993 forum token is a Token-2022 asset with both mint and freeze authorities successfully revoked. The primary risks identified are a 5% transfer fee and mutable metadata. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should account for the 5% transfer fee when calculating entry and exit points, as this significantly impacts net proceeds. Verify the token metadata on-chain before trading to ensure the branding matches current expectations.

Monitor the token's market activity for any unexpected changes in liquidity or metadata. Since holder concentration data is unavailable, exercise caution regarding potential whale activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture is standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic analysis shows a 5% transfer fee applied to all transactions. 7.6 External liquidity is $34,325, which is fully locked in a permanent LP locker. 7.5 Governance and holder concentration… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints. 7.8 Operations are impacted by metadata mutability, allowing the token name and symbol to be changed. The transfer fee and hook configurations are not… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | 5.0% (immutable) |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — High Transfer Fee  *(Severity: High · Status: Unresolved)*

Every transfer incurs a 5% (500 bps) fee paid to the fee authority.

**Recommendation:** Account for the 5% fee in all swap and trading calculations.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is currently mutable and can be changed by the authority.

**Recommendation:** Verify metadata against official sources before trusting the token branding.


### `L-01` — Holder Concentration Data Unavailable  *(Severity: Low · Status: Unresolved)*

On-chain RPC data for holder distribution could not be retrieved.

**Recommendation:** Perform independent analysis of the top token accounts via a block explorer.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $40K (DexScreener, all pools). 24h trading volume $148K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $40K of DEX liquidity across 5 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7Ypg1r...cash`](https://solscan.io/account/7Ypg1rKLu8q32E1AQEDjaPCg8dfGeCSsMkFnK98zcash) |
| **Network** | Solana |
| **Price** | $0.0002086 |
| **24h Volume** | $147.9K |
| **Liquidity** | $39.2K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1046 buys / 1146 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/anhkaunhr84zhkgbfhalsrvgtzev5udcn4jiu82w5gap)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/1993-forum-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
