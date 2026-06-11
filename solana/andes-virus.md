---
token: Andes Virus
ticker: ANDV
network: solana
risk_score: 35
status: medium
date: 2026-06-10
---

# Andes Virus (ANDV) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/andes-virus-sol)

---

## Audit Summary

This audit of the Andes Virus (ANDV) SPL Token Mint found no critical or high-severity issues based on the provided on-chain data and external security signals. Both the mint and freeze authorities have been revoked, indicating a fixed supply and no ability to freeze user accounts. Holder concentration data was unavailable, which is a common limitation for new tokens.

> **Final Recommendation:** Based on the available data, the Andes Virus (ANDV) token mint appears to be well-configured with critical authorities revoked, indicating a fixed supply and no ability to freeze user funds. Investors should be aware that holder concentration data was unavailable, which can be a risk factor for price volatility. Before making any investment decisions, consider the implications of the current liquidity and pair age. For a Premium Deploy option, ensure continuous monitoring of on-chain activity and any future changes to the token's ecosystem.

## Security Analysis

This audit of the Andes Virus (ANDV) SPL Token Mint found no critical or high-severity issues based on the provided on-chain data and external security signals. Both the mint and freeze authorities have been revoked, indicating a fixed supply and no ability to freeze user accounts. Holder concentration data was unavailable, which is a common limitation for new tokens.

Based on the available data, the Andes Virus (ANDV) token mint appears to be well-configured with critical authorities revoked, indicating a fixed supply and no ability to freeze user funds. Investors should be aware that holder concentration data was unavailable, which can be a risk factor for price volatility. Before making any investment decisions, consider the implications of the current liquidity and pair age. For a Premium Deploy option, ensure continuous monitoring of on-chain activity and any future changes to the token's ecosystem.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, 7.8 Operations: The Andes Virus (ANDV) token is an SPL Token-2022 mint on Solana. A key security strength is that both the Mint Authority and F |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic: The token exhibits moderate liquidity with $26,762 USD available on DEXs. The 24-hour trading volume is $8,996, resulting in a healthy Volume/Liquidity Ratio of 0.34, which does not sugg |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The token's core parameters, such as total supply and freeze capability, are immutable due to the revocation of both Mint and Freeze Authorities. No Token-2022 extensions like Transfer H |

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
| **Contract** | [`jvKtLF...pump`](https://solscan.io/account/jvKtLFLnNGPM7edS9KEpYqPxuY8HPGTZohLFM4Spump) |
| **Network** | Solana |
| **Price** | $0.0004631 |
| **24h Volume** | $189.8K |
| **Liquidity** | $67.6K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 7d |
| **Top-10 Holders** | 42.0% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/jhmcrrlmpte1qvypwe1yjtjzm2k44eorpducj6j8pwc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/andes-virus-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
