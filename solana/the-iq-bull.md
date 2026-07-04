---
token: The IQ Bull
ticker: AMEN
network: solana
risk_score: 40
status: medium
date: 2026-07-04
---

# The IQ Bull (AMEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-iq-bull-sol)

---

## Audit Summary

The audit of The IQ Bull (AMEN) token mint identified a medium risk related to the very recent creation of its DEX trading pair. Key authorities such as mint and freeze authorities are revoked, indicating a fixed supply and unfreezable accounts. Holder concentration data was unavailable, and RugCheck.xyz provided a score of 43/100 with risk labels, but not an explicit 'RUGGED' verdict.

> **Final Recommendation:** Given the very new DEX pair (1 day old), potential holders should exercise extreme caution. While core authorities like mint and freeze are revoked, the lack of historical data and unavailable holder concentration information present significant risks. It is recommended to monitor the token's trading activity and holder distribution for a longer period before making any substantial investment. Verify on-chain that the mint authority and freeze authority remain revoked. For a Premium Deploy, consider implementing additional on-chain checks for liquidity depth and age before allowing trading.

## Security Analysis

The audit of The IQ Bull (AMEN) token mint identified a medium risk related to the very recent creation of its DEX trading pair. Key authorities such as mint and freeze authorities are revoked, indicating a fixed supply and unfreezable accounts. Holder concentration data was unavailable, and RugCheck.xyz provided a score of 43/100 with risk labels, but not an explicit 'RUGGED' verdict.

Given the very new DEX pair (1 day old), potential holders should exercise extreme caution. While core authorities like mint and freeze are revoked, the lack of historical data and unavailable holder concentration information present significant risks. It is recommended to monitor the token's trading activity and holder distribution for a longer period before making any substantial investment. Verify on-chain that the mint authority and freeze authority remain revoked. For a Premium Deploy, consider implementing additional on-chain checks for liquidity depth and age before allowing trading.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is implemented using the spl-token-2022 program. Crucially, the mint authority and freeze authority are both revoked, ensuring that no new tokens can be minted and no holder accounts can be  |
| **Governance / Economics** | 5/10 | Medium | The token's DEX pair is very new, having been created only 1 day ago, which provides insufficient track record for assessing market behavior. Total DEX liquidity stands at $22,348, with a 24-hour volu |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply is fixed and no accounts can be frozen by an external party. The token does not utilize any Token-2022 extensions t |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 1 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Monitor the token's trading activity and holder distribution for a longer period before making any substantial investment.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CbdMt7...pump`](https://solscan.io/account/CbdMt7xCe91AiAwnqtiHpUB5QrR3Z3ZL3LqnKGSypump) |
| **Network** | Solana |
| **Price** | $0.00008364 |
| **24h Volume** | $112.9K |
| **Liquidity** | $22.7K |
| **Volume / Liquidity** | 5.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1204 buys / 1387 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/akydjym7sbevr88fm9qzq3bncj4s1oe7ibbzyhavc1cv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-iq-bull-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-04*
