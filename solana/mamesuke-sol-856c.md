---
token: MAMESUKE
ticker: MAMESUKE
network: solana
risk_score: 8
status: low
date: 2026-11-02
---

# MAMESUKE (MAMESUKE) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-sol-856c)

---

## Audit Summary

The MAMESUKE token is a Token-2022 asset with both mint and freeze authorities successfully revoked. The primary identified risks are the mutability of token metadata and a third-party registry flag indicating that a large portion of liquidity remains unlocked. Holder concentration data was unavailable for this analysis.

> **Final Recommendation:** Investors should monitor the liquidity pool status to ensure that the unlocked LP is not withdrawn by the creator. Verify the token metadata on-chain before trading to ensure it matches the expected branding.

Users should remain cautious regarding the lack of holder distribution data and perform independent checks on block explorers to assess the concentration of supply among top accounts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default frozen… |
| **Governance / Economics** | 8/10 | Low | Liquidity is currently $393,714 with a healthy volume-to-liquidity ratio of 0.74 (7.4 Economic). However, a third-party registry flags that a large amount of LP is unlocked, posing a potential… |
| **Upgrades** | 9/10 | Low | The token metadata remains mutable, allowing for potential changes to the name or symbol (7.7 Upgrades). There are no other upgradeable components or proxy patterns (7.8 Operations). |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry indicates that a large amount of the pool's liquidity is unlocked and potentially withdrawable by the creator.

**Recommendation:** Verify the liquidity provider's wallet activity and confirm if the liquidity is moved to a time-locked contract or burned.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata is mutable, meaning the name, symbol, or image can be altered by the authority at any time.

**Recommendation:** Verify the token metadata against official sources before interacting with the asset.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $464K (DexScreener, all pools). 24h trading volume $2.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $464K of DEX liquidity across 10 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SCGBBn...STNK`](https://solscan.io/account/SCGBBnSwnekytGFHgyeHHxPMiN7xDxsWFGg9JgFSTNK) |
| **Network** | Solana |
| **Price** | $0.00106 |
| **24h Volume** | $262.6K |
| **Liquidity** | $358.8K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1948 buys / 1996 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/fmkswmdkwstg3jm6v5pkexe5lkcw3ny84qrhdcktc7a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-sol-856c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
