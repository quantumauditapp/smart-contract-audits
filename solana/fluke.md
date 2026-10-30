---
token: Fluke
ticker: FLUKE
network: solana
risk_score: 22
status: low
date: 2026-10-30
---

# Fluke (FLUKE) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fluke-sol)

---

## Audit Summary

The Fluke (FLUKE) token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While the liquidity is fully locked, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high volume-to-liquidity ratio persists, as this may indicate artificial market activity. Verify the current supply and holder distribution via a block explorer to ensure the token's distribution aligns with expectations.

Regularly check the on-chain mint and freeze authority status to confirm they remain revoked. No further administrative actions are required as the contract is immutable and liquidity is secured.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing is possible (7.3… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully locked in a Raydium LP locker, preventing creator withdrawal (7.4 Economic). However, the 24h volume-to-liquidity ratio of 20.79 indicates suspicious trading patterns (7.8… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable extensions or proxy-like mechanisms present. The token state is fixed and cannot be… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 20.79, which exceeds the threshold of 20, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive or non-organic patterns.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $33K (DexScreener, all pools). 24h trading volume $615K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $33K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`C31uUc...ZVUQ`](https://solscan.io/account/C31uUcfLGPpQDHHieNtDkSWvp4PhNxeSs81cFQFdZVUQ) |
| **Network** | Solana |
| **Price** | $0.0001385 |
| **24h Volume** | $614.9K |
| **Liquidity** | $32.6K |
| **Volume / Liquidity** | 18.9× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6650 buys / 6876 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2pzngxgxhhlgwpblwykbkitg6mm7jomgd57y4e8bresw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fluke-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
