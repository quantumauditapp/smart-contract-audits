---
token: BOYCOTTPUMPFUN
ticker: BPF
network: solana
risk_score: 48
status: medium
date: 2026-10-29
---

# BOYCOTTPUMPFUN (BPF) — Smart Contract Security Analysis | Solana

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/boycottpumpfun-sol-4248)

---

## Audit Summary

The BOYCOTTPUMPFUN token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, mitigating rug-pull risks, though metadata remains mutable. Holder concentration data is unavailable, and the transfer fee is set to 100 bps.

> **Final Recommendation:** Investors should monitor the mutable metadata and transfer fee settings, as these can be adjusted by the current owner of those specific extension authorities. Verify the current metadata on-chain before executing large trades.

Given the lack of holder concentration data, exercise caution regarding potential whale activity. Ensure all interactions occur through verified DEX interfaces to avoid malicious routing.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token includes a 100 bps… |
| **Governance / Economics** | 8/10 | Low | Liquidity is fully secured with 100% of pool funds locked in a permanent locker (7.4 Economic). Trading volume is active relative to liquidity, though holder concentration data is unavailable (7.5… |
| **Upgrades** | 8/10 | Low | The token metadata is mutable, allowing for potential branding changes (7.7 Upgrades). The transfer fee configuration is also marked as upgradable. No other upgradeable components exist for this mint. |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

The token metadata is mutable, allowing the name, symbol, or image to be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The metadata_mutable flag is set to True, permitting updates to token branding.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $100K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AWqjGV...W7QM`](https://solscan.io/account/AWqjGVukKcG79uPHm9FcBcbAHmApemZPZetzv69aW7QM) |
| **Network** | Solana |
| **Price** | $0.00003289 |
| **24h Volume** | $100.3K |
| **Liquidity** | $15.4K |
| **Volume / Liquidity** | 6.5× |
| **Token Age** | 12h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1304 buys / 902 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8a67xg1wkqupqjvljzeudrnpkivg7de4bjari7xvfdb4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/boycottpumpfun-sol-4248)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
