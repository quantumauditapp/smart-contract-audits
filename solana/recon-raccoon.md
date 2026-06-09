---
token: RECON RACCOON
ticker: RCON
network: solana
risk_score: 90
status: critical
date: 2026-05-12
---

# RECON RACCOON (RCON) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/recon-raccoon-sol)

---

## Audit Summary

This audit report focuses on the RECON RACCOON (RCON) SPL Token Mint account on Solana. The primary finding is that the mint account is marked as 'Initialized: False', which means it is not a functional token mint. Despite this, liquidity and trading volume data are present, creating a significant inconsistency and potential for user confusion. Key authorities (Mint and Freeze) are revoked, which is a positive security practice for a fully deployed token, but this is overshadowed by the uninitialized state. A comprehensive assessment is hindered by the lack of complete on-chain data regarding supply, decimals, and holder distribution.

> **Final Recommendation:** The RECON RACCOON (RCON) SPL Token Mint account presents significant risks primarily due to its uninitialized state. Users should exercise extreme caution, as an uninitialized mint cannot function as a token. The presence of liquidity data for such an account is a critical red flag that could lead to financial loss if users attempt to interact with it as a functional token. It is imperative to clarify the status of this mint account and reconcile the conflicting data.

For future SPL Token deployments, we recommend a Premium Deploy option that includes a comprehensive pre-deployment audit to ensure all accounts are correctly initialized and configured, and that all on-chain data accurately reflects the intended state of the token. This would prevent critical issues like an uninitialized mint from reaching production and misleading users.

## Security Analysis

This audit report focuses on the RECON RACCOON (RCON) SPL Token Mint account on Solana. The primary finding is that the mint account is marked as 'Initialized: False', which means it is not a functional token mint. Despite this, liquidity and trading volume data are present, creating a significant inconsistency and potential for user confusion. Key authorities (Mint and Freeze) are revoked, which is a positive security practice for a fully deployed token, but this is overshadowed by the uninitialized state. A comprehensive assessment is hindered by the lack of complete on-chain data regarding supply, decimals, and holder distribution.

The RECON RACCOON (RCON) SPL Token Mint account presents significant risks primarily due to its uninitialized state. Users should exercise extreme caution, as an uninitialized mint cannot function as a token. The presence of liquidity data for such an account is a critical red flag that could lead to financial loss if users attempt to interact with it as a functional token. It is imperative to clarify the status of this mint account and reconcile the conflicting data.

For future SPL Token deployments, we recommend a Premium Deploy option that includes a comprehensive pre-deployment audit to ensure all accounts are correctly initialized and configured, and that all on-chain data accurately reflects the intended state of the token. This would prevent critical issues like an uninitialized mint from reaching production and misleading users.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical analysis (7.1 Architecture, 7.2 Code Security, 7.3 Access Control) reveals a critical issue: the SPL Token Mint account is uninitialized. While the Mint Authority and Freeze Authority ar |
| **Governance / Economics** | 6/10 | Medium | From an economic and governance perspective (7.4 Economic, 7.5 Governance), the revocation of both Mint and Freeze Authorities is a strong positive, indicating no single entity can inflate the supply  |
| **Upgrades** | 6/10 | Low | Regarding upgrades (7.7 Upgrades), SPL Token Mint accounts themselves are not directly upgradeable in the traditional sense. The underlying SPL Token Program is maintained by Solana Labs. The revocati |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at 7nzuyzyznof9gf3zr9qhdnxpq1mtm8ln3vajuhrgbonk is explicitly marked as 'Initialized: False'. An uninitialized mint account is not a functional token. It lacks defined supply, decimals, and cannot be used for token transfers or other SPL Token operations. This state renders the token unusable and any associated liquidity or trading data highly suspicious.

**Recommendation:** Investigate why the mint account is uninitialized. If this is intended to be a functional token, the account must be properly initialized using the `initialize_mint` instruction of the SPL Token Program. If it's not intended to be a functional token, any associated liquidity should be removed to prevent user confusion.


### `H-01` — Inconsistent Liquidity and Trading Data for Uninitialized Mint  *(Severity: High · Status: Unresolved)*

Despite the mint account being 'Initialized: False', external data sources report significant liquidity ($50,426 USD) and 24h trading volume ($608 USD). This is a severe inconsistency, as an uninitialized mint cannot facilitate actual token trading. This discrepancy could mislead users into believing a non-functional token is active and tradable, potentially leading to financial losses if they attempt to acquire or trade it.

**Recommendation:** Clarify the source and validity of the reported liquidity and trading data. If the data pertains to a different token or is erroneous, it should be corrected or disclaimed. Users should be explicitly warned about the uninitialized state of the mint account and the implications for any reported market activity.


### `M-01` — Lack of Comprehensive On-Chain Data  *(Severity: Medium · Status: Unresolved)*

Critical on-chain data points such as 'Supply (raw)', 'Decimals', and 'Holder Distribution' are reported as 'unknown'. Additionally, external security signals from GoPlus Solana and RugCheck are unavailable. This lack of transparency and data completeness prevents a thorough security and economic assessment of the token and increases the risk for potential users.

**Recommendation:** Ensure all relevant on-chain data for the token mint, including supply, decimals, and holder distribution, is accessible and verifiable. Integrate with or provide links to reputable external security analysis platforms (e.g., GoPlus, RugCheck) to enhance transparency and user confidence.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7nzuyz...bonk`](https://solscan.io/account/7nzuyzyznof9gf3zr9qhdnxpq1mtm8ln3vajuhrgbonk) |
| **Network** | Solana |
| **Price** | $0.002601 |
| **24h Volume** | $121.1K |
| **Liquidity** | $141.8K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 8mo |
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

- [View on DexScreener](https://dexscreener.com/solana/gcxnezvgsn3sj753ak6mcca43gsjlmnvfhyqva2bsf4k)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/recon-raccoon-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-12*
