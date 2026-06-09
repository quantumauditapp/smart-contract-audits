---
token: Andes Virus
ticker: ANDV
network: solana
risk_score: 90
status: critical
date: 2026-05-14
---

# Andes Virus (ANDV) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/andes-virus-sol)

---

## Audit Summary

This report details a security audit of the Andes Virus (ANDV) SPL Token Mint account on the Solana blockchain. The analysis is based on on-chain metadata and publicly available liquidity data, as source code for SPL Token Mints is not applicable. Key findings include the critical issue of the mint account being uninitialized, rendering the token non-functional, and a lack of transparency regarding holder distribution and external security signals. While the mint and freeze authorities are revoked, which is a positive security measure, the fundamental uninitialized state poses a significant barrier to usability. Due to the metadata-driven nature of this audit, certain deeper technical and economic analyses were limited by data availability.

> **Final Recommendation:** The Andes Virus (ANDV) token mint account is currently in a non-functional state due to being uninitialized. This critical issue must be addressed immediately for the token to become usable. While the revocation of mint and freeze authorities is a positive security practice, it is overshadowed by the fundamental setup error. Addressing the initialization, improving transparency around holder distribution, and seeking external security signal integration are crucial next steps.

## Security Analysis

This report details a security audit of the Andes Virus (ANDV) SPL Token Mint account on the Solana blockchain. The analysis is based on on-chain metadata and publicly available liquidity data, as source code for SPL Token Mints is not applicable. Key findings include the critical issue of the mint account being uninitialized, rendering the token non-functional, and a lack of transparency regarding holder distribution and external security signals. While the mint and freeze authorities are revoked, which is a positive security measure, the fundamental uninitialized state poses a significant barrier to usability. Due to the metadata-driven nature of this audit, certain deeper technical and economic analyses were limited by data availability.

The Andes Virus (ANDV) token mint account is currently in a non-functional state due to being uninitialized. This critical issue must be addressed immediately for the token to become usable. While the revocation of mint and freeze authorities is a positive security practice, it is overshadowed by the fundamental setup error. Addressing the initialization, improving transparency around holder distribution, and seeking external security signal integration are crucial next steps.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture & 7.2 Code Security: The primary technical concern is that the SPL Token Mint account is reported as 'Initialized: False'. This critical state means the token cannot function as inten |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic & 7.5 Governance: The token exhibits a normal Volume/Liquidity Ratio of 0.05, indicating healthy trading activity relative to its liquidity of $28,885 over its 34-day pair age. However, a |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The mint authority for the Andes Virus (ANDV) token has been revoked. This is a strong security measure that prevents any further changes to the token's core properties, such as minting  |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account `jvktlflnngpm7eds9kepyqpxuy8hpgtzohlfm4spump` is reported as `Initialized: False`. An uninitialized mint account cannot be used to mint tokens, set decimals, or track supply, rendering the token completely non-functional and unusable within the Solana ecosystem.

**Recommendation:** The mint account must be properly initialized using the `initialize_mint` instruction of the SPL Token Program. This instruction requires specifying the number of decimals, the mint authority, and optionally the freeze authority. Until initialized, the token cannot be utilized.


### `H-01` — Unknown Decimals and Supply  *(Severity: High · Status: Unresolved)*

As a direct consequence of the mint account being uninitialized, the number of decimals and the total supply of the token are reported as `unknown`. This lack of fundamental token information prevents users from understanding the token's divisibility and total issuance, which is critical for its utility, market valuation, and trust.

**Recommendation:** Ensure the mint account is correctly initialized. Once initialized, the decimals will be defined, and the supply will be accurately tracked by the SPL Token Program as tokens are minted or burned, providing essential transparency to users.


### `M-01` — Lack of Transparency in Holder Distribution  *(Severity: Medium · Status: Unresolved)*

Information regarding the holder concentration for the Andes Virus (ANDV) token is unavailable. This lack of transparency makes it impossible for potential investors and users to assess the distribution of the token, identify potential whale concentrations, or evaluate the risk of price manipulation by a few large holders.

**Recommendation:** While not a direct program vulnerability, the project should integrate with or provide data to services that offer on-chain holder distribution analytics. This would enhance transparency and allow for better-informed decisions by the community.


### `L-01` — Absence of External Security Signal Integration  *(Severity: Low · Status: Unresolved)*

External security signals from reputable services like GoPlus Solana and RugCheck are unavailable for the Andes Virus (ANDV) token. These services provide automated risk assessments and flag common scam indicators or vulnerabilities, and their absence means that standard external due diligence checks cannot be performed, potentially leaving users unaware of common market risks.

**Recommendation:** The project should aim to be listed and evaluated by reputable third-party security signal providers. This would build trust within the community and provide more comprehensive risk information to potential participants, aiding in their due diligence process.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`jvktlf...pump`](https://solscan.io/account/jvktlflnngpm7eds9kepyqpxuy8hpgtzohlfm4spump) |
| **Network** | Solana |
| **Price** | $0.0004631 |
| **24h Volume** | $189.8K |
| **Liquidity** | $67.6K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 7d |
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

- [View on DexScreener](https://dexscreener.com/solana/jhmcrrlmpte1qvypwe1yjtjzm2k44eorpducj6j8pwc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/andes-virus-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-14*
