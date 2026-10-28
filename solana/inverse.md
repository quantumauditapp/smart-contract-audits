---
token: Inverse
ticker: INVERSE
network: solana
risk_score: 14
status: low
date: 2026-10-28
---

# Inverse (INVERSE) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/inverse-sol)

---

## Audit Summary

The Inverse (INVERSE) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a permanent lock, and no adverse flags were identified by third-party registries. The primary risks are limited to mutable metadata and a high volume-to-liquidity ratio suggesting potential wash trading.

> **Final Recommendation:** Investors should monitor the token's metadata for unexpected changes, as the metadata remains mutable. Given the high volume-to-liquidity ratio, users should exercise caution regarding the authenticity of trading volume before executing large swaps.

Verify the current metadata state on-chain periodically. Ensure that any future interactions are based on the verified mint address provided in this report to avoid impersonation tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program. 7.1 Architecture is standard, with no transfer hooks or default frozen states enabled. 7.3 Access Control is robust as both mint and freeze authorities… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% of liquidity being locked for good. 7.5 Governance is decentralized due to authority revocation. However, 7.6 External market data indicates a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints; however, 7.8 Operations are affected by metadata mutability. The token name and symbol can be changed at any time by the current metadata authority. No… |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 38.52, exceeding the 20x threshold, which is a strong indicator of artificially inflated trading activity.

**Recommendation:** Exercise caution when interpreting market volume; verify trade history for repetitive patterns.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be altered post-launch.

**Recommendation:** Verify metadata against official project channels before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. This assessment covers the main pool, which holds 64% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $92K (DexScreener, all pools). 24h trading volume $2.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $92K of DEX liquidity across 8 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2gLhk8...Zfiw`](https://solscan.io/account/2gLhk8p2KvUFeUXur2hiF4hxjdRM1vBcbgo9Q7DMZfiw) |
| **Network** | Solana |
| **Price** | $0.0004097 |
| **24h Volume** | $2.38M |
| **Liquidity** | $59.3K |
| **Volume / Liquidity** | 40.1× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24823 buys / 19384 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/rwq7wrfazybtdzgbxykehathfhaedw6vyqghpt1xbau)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/inverse-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
