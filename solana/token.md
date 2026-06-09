---
token: 🦎
ticker: LIZARD
network: solana
risk_score: 90
status: critical
date: 2026-05-12
---

# 🦎 (LIZARD) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-sol)

---

## Audit Summary

This audit report analyzes the metadata of the 🦎 (LIZARD) SPL Token Mint account. A critical finding is that the mint account is reported as uninitialized, which fundamentally compromises its functionality and contradicts the presence of reported liquidity. While both mint and freeze authorities have been revoked, which is a strong security positive, the uninitialized state presents a severe risk. Key token economic data and external security signals are also unavailable, limiting a comprehensive risk assessment.

> **Final Recommendation:** The 🦎 (LIZARD) SPL Token Mint presents a critical inconsistency: it is reported as uninitialized despite having associated liquidity and trading volume. This state fundamentally compromises the token's integrity and functionality. While the revocation of mint and freeze authorities is a positive security measure, the uninitialized status overrides these benefits, making the token highly suspicious. Users should exercise extreme caution and verify the on-chain initialization status independently before any interaction. For projects seeking to launch a secure and transparent token, a Premium Deploy option ensures all critical parameters are correctly configured and verified on-chain from inception, avoiding such fundamental issues.

## Security Analysis

This audit report analyzes the metadata of the 🦎 (LIZARD) SPL Token Mint account. A critical finding is that the mint account is reported as uninitialized, which fundamentally compromises its functionality and contradicts the presence of reported liquidity. While both mint and freeze authorities have been revoked, which is a strong security positive, the uninitialized state presents a severe risk. Key token economic data and external security signals are also unavailable, limiting a comprehensive risk assessment.

The 🦎 (LIZARD) SPL Token Mint presents a critical inconsistency: it is reported as uninitialized despite having associated liquidity and trading volume. This state fundamentally compromises the token's integrity and functionality. While the revocation of mint and freeze authorities is a positive security measure, the uninitialized status overrides these benefits, making the token highly suspicious. Users should exercise extreme caution and verify the on-chain initialization status independently before any interaction. For projects seeking to launch a secure and transparent token, a Premium Deploy option ensures all critical parameters are correctly configured and verified on-chain from inception, avoiding such fundamental issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The underlying SPL Token Program is a robust and well-audited Solana program. However, the specific 🦎 (LIZARD) mint account is reported as uninitialized, which is |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic & 7.5 Governance: The revocation of both mint and freeze authorities significantly reduces economic and governance risks associated with centralized control. This prevents inflationary at |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The SPL Token Mint account itself is a data account and not subject to direct upgrades. The underlying SPL Token Program is maintained and upgraded by Solana governance, a well-establish |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account `347k5f1wlrye81rorclbwdr6k3ecrunaqetqpw6pbonk` is reported as `Initialized: False`. An uninitialized mint account cannot properly function, meaning its supply, decimals, and ability to facilitate transfers are compromised. This directly contradicts the presence of reported liquidity and trading volume, indicating a severe inconsistency in the token's state or the data reporting.

**Recommendation:** Verify the true initialization status of the mint account directly on-chain. If it is indeed uninitialized, any associated liquidity or trading activity is highly suspicious and potentially fraudulent. Users should exercise extreme caution and avoid interacting with this token until its initialization status is confirmed and resolved.


### `I-01` — Unknown Supply and Decimals  *(Severity: Informational · Status: Unresolved)*

The total supply and decimal precision for the 🦎 (LIZARD) token are reported as unknown. This information is fundamental for understanding token economics, valuation, and user interface display. This state is consistent with an uninitialized mint account, further highlighting the critical issue.

**Recommendation:** Users should be aware that critical token economic data is unavailable. This lack of transparency hinders proper risk assessment and makes it difficult to understand the token's true value or potential for dilution.


### `I-02` — Unavailable Holder Distribution Data  *(Severity: Informational · Status: Unresolved)*

Data regarding the distribution of 🦎 (LIZARD) tokens among holders is unavailable. This prevents an assessment of token centralization, which is crucial for understanding potential market manipulation risks or governance influence by a small number of large holders.

**Recommendation:** Without holder distribution data, it is impossible to determine if a small number of addresses control a significant portion of the token supply, posing a risk of concentrated ownership and potential market manipulation. Users should proceed with caution.


### `I-03` — Unavailable External Security Signals  *(Severity: Informational · Status: Unresolved)*

External security signals from GoPlus Solana and RugCheck are unavailable for the 🦎 (LIZARD) token. These services provide additional layers of automated security analysis and red flag identification, which can help users assess token legitimacy and safety.

**Recommendation:** The absence of these external checks means that potential red flags or known scam indicators might not have been identified by third-party services. Users are advised to conduct more thorough independent due diligence.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`347k5f...bonk`](https://solscan.io/account/347k5f1wlrye81rorclbwdr6k3ecrunaqetqpw6pbonk) |
| **Network** | Solana |
| **Price** | $0.0001683 |
| **24h Volume** | $206.8K |
| **Liquidity** | $58.6K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 9mo |
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

- [View on DexScreener](https://dexscreener.com/solana/gcgn1netxzanrvfzfno1w1br5vdvug7mysxdcgsrfsm4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*
