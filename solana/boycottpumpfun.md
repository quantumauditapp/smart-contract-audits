---
token: BOYCOTTPUMPFUN
ticker: BOYCOTT
network: solana
risk_score: 51
status: medium
date: 2026-10-25
---

# BOYCOTTPUMPFUN (BOYCOTT) — Smart Contract Security Analysis | Solana

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/boycottpumpfun-sol)

---

## Audit Summary

The token is built on the Token-2022 program with revoked mint and freeze authorities, providing basic supply security. However, the project is flagged as high-risk by a third-party registry due to developer history, and the trading data exhibits strong indicators of wash trading. Holder concentration data is unavailable.

> **Final Recommendation:** Investors should exercise extreme caution due to the third-party high-risk classification and suspicious trading volume. Monitor the token metadata for unexpected changes and verify the transfer fee configuration periodically on-chain.

Before interacting, verify the current transfer fee via the Token-2022 extension state and confirm that the metadata remains consistent with the project's stated branding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program with 7.1 Architecture standards. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis reveals a volume/liquidity ratio of 55.68, suggesting significant wash trading. 7.6 External signals indicate the project is flagged as high-risk by a third-party registry.… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to SPL mints, but 7.5 Governance is impacted by mutable metadata. The token name and symbol can be changed at any time. Additionally, the transfer fee is currently… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history.

**Recommendation:** Do not interact with this token.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume is 55.68x liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for potential liquidity manipulation when assessing market depth.


### `H-02` — High Transfer Fee  *(Severity: High · Status: Unresolved)*

Every transfer pays 1.00% (100 bps) to the fee authority.

**Recommendation:** Account for the fee in any swap calculation.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee configuration is marked as upgradable, allowing the fee authority to change the rate.

**Recommendation:** Monitor the transfer fee extension for unexpected increases.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 73% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4b7hUY...hvCR`](https://solscan.io/account/4b7hUYrtSjndqRwbc6PxMuXvSKZd8s7rkm66xSTshvCR) |
| **Network** | Solana |
| **Price** | $0.00005667 |
| **24h Volume** | $1.47M |
| **Liquidity** | $23.4K |
| **Volume / Liquidity** | 62.6× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13434 buys / 10218 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/czordzyr22h5kepcprldmvlhpgs8zkghu9cwddyrhobs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/boycottpumpfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
