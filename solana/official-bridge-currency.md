---
token: Official Bridge Currency
ticker: OBC
network: solana
risk_score: 72
status: critical
date: 2026-05-12
---

# Official Bridge Currency (OBC) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/official-bridge-currency-sol)

---

## Audit Summary

This report provides a security assessment of the Official Bridge Currency (OBC) SPL Token Mint account based on available on-chain metadata and external security signals. Source code for the underlying SPL Token Program is not subject to this review. Data completeness was limited for certain aspects, such as token supply, decimals, holder distribution, and RugCheck data, which impacts the comprehensiveness of the analysis. The primary finding is that the token mint account is uninitialized, preventing its intended functionality.

> **Final Recommendation:** The Official Bridge Currency (OBC) SPL Token Mint presents a critical technical flaw: it is uninitialized, rendering it non-functional. While the revocation of mint and freeze authorities and the immutability of key parameters are strong security positives, the fundamental uninitialized state must be addressed for the token to serve its intended purpose. Economic risks are present due to low liquidity and trading volume, but these are not direct security vulnerabilities of the program itself.

It is strongly recommended to initialize the mint account correctly to enable token functionality. For future deployments, consider a Premium Deploy option that includes a pre-deployment checklist and automated verification of critical account states to prevent such initialization issues.

## Security Analysis

This report provides a security assessment of the Official Bridge Currency (OBC) SPL Token Mint account based on available on-chain metadata and external security signals. Source code for the underlying SPL Token Program is not subject to this review. Data completeness was limited for certain aspects, such as token supply, decimals, holder distribution, and RugCheck data, which impacts the comprehensiveness of the analysis. The primary finding is that the token mint account is uninitialized, preventing its intended functionality.

The Official Bridge Currency (OBC) SPL Token Mint presents a critical technical flaw: it is uninitialized, rendering it non-functional. While the revocation of mint and freeze authorities and the immutability of key parameters are strong security positives, the fundamental uninitialized state must be addressed for the token to serve its intended purpose. Economic risks are present due to low liquidity and trading volume, but these are not direct security vulnerabilities of the program itself.

It is strongly recommended to initialize the mint account correctly to enable token functionality. For future deployments, consider a Premium Deploy option that includes a pre-deployment checklist and automated verification of critical account states to prevent such initialization issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical architecture (7.1 Architecture) of the OBC token mint benefits from the standard SPL Token Program, which is well-audited and robust. A significant strength in code security (7.2 Code Se |
| **Governance / Economics** | 6/10 | Medium | From an economic perspective (7.4 Economic), the token exhibits low liquidity ($4,603 USD) and daily trading volume ($118 USD), which could lead to price volatility and make large trades difficult. Go |
| **Upgrades** | 6/10 | Low | The program's upgradeability (7.7 Upgrades) is highly favorable for security and predictability. External security signals indicate that key parameters such as transfer fees, transfer hooks, and metad |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Uninitialized SPL Token Mint Account  *(Severity: High · Status: Unresolved)*

The SPL Token Mint account at address 2necwdgejstlv2yrfmsjtindwyvj7snnucqjwgc5ydk1 is marked as 'Initialized: False'. An uninitialized mint account cannot be used to create or manage tokens, as its essential properties like supply and decimals are not set. This prevents the token from functioning as intended within the Solana ecosystem.

**Recommendation:** The token mint account must be properly initialized using the `initialize_mint` instruction of the SPL Token Program. This will set the supply, decimals, and assign the mint authority, enabling the token to be used.


### `L-01` — Low Liquidity and Trading Volume  *(Severity: Low · Status: Unresolved)*

The token exhibits low liquidity ($4,603 USD) and 24-hour trading volume ($118 USD). While not a direct technical vulnerability, low liquidity can lead to significant price volatility and make it difficult for users to buy or sell substantial amounts of the token without impacting its market price. This poses an economic risk to holders.

**Recommendation:** To mitigate economic risk and improve market stability, strategies should be implemented to increase liquidity and foster organic trading activity. This could include incentivizing liquidity providers or promoting wider adoption and utility for the token.


### `I-01` — Limited Data Availability for Comprehensive Assessment  *(Severity: Informational · Status: Unresolved)*

Key data points, including the exact token supply, decimals (due to uninitialized state), holder distribution, and RugCheck analysis, were unavailable during the audit. This limitation restricts the ability to perform a complete risk assessment regarding tokenomics, centralization of holdings, and potential rug pull indicators.

**Recommendation:** For future audits or ongoing monitoring, efforts should be made to ensure all relevant on-chain data sources are accessible and complete. This includes successful RPC queries for all mint properties and integration with comprehensive analytics platforms.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2necwd...ydk1`](https://solscan.io/account/2necwdgejstlv2yrfmsjtindwyvj7snnucqjwgc5ydk1) |
| **Network** | Solana |
| **Price** | $0.002121 |
| **24h Volume** | $332.5K |
| **Liquidity** | $69.0K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 5d |
| **Top-10 Holders** | N/A of supply |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/drkhakh4eb7ncrs5odcowbvjcrasuazbtxvedezaaxkm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/official-bridge-currency-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*
