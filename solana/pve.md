---
token: PVE
ticker: PVE
network: solana
risk_score: 70
status: high
date: 2026-10-22
---

# PVE (PVE) — Smart Contract Security Analysis | Solana

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pve-sol)

---

## Audit Summary

The PVE token utilizes the Token-2022 program with a revoked freeze authority, providing basic security for holders. However, the mint authority remains active, allowing for potential supply inflation, and the token exhibits strong indicators of wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the mint authority address for any activity, as the current configuration allows for unlimited token issuance. Given the high volume/liquidity ratio, exercise caution regarding the token's market price, as it may not reflect genuine demand.

Verify the current supply on-chain regularly to ensure no unauthorized minting has occurred. Avoid large positions until the mint authority is revoked, as the current state allows the holder of the mint key to dilute all existing holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is deployed via the Token-2022 program (7.1 Architecture). Access control is partially secured as the freeze authority is revoked (7.3 Access Control). However, the mint authority remains… |
| **Governance / Economics** | 6/10 | Medium | Liquidity is $19,090, with 95.5% of the pool locked, ensuring the majority of liquidity cannot be withdrawn (7.4 Economic). The volume/liquidity ratio of 92.93 indicates significant wash-trading… |
| **Upgrades** | 6/10 | Medium | Metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). The token program configuration is fixed, with no upgradable hooks or fees (7.7 Upgrades). Operations are limited to… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 6 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 6zWs8f9rMde2CyA6hbsWGwwHnkZzgRNiQ5ZZH25oGPkV. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 92.93x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the potential lack of genuine liquidity in any swap calculation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

95.6% of the pool's LP is burned or time-locked. 95.6% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 4.2% is held, unlocked, by 2 address(es) other than the pool's creator. This assessment covers the main pool, which holds 77% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $2.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 6 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EVQtaC...o6ea`](https://solscan.io/account/EVQtaC7JhakRZr4deKv8nbhqs9YaRt3eVDxt6DyQo6ea) |
| **Network** | Solana |
| **Price** | $0.0000411 |
| **24h Volume** | $2.13M |
| **Liquidity** | $19.7K |
| **Volume / Liquidity** | 108.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9553 buys / 8264 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/9czqzshhhtbjyzkdvjer3bdbumpooek4qqp9aw22tzeo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pve-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
