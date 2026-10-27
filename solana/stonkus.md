---
token: STONKUS
ticker: STONKUS
network: solana
risk_score: 58
status: medium
date: 2026-10-27
---

# STONKUS (STONKUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stonkus-sol)

---

## Audit Summary

STONKUS is a Token-2022 asset with fully revoked mint and freeze authorities, mitigating central control risks. Liquidity is fully locked, providing a stable foundation for trading. Holder concentration data is unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should monitor the mutable metadata status to ensure branding remains consistent with expectations. Given the low liquidity, participants should execute trades in smaller sizes to minimize slippage impact.

Verify the current transfer fee on-chain before initiating large transactions, as the fee configuration is upgradable. No further action is required regarding authority control as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token implements a 100 bps… |
| **Governance / Economics** | 7/10 | Low | Total liquidity is $6,262, which is fully locked in a permanent locker (7.4 Economic). The 24h volume of $53,563 results in a volume/liquidity ratio of 8.55 (7.6 External). Holder concentration data… |
| **Upgrades** | 8/10 | Low | The mint and freeze authorities are permanently revoked, preventing further supply changes or account freezing (7.7 Upgrades). Metadata is mutable, allowing for potential updates to the token name or… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $6,262. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $47K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AABqYv...CdtQ`](https://solscan.io/account/AABqYvMM6Erf5snARQiHKwo1sgNh8UVeut6KJ6YeCdtQ) |
| **Network** | Solana |
| **Price** | $0.00000942 |
| **24h Volume** | $47.3K |
| **Liquidity** | $8.2K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 727 buys / 564 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/nyasj1ram5przanbynt79hwvvguezy8hwydmvlbrjnp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stonkus-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
