---
token: Bullish Degen
ticker: BULLISH
network: solana
risk_score: 95
status: critical
date: 2026-05-14
---

# Bullish Degen (BULLISH) — Smart Contract Security Analysis | Solana

> **Risk Score: 95/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bullish-degen-sol)

---

## Audit Summary

This report provides a security analysis of the Bullish Degen (BULLISH) SPL Token Mint account based on on-chain metadata. The analysis reveals critical issues, primarily that the token mint is uninitialized and associated with an unknown token program, rendering it non-functional and highly risky. While liquidity is reported, the underlying technical state makes any economic activity impossible or highly precarious. The audit is limited to available on-chain data and does not include source code review.

> **Final Recommendation:** The Bullish Degen (BULLISH) SPL Token Mint presents critical security and functionality risks due to its uninitialized state and association with an unknown token program. Any interaction with this token is strongly discouraged as it is fundamentally non-functional and potentially malicious. Users should exercise extreme caution and avoid purchasing or holding this token.

For projects aiming for robust and secure token deployments, a 'Premium Deploy' option is recommended. This includes a comprehensive pre-deployment audit of the token program's source code, rigorous on-chain validation post-deployment, and continuous monitoring. Such a service ensures all critical parameters, like initialization and program association, are correctly configured and verified, mitigating the severe issues observed in this token.

## Security Analysis

This report provides a security analysis of the Bullish Degen (BULLISH) SPL Token Mint account based on on-chain metadata. The analysis reveals critical issues, primarily that the token mint is uninitialized and associated with an unknown token program, rendering it non-functional and highly risky. While liquidity is reported, the underlying technical state makes any economic activity impossible or highly precarious. The audit is limited to available on-chain data and does not include source code review.

The Bullish Degen (BULLISH) SPL Token Mint presents critical security and functionality risks due to its uninitialized state and association with an unknown token program. Any interaction with this token is strongly discouraged as it is fundamentally non-functional and potentially malicious. Users should exercise extreme caution and avoid purchasing or holding this token.

For projects aiming for robust and secure token deployments, a 'Premium Deploy' option is recommended. This includes a comprehensive pre-deployment audit of the token program's source code, rigorous on-chain validation post-deployment, and continuous monitoring. Such a service ensures all critical parameters, like initialization and program association, are correctly configured and verified, mitigating the severe issues observed in this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical analysis (7.2 Code Security, 7.3 Access Control) reveals critical flaws: the SPL Token Mint is marked as 'Initialized: False', meaning it cannot function to mint or manage tokens, and it |
| **Governance / Economics** | 6/10 | High | Despite reported liquidity of $64,398 and a 24h volume of $62,074 (7.4 Economic), these metrics are highly misleading given the token's uninitialized state. An uninitialized token cannot be properly t |
| **Upgrades** | 6/10 | Low | SPL Token Mint accounts are not directly upgradeable (7.7 Upgrades). The underlying SPL Token Program is managed and upgradeable by Solana Labs, ensuring its core functionality is maintained by the So |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at `c2omvhcvt3ddy77s2kzzawfjqeetzofgz4enwwkxpump` is reported as 'Initialized: False'. An uninitialized mint account cannot be used to create, transfer, or manage tokens. This means no tokens can be minted, the supply and decimals are unknown, and the token is effectively non-functional. Any reported liquidity or trading volume for an uninitialized token is highly misleading and represents a significant risk to users attempting to interact with it.

**Recommendation:** The token mint account must be properly initialized using the SPL Token Program's `initialize_mint` instruction. Without proper initialization, the token is unusable. If this was an intentional state for a specific purpose, it should be clearly communicated; otherwise, it represents a critical failure in deployment.


### `H-01` — Unknown Token Program Association  *(Severity: High · Status: Unresolved)*

The 'Token Program' associated with the mint account is listed as 'unknown'. Standard SPL tokens are managed by the official `TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA` program. An unknown program implies that this account might not be a standard SPL token mint, or it is associated with a custom, potentially unaudited, or malicious program. This introduces significant uncertainty regarding the account's true nature and functionality, posing a high security risk.

**Recommendation:** Verify the program ID associated with this mint account. If it is not the official SPL Token Program, a thorough audit of the custom program's source code is essential to understand its behavior and security implications. Users should avoid interacting with tokens managed by unknown or unverified programs.


### `M-01` — Absence of External Security Signals  *(Severity: Medium · Status: Unresolved)*

Data from external security signals such as GoPlus Solana and RugCheck is unavailable. The absence of these independent security assessments means there is no third-party validation regarding potential risks like honeypots, mutable metadata, or other common token scams. This lack of external scrutiny increases the overall risk profile, especially for a token with fundamental technical issues.

**Recommendation:** Engage with reputable security auditing firms and integrate with external security signal providers (e.g., GoPlus, RugCheck) to provide transparency and independent validation of the token's safety and integrity. This helps build trust within the community.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

Both the Mint Authority and Freeze Authority for the token have been revoked (set to 'None'). If the token were properly initialized and functional, this would be a positive security feature, preventing any single entity from minting new tokens or freezing existing token accounts. This decentralizes control over the token's supply and transferability.

**Recommendation:** Maintain revoked authorities for production tokens to enhance decentralization and prevent centralized control over token supply and transfer mechanisms. This is a good practice for community-owned or fixed-supply tokens.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`c2omvh...pump`](https://solscan.io/account/c2omvhcvt3ddy77s2kzzawfjqeetzofgz4enwwkxpump) |
| **Network** | Solana |
| **Price** | $0.00169 |
| **24h Volume** | $308.8K |
| **Liquidity** | $150.3K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 7mo |
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

- [View on DexScreener](https://dexscreener.com/solana/gc1utsxrrlauwby3uwsemjuxhjmjhhv1sxj9a1jhvyxp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bullish-degen-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-14*
