---
token: Stonka
ticker: STONKA
network: solana
risk_score: 20
status: low
date: 2026-11-07
---

# Stonka (STONKA) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonka-sol)

---

## Audit Summary

The Stonka token mint is configured with both mint and freeze authorities revoked, ensuring supply immutability and preventing account freezing. While liquidity is fully locked, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high volume-to-liquidity ratio reflects genuine market interest or artificial activity. Given the lack of holder distribution data, users should exercise caution regarding potential concentration risks.

Verify the current liquidity lock status periodically via on-chain explorers to ensure the LP tokens remain in the designated locker. No further on-chain actions are required to secure the token mint itself as authorities are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8 Operations are secure… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show $10,231 in liquidity, which is fully locked in a permanent LP locker. 7.5 Governance is decentralized due to revoked authorities. 7.6 External market data indicates a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, preventing unauthorized branding changes. The token configuration is static and cannot be modified by any party. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 27.91, which exceeds the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading volume; perform independent analysis of trade history to identify potential wash trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $282K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`76inp9...BJnp`](https://solscan.io/account/76inp9q4HxQUsGxEvxMhhjtx9DipbMrqssLQEcWABJnp) |
| **Network** | Solana |
| **Price** | $0.0000182 |
| **24h Volume** | $281.9K |
| **Liquidity** | $11.2K |
| **Volume / Liquidity** | 25.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3596 buys / 2259 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/awznmjrv3tkmvdjh4ellsarrksrpj8jkx7uanqccbda3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonka-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
