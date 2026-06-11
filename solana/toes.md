---
token: TOES
ticker: TOESCOIN
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# TOES (TOESCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/toes-sol)

---

## Audit Summary

The TOES (TOESCOIN) SPL Token Mint on Solana has its mint and freeze authorities revoked, indicating a fixed supply and no ability to freeze user accounts. No Token-2022 extensions like transfer hooks or permanent delegates are active. While RugCheck.xyz reports a score of 30/100 with 'High holder correlation' as a risk label, no critical or high-severity issues were identified based on the deterministic audit rules. Holder concentration data was unavailable.

> **Final Recommendation:** Based on the available on-chain data and external security signals, the TOES (TOESCOIN) token mint appears to be well-configured with revoked authorities, indicating a fixed supply and no ability to freeze accounts. Holders should be aware that holder concentration data was unavailable, and RugCheck.xyz noted 'High holder correlation' as a risk label, which could imply potential market manipulation risks. For a premium deployment, consider integrating real-time monitoring for holder distribution changes and liquidity pool health.

## Security Analysis

The TOES (TOESCOIN) SPL Token Mint on Solana has its mint and freeze authorities revoked, indicating a fixed supply and no ability to freeze user accounts. No Token-2022 extensions like transfer hooks or permanent delegates are active. While RugCheck.xyz reports a score of 30/100 with 'High holder correlation' as a risk label, no critical or high-severity issues were identified based on the deterministic audit rules. Holder concentration data was unavailable.

Based on the available on-chain data and external security signals, the TOES (TOESCOIN) token mint appears to be well-configured with revoked authorities, indicating a fixed supply and no ability to freeze accounts. Holders should be aware that holder concentration data was unavailable, and RugCheck.xyz noted 'High holder correlation' as a risk label, which could imply potential market manipulation risks. For a premium deployment, consider integrating real-time monitoring for holder distribution changes and liquidity pool health.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The TOES (TOESCOIN) token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority are revoked (None), ensuring that no new tokens can be minted and no existing to |
| **Governance / Economics** | 6/10 | Low | The token exhibits a healthy liquidity of $290,660 USD with a 24-hour volume of $1,271,176 USD, resulting in a normal Volume/Liquidity Ratio of 4.37. The DEX pair has been active for 22 days, providin |
| **Upgrades** | 6/10 | Low | The mint authority and freeze authority are both revoked (None), meaning the token's supply and account freezing capabilities are immutable. The token is built on the spl-token-2022 program but does n |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6ehEcT...pump`](https://solscan.io/account/6ehEcTMCc85aNF4x9CWx8HuvWGhxQtvKdhKVf2HDpump) |
| **Network** | Solana |
| **Price** | $0.007238 |
| **24h Volume** | $1.07M |
| **Liquidity** | $229.9K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 9d |
| **Top-10 Holders** | 16.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

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

- [View on DexScreener](https://dexscreener.com/solana/ee3zk9fxp9guair2xerefxf4tsexezffuwetrna2pkcv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/toes-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
