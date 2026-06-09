---
token: Aliens are real
ticker: ALIENS
network: solana
risk_score: 95
status: critical
date: 2026-05-12
---

# Aliens are real (ALIENS) — Smart Contract Security Analysis | Solana

> **Risk Score: 95/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aliens-are-real-sol)

---

## Audit Summary

The audit of the 'Aliens are real' SPL Token Mint account reveals critical fundamental issues. The mint is reported as 'Initialized: False' and its associated 'Token Program' is 'unknown'. These findings are highly contradictory to the reported liquidity and trading volume, indicating a severe misconfiguration or potential scam. While mint and freeze authorities are revoked, preventing further centralized control, the core functionality of the token is compromised, posing a significant risk to users. Extreme caution is advised.

> **Final Recommendation:** Given the critical finding of an uninitialized token mint account with reported liquidity, users are strongly advised to exercise extreme caution and immediately verify the on-chain status of this token. Trading or holding this token carries a high risk of loss due to its potentially non-functional nature. It is recommended to cease all interactions until the initialization status and associated token program are definitively confirmed as legitimate and functional. For projects seeking to deploy a robust and secure token, consider a Premium Deploy option that includes comprehensive pre-deployment audits and continuous monitoring to prevent such fundamental configuration errors.

## Security Analysis

The audit of the 'Aliens are real' SPL Token Mint account reveals critical fundamental issues. The mint is reported as 'Initialized: False' and its associated 'Token Program' is 'unknown'. These findings are highly contradictory to the reported liquidity and trading volume, indicating a severe misconfiguration or potential scam. While mint and freeze authorities are revoked, preventing further centralized control, the core functionality of the token is compromised, posing a significant risk to users. Extreme caution is advised.

Given the critical finding of an uninitialized token mint account with reported liquidity, users are strongly advised to exercise extreme caution and immediately verify the on-chain status of this token. Trading or holding this token carries a high risk of loss due to its potentially non-functional nature. It is recommended to cease all interactions until the initialization status and associated token program are definitively confirmed as legitimate and functional. For projects seeking to deploy a robust and secure token, consider a Premium Deploy option that includes comprehensive pre-deployment audits and continuous monitoring to prevent such fundamental configuration errors.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical analysis reveals critical issues with the token mint account, primarily its 'Initialized: False' status and 'unknown' associated Token Program. These fundamental flaws contradict the rep |
| **Governance / Economics** | 6/10 | High | The economic stability of the 'Aliens are real' token is severely compromised by its uninitialized state, making its fundamental properties like supply and decimals unknown. This creates significant u |
| **Upgrades** | 6/10 | Low | As an SPL Token Mint account, this asset's core functionality is governed by the underlying SPL Token Program, which is maintained and upgradable by Solana Labs. This specific mint account itself is a |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 2 Informational_

### `C-01` — Uninitialized Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The token mint account is reported as 'Initialized: False'. An SPL Token Mint must be initialized to define its properties (supply, decimals) and enable token operations. The presence of reported liquidity and trading volume for an uninitialized mint is a severe contradiction.

**Recommendation:** Verify the true initialization status of the mint account on-chain. If it is indeed uninitialized, all associated liquidity and trading should be considered highly suspicious and potentially fraudulent. Users should immediately cease interaction with this token.


### `H-01` — Unknown Token Program  *(Severity: High · Status: Unresolved)*

The 'Token Program' associated with this mint is reported as 'unknown'. Standard SPL tokens are managed by the well-known 'TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA' program. An unknown program, especially combined with an uninitialized state, raises significant concerns about the token's legitimacy.

**Recommendation:** Determine the exact program ID controlling this mint. If it's not the standard SPL Token Program, a thorough audit of the custom program is required. If the program ID cannot be determined, the token should be treated as highly risky.


### `I-01` — Undefined Token Properties  *(Severity: Informational · Status: Unresolved)*

The 'Supply (raw)' and 'Decimals' for the token are reported as 'unknown'. These fundamental properties are essential for understanding a token's economics and usability. Their absence is a direct consequence of the uninitialized state.

**Recommendation:** A functional SPL Token Mint must have defined supply and decimals. This issue will be resolved if the mint is properly initialized and its properties are retrievable.


### `I-02` — Lack of Comprehensive Security Data  *(Severity: Informational · Status: Unresolved)*

External security signals from GoPlus Solana and RugCheck, as well as holder distribution data, are unavailable. This limits the ability to perform a comprehensive risk analysis.

**Recommendation:** Seek out additional on-chain data and third-party security analyses to gain a more complete picture of the token's risk profile and distribution.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`f5tfzt...pump`](https://solscan.io/account/f5tfzttne4sysmhzt5krfpwvhmysfjzorjcuxkpbpump) |
| **Network** | Solana |
| **Price** | $0.0008594 |
| **24h Volume** | $648.2K |
| **Liquidity** | $158.6K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 2mo |
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

- [View on DexScreener](https://dexscreener.com/solana/7nvp4qykvmpeuhobyrzcn1tqiz7k8pmk5uxqeebrzyh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aliens-are-real-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*
