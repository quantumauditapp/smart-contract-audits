---
token: Solstice
ticker: SLX
network: solana
risk_score: 90
status: critical
date: 2026-06-01
---

# Solstice (SLX) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/solstice-sol)

---

## Audit Summary

This report provides a security assessment of the Solstice (SLX) SPL Token Mint account based on available on-chain metadata. Critical functional issues were identified, including the mint being uninitialized and its owning token program being unknown. While mint and freeze authorities are revoked, these controls are moot given the uninitialized state. Economic data shows moderate liquidity and volume, but crucial information regarding holder distribution and external security signals is unavailable, limiting a comprehensive risk assessment.

> **Final Recommendation:** The Solstice (SLX) SPL Token Mint account is currently in a non-functional state due to being uninitialized and having an unknown owning token program. These are critical issues that prevent the token from being used as a standard SPL token. It is imperative to address these foundational problems before any further development or deployment. Without resolution, the token cannot be minted, transferred, or utilized within the Solana ecosystem. 

For future deployments, consider a Premium Deploy option that includes a pre-deployment audit of the token's configuration and initialization process to ensure all critical parameters are correctly set and verified on-chain, mitigating such fundamental risks.

## Security Analysis

This report provides a security assessment of the Solstice (SLX) SPL Token Mint account based on available on-chain metadata. Critical functional issues were identified, including the mint being uninitialized and its owning token program being unknown. While mint and freeze authorities are revoked, these controls are moot given the uninitialized state. Economic data shows moderate liquidity and volume, but crucial information regarding holder distribution and external security signals is unavailable, limiting a comprehensive risk assessment.

The Solstice (SLX) SPL Token Mint account is currently in a non-functional state due to being uninitialized and having an unknown owning token program. These are critical issues that prevent the token from being used as a standard SPL token. It is imperative to address these foundational problems before any further development or deployment. Without resolution, the token cannot be minted, transferred, or utilized within the Solana ecosystem. 

For future deployments, consider a Premium Deploy option that includes a pre-deployment audit of the token's configuration and initialization process to ensure all critical parameters are correctly set and verified on-chain, mitigating such fundamental risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture and 7.2 Code Security reveal significant technical deficiencies. The SPL Token Mint is marked as 'Initialized: False', rendering it non-functional and preventing any token operations. |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic and 7.5 Governance aspects present a mixed picture. The token exhibits a healthy Volume/Liquidity Ratio of 0.08 over its 15-day pair age, with $100,281 in liquidity and $8,011 in 24h volu |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades are not directly applicable to an SPL Token Mint account, which is a data structure managed by the SPL Token Program. The underlying SPL Token Program itself is upgradeable, but the mint  |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 2 Low_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account for Solstice (SLX) is marked as 'Initialized: False'. An uninitialized mint cannot be used to create or manage tokens, rendering the token completely non-functional. This prevents any minting, burning, or transfer operations, making the token unusable.

**Recommendation:** The token mint must be properly initialized using the SPL Token Program's `initialize_mint` instruction. This will set the supply, decimals, and other critical parameters, enabling the token to function as intended.


### `H-01` — Unknown Token Program Ownership  *(Severity: High · Status: Unresolved)*

The 'Token Program' associated with this mint is listed as 'unknown'. For a standard SPL token, this should be the well-known SPL Token Program (TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA). An unknown program owner raises significant concerns about the token's legitimacy, security, and adherence to Solana's token standards, potentially indicating a custom or misconfigured implementation without transparency.

**Recommendation:** Verify and confirm that the mint account is owned by the official SPL Token Program or a known, audited custom token program. If it's a custom program, its source code must be made available for a thorough security review.


### `M-01` — Missing Core Token Metadata  *(Severity: Medium · Status: Unresolved)*

Fundamental token metadata, specifically 'Supply (raw): unknown' and 'Decimals: unknown', is not available. This is a direct consequence of the mint being uninitialized and/or the unknown token program. Without these details, users and applications cannot correctly interact with or display information about the token.

**Recommendation:** Ensure the token mint is correctly initialized, which will populate the supply and decimals fields. This information is crucial for token usability and integration across the Solana ecosystem.


### `L-01` — Lack of Holder Distribution Data  *(Severity: Low · Status: Unresolved)*

Information regarding holder concentration is 'unavailable'. The absence of this data prevents an assessment of potential centralization risks, such as a few large holders controlling a significant portion of the supply, which could lead to market manipulation or governance issues if the token were functional and had governance implications.

**Recommendation:** Implement or integrate with tools that provide transparent holder distribution data. This information is vital for community trust and assessing the decentralization of token ownership.


### `L-02` — Absence of External Security Signals  *(Severity: Low · Status: Unresolved)*

External security signals from reputable services like GoPlus Solana and RugCheck are 'unavailable'. These services provide valuable insights into potential scam indicators, contract risks, and liquidity health. Their absence means that potential red flags or security assurances cannot be independently verified.

**Recommendation:** Ensure integration with and reporting from established security auditing and monitoring services. This provides an additional layer of trust and transparency for the token and its ecosystem.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`slxdx4...rfgq`](https://solscan.io/account/slxdx4but2v9ujqnzwqsfztj9ukludsvxhfmeedrfgq) |
| **Network** | Solana |
| **Price** | $0.4214 |
| **24h Volume** | $521.6K |
| **Liquidity** | $203.3K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 6d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2275 buys / 2192 sells |

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

## Frequently Asked Questions

### Is Solstice a scam?

Based on the provided data, Solstice (SLX) exhibits multiple critical risk factors often associated with fraudulent schemes, culminating in a 72/100 Critical Risk score. The lack of contract verification, unrenounced ownership, and unlocked liquidity are significant indicators of potential malicious intent or severe vulnerability. While these factors don't definitively label it a scam, they strongly advise against investment due to the high probability of financial loss.

### Is Solstice safe to buy?

No, Solstice (SLX) is assessed as critically unsafe for investment, reflected by its 72/100 risk score. The contract's unverified status means its code is unknown and unauditable, while unrenounced ownership allows the developer to retain full control. Crucially, the liquidity pool is not locked, exposing investor funds to potential removal by the owner (a rug pull). These fundamental risks make Solstice a highly speculative and dangerous asset.

### Has Solstice been audited?

There is no indication of a security audit for Solstice (SLX). Furthermore, the contract code is not verified on the blockchain. This means the underlying code is opaque and has not been publicly confirmed or reviewed by independent parties. Without verification, a professional audit is practically impossible, leaving investors with no transparency regarding the contract's safety or functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/sgo6ropnwxzutdhkbejkxvyuvwycgwzh5hgx6w6pxhh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/solstice-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-01*
