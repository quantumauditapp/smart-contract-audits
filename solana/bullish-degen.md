---
token: Bullish Degen
ticker: BULLISH
network: solana
risk_score: 90
status: critical
date: 2026-05-14
---

# Bullish Degen (BULLISH) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bullish-degen-sol)

---

## Audit Summary

This report details a security audit of the Bullish Degen (BULLISH) SPL Token Mint account on Solana, based solely on on-chain metadata. The primary finding is that the token mint is uninitialized, rendering the token non-functional. Compounding this, the mint authority has been revoked, preventing any future initialization. While the freeze authority is also revoked, which is generally a positive security practice for decentralization, it is currently irrelevant given the token's unusable state. Information regarding holder distribution and external security signals (GoPlus, RugCheck) was unavailable for this analysis.

> **Final Recommendation:** The Bullish Degen (BULLISH) SPL Token Mint is in a critical, non-functional state due to being uninitialized with a revoked mint authority. This combination means the token cannot be used as intended, and its state cannot be rectified. Any reported liquidity or trading volume is associated with a fundamentally broken asset.

It is strongly recommended that users exercise extreme caution. For any future token deployments, ensure the mint is fully initialized with appropriate decimals and supply *before* revoking the mint authority. For projects requiring robust security and operational integrity, consider a Premium Deploy option, which includes pre-deployment verification and continuous monitoring to prevent such critical configuration errors.

## Security Analysis

This report details a security audit of the Bullish Degen (BULLISH) SPL Token Mint account on Solana, based solely on on-chain metadata. The primary finding is that the token mint is uninitialized, rendering the token non-functional. Compounding this, the mint authority has been revoked, preventing any future initialization. While the freeze authority is also revoked, which is generally a positive security practice for decentralization, it is currently irrelevant given the token's unusable state. Information regarding holder distribution and external security signals (GoPlus, RugCheck) was unavailable for this analysis.

The Bullish Degen (BULLISH) SPL Token Mint is in a critical, non-functional state due to being uninitialized with a revoked mint authority. This combination means the token cannot be used as intended, and its state cannot be rectified. Any reported liquidity or trading volume is associated with a fundamentally broken asset.

It is strongly recommended that users exercise extreme caution. For any future token deployments, ensure the mint is fully initialized with appropriate decimals and supply *before* revoking the mint authority. For projects requiring robust security and operational integrity, consider a Premium Deploy option, which includes pre-deployment verification and continuous monitoring to prevent such critical configuration errors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture & 7.2 Code Security: The core technical issue is the uninitialized state of the SPL Token Mint, which prevents any token operations. This is a critical flaw, as the token cannot be mi |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic & 7.5 Governance: The mint authority and freeze authority for the Bullish Degen token have both been revoked. While this typically enhances decentralization by preventing further token is |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: SPL Token Mint accounts are data accounts managed by the immutable SPL Token Program. As such, the mint account itself is not upgradable. Any changes to token functionality would require |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 2 Informational_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at `c2omvhcvt3ddy77s2kzzawfjqeetzofgz4enwwkxpump` is reported as `Initialized: False`. An uninitialized mint cannot be used to create or manage tokens, rendering the token non-functional. This also means its supply and decimals are undefined.

**Recommendation:** The mint account must be properly initialized using the `initialize_mint` instruction of the SPL Token Program. This requires a mint authority and specifying decimals and supply. However, given the revoked mint authority (H-01), this action is currently impossible.


### `H-01` — Revoked Mint Authority on Uninitialized Mint  *(Severity: High · Status: Unresolved)*

The mint authority for the token `Bullish Degen (BULLISH)` has been revoked (`None`). While typically a security strength preventing arbitrary minting, this is problematic given the mint's `Initialized: False` status (C-01). Without a mint authority, the token cannot be initialized, making it permanently non-functional and unusable.

**Recommendation:** If the intention was to create a functional token, the mint should have been initialized *before* revoking the mint authority. As it stands, this token cannot be made functional. A new, properly initialized mint would be required for a usable token.


### `I-01` — Revoked Freeze Authority  *(Severity: Informational · Status: Resolved)*

The freeze authority for the `Bullish Degen (BULLISH)` token mint has been revoked. This prevents any entity from freezing token accounts, enhancing decentralization and user control over their assets.

**Recommendation:** This is a positive security practice for a decentralized token. No action required.


### `I-02` — Undetermined Token Program  *(Severity: Informational · Status: Unresolved)*

The specific token program governing the `Bullish Degen (BULLISH)` mint is reported as 'unknown'. While typically the standard SPL Token Program, an undetermined program could imply a custom implementation, which would require source code verification for security assessment.

**Recommendation:** Verify the program ID associated with this mint account to confirm it is the official SPL Token Program. If it's a custom program, a full code audit would be necessary to assess its security posture.

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
