---
token: Lab
ticker: LAB
network: solana
risk_score: 1
status: low
date: 2026-10-26
---

# Lab (LAB) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lab-sol)

---

## Audit Summary

The Lab (LAB) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a permanent lock, mitigating rug-pull risks associated with pool withdrawal. Holder concentration data is unavailable, and metadata remains mutable, which should be monitored by potential participants.

> **Final Recommendation:** Investors should monitor the token's metadata for any unexpected changes, as the mutable flag allows for branding updates. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity and verify liquidity lock status periodically through on-chain explorers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply stability and preventing account freezing (7.3 Access Control). No… |
| **Governance / Economics** | 10/10 | Low | Liquidity is fully locked (100%) in a third-party locker, preventing creator withdrawal (7.4 Economic). Trading volume is active with a ratio of 7.51, though the pair is new (7.8 Operations). Holder… |
| **Upgrades** | 10/10 | Low | The mint has no upgradeable logic (7.7 Upgrades). Metadata is currently mutable, allowing for potential changes to the token name or symbol (7.6 External). |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is currently mutable, meaning it can be altered by the owner at any time.

**Recommendation:** Verify the token metadata against official project channels before interacting with the asset.


### `L-01` — Holder Concentration Data Unavailable  *(Severity: Low · Status: Unresolved)*

Current on-chain data does not provide a breakdown of holder distribution, preventing an assessment of supply concentration.

**Recommendation:** Monitor large wallet movements on-chain to identify potential concentration risks.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 88% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $85K (DexScreener, all pools). 24h trading volume $454K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $85K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BEwvuL...2zL1`](https://solscan.io/account/BEwvuL9EsEukMbETMcgRDJ2MVvVjTyEz4SAUxLuh2zL1) |
| **Network** | Solana |
| **Price** | $0.0003518 |
| **24h Volume** | $439.2K |
| **Liquidity** | $74.8K |
| **Volume / Liquidity** | 5.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4941 buys / 3292 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8gc4vywxq5jdz26oh1t9eekenjpjcyeyt2xkbpcnau38)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lab-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
