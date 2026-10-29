---
token: Grand Theft Auto VI -Vicecity
ticker: VICECITY
network: solana
risk_score: 44
status: medium
date: 2026-10-29
---

# Grand Theft Auto VI -Vicecity (VICECITY) — Smart Contract Security Analysis | Solana

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-vicecity-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, mitigating primary centralization risks. Liquidity is fully locked, and the protocol exhibits standard trading behavior. Holder concentration data was unavailable from the registry, preventing a full assessment of distribution risks.

> **Final Recommendation:** Investors should monitor the transfer fee authority, as it retains the ability to adjust the 1% fee rate. Verify the token metadata periodically to ensure it aligns with the original project branding, as the metadata remains mutable.

Given the lack of holder distribution data, users should exercise caution regarding potential whale concentration. Always verify the current liquidity lock status on-chain before committing significant capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is deployed via the Token-2022 program, incorporating a 1% transfer fee (100 bps). 7.1 Architecture and 7.2 Code Security are standard for SPL-2022 assets. 7.3 Access Control is robust as… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show $20,544 in liquidity, which is fully locked in a permanent LP locker. 7.5 Governance is decentralized due to authority revocation. 7.6 External signals indicate low… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are limited by the revocation of mint and freeze authorities. However, the transfer fee remains upgradable, allowing the fee authority to modify the 1% rate. Metadata is currently… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Transfer Fee Upgradable  *(Severity: Medium · Status: Unresolved)*

The 1% transfer fee is marked as upgradable, allowing the fee authority to modify the rate at any time.

**Recommendation:** Monitor the fee authority for any unexpected changes to the transfer fee structure.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, allowing the issuer to change branding post-launch.

**Recommendation:** Verify the token metadata against official project channels before interacting.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $14K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`25NVbD...32Tm`](https://solscan.io/account/25NVbDfwuAVhb2XADxGCs6WQuPjU1RsgDfUG6GV132Tm) |
| **Network** | Solana |
| **Price** | $0.00003269 |
| **24h Volume** | $39.2K |
| **Liquidity** | $14.5K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 359 buys / 286 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5exm58qjprwwpqalkqzjjajwymzqbtxaejrbtaxgpq19)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grand-theft-auto-vi-vicecity-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
