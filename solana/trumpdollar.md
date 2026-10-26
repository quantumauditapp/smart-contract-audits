---
token: TRUMPDOLLAR
ticker: TRUMPDOLLAR
network: solana
risk_score: 43
status: medium
date: 2026-10-26
---

# TRUMPDOLLAR (TRUMPDOLLAR) — Smart Contract Security Analysis | Solana

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/trumpdollar-sol)

---

## Audit Summary

TRUMPDOLLAR is a Token-2022 asset with both mint and freeze authorities successfully revoked. The token features a 3% transfer fee and mutable metadata, but maintains high security through fully locked liquidity. Third-party risk registry data was successfully retrieved and indicates no critical flags.

> **Final Recommendation:** Investors should account for the 3% transfer fee when calculating entry and exit points, as this cost is deducted from every transaction. Monitor the metadata for any unexpected changes, as the mutable flag allows for branding updates.

Verify the current transfer fee on-chain before executing large trades, as the fee configuration remains upgradable. No further action is required regarding liquidity, as the current lock provides sufficient protection against withdrawal risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program, which allows for advanced extensions. 7.1 Architecture and 7.3 Access Control are robust, as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance factors are influenced by a 300 bps (3%) transfer fee. Holder concentration is moderate, with the top 10 holders controlling 24.07% of the supply. Liquidity is healthy… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are limited to metadata and fee configuration. While metadata is mutable, the core token logic is immutable due to the revocation of authorities. 7.8 Operations remain transparent as the… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Raydium Lock |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the authority at any time.

**Recommendation:** Verify the token branding on official channels before interacting to ensure the metadata has not been altered.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee configuration is currently set to 300 bps (3%) and remains upgradable by the fee authority.

**Recommendation:** Periodically check the token's transfer fee extension state to ensure the fee has not been increased.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.6% of supply. Of that, 5.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.1% in wallets, 0.0% in other contracts. 441 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

441 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $82K (DexScreener, all pools). 24h trading volume $405K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $82K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5Aa378...NHRw`](https://solscan.io/account/5Aa378KvCX3bz2dJ3YncoXijBBVvgvipQAXHWaBNNHRw) |
| **Network** | Solana |
| **Price** | $0.0006865 |
| **24h Volume** | $404.6K |
| **Liquidity** | $82.1K |
| **Volume / Liquidity** | 4.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | 29.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2280 buys / 1791 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bqdaoudsea3qalijfxzbrdh4sjy9vymy29e7fvoefdh3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/trumpdollar-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
