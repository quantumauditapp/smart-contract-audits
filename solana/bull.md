---
token: Bull
ticker: BULL
network: solana
risk_score: 90
status: critical
date: 2026-05-11
---

# Bull (BULL) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bull-sol)

---

## Audit Summary

The audit of the Bull (BULL) SPL Token Mint (address 3tygkwke2y3rxdw9oslrspxpxmsc1c1oo19w9khspump) reveals a critical inconsistency: the mint account is reported as 'Initialized: False' despite having significant liquidity and trading volume on DEXs. If accurate, this status implies the token is fundamentally non-functional, posing an extreme risk to holders and liquidity providers. Further investigation is required to reconcile this contradiction, as this issue severely impacts the token's validity and usability.

> **Final Recommendation:** Immediate and thorough investigation is required to clarify the 'Initialized: False' status of the Bull (BULL) SPL Token Mint. If the mint is genuinely uninitialized, all associated liquidity and trading are based on a non-functional asset, posing a critical risk to all participants. Users are strongly advised to exercise extreme caution and avoid interacting with this token until this fundamental issue is resolved and verified.

For future token deployments, consider a Premium Deploy option that includes comprehensive pre-launch verification of all on-chain parameters, including mint initialization, authority configurations, and metadata completeness, to prevent such critical discrepancies. This ensures the token is correctly configured and functional before any liquidity is added or trading commences.

## Security Analysis

The audit of the Bull (BULL) SPL Token Mint (address 3tygkwke2y3rxdw9oslrspxpxmsc1c1oo19w9khspump) reveals a critical inconsistency: the mint account is reported as 'Initialized: False' despite having significant liquidity and trading volume on DEXs. If accurate, this status implies the token is fundamentally non-functional, posing an extreme risk to holders and liquidity providers. Further investigation is required to reconcile this contradiction, as this issue severely impacts the token's validity and usability.

Immediate and thorough investigation is required to clarify the 'Initialized: False' status of the Bull (BULL) SPL Token Mint. If the mint is genuinely uninitialized, all associated liquidity and trading are based on a non-functional asset, posing a critical risk to all participants. Users are strongly advised to exercise extreme caution and avoid interacting with this token until this fundamental issue is resolved and verified.

For future token deployments, consider a Premium Deploy option that includes comprehensive pre-launch verification of all on-chain parameters, including mint initialization, authority configurations, and metadata completeness, to prevent such critical discrepancies. This ensures the token is correctly configured and functional before any liquidity is added or trading commences.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical architecture (7.1 Architecture) of the Bull (BULL) SPL Token Mint presents a critical inconsistency: the mint account is reported as 'Initialized: False' despite having significant on-ch |
| **Governance / Economics** | 6/10 | High | The economic viability (7.4 Economic) and governance (7.5 Governance) of the Bull (BULL) token are severely impacted by the reported 'Initialized: False' status of its SPL Token Mint. Despite active t |
| **Upgrades** | 6/10 | Low | SPL Token Mints, as part of the standard SPL Token Program (7.1 Architecture), are not directly upgradeable in the same manner as custom Solana programs (7.7 Upgrades). The 'SOLC_VERSION' indicates 'S |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Uninitialized SPL Token Mint with Active Trading  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint for Bull (BULL) is reported as 'Initialized: False'. However, the token has significant on-chain liquidity ($179,613) and active trading volume ($243,820 in 24h). An uninitialized SPL Token Mint account cannot issue valid tokens, making any associated tokens non-functional and potentially worthless. This contradiction indicates a severe underlying issue, either with the token's fundamental state or the accuracy of the reported data, posing an extreme risk to token holders and liquidity providers.

**Recommendation:** Verify the true initialization status of the mint account. If it is indeed uninitialized, all liquidity should be withdrawn, and trading should cease immediately. If the data source is incorrect, ensure accurate on-chain data is reflected and publicly verifiable.


### `I-01` — Unknown Token Program  *(Severity: Informational · Status: Unresolved)*

The 'Token Program' responsible for managing the Bull (BULL) mint is listed as 'unknown'. While the prefilled 'SOLC_VERSION' suggests 'SPL Token (Token Program v3)', the explicit 'unknown' in the raw data could indicate a non-standard or custom token program. Without knowing the specific program address, a full security assessment of its underlying logic is impossible, though it is likely the standard SPL Token Program.

**Recommendation:** Explicitly identify the SPL Token Program address responsible for managing this mint. If it's a custom program, its source code would require a dedicated audit.


### `I-02` — Missing Basic Token Metadata (Supply & Decimals)  *(Severity: Informational · Status: Unresolved)*

Essential token metadata, specifically 'Supply (raw)' and 'Decimals', are reported as 'unknown'. This lack of information prevents a comprehensive understanding of the token's total issuance, divisibility, and overall tokenomics, which are crucial for assessing its economic model and potential for manipulation.

**Recommendation:** Ensure all fundamental token metadata, including total supply and decimals, is accurately retrievable and publicly available for transparency and proper analysis.


### `I-03` — Lack of External Security Signal Coverage  *(Severity: Informational · Status: Unresolved)*

External security signals from GoPlus Solana and RugCheck are unavailable. While not a direct vulnerability, the absence of these third-party assessments means there is no independent validation or flagging of potential risks (e.g., rug pull indicators, suspicious token configurations) that these services typically provide.

**Recommendation:** Encourage integration with and reporting from reputable third-party security analysis tools to provide additional layers of assurance and risk assessment for token holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3tygkw...pump`](https://solscan.io/account/3tygkwke2y3rxdw9oslrspxpxmsc1c1oo19w9khspump) |
| **Network** | Solana |
| **Price** | $0.004915 |
| **24h Volume** | $735.4K |
| **Liquidity** | $324.5K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 1mo |
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

- [View on DexScreener](https://dexscreener.com/solana/hngjllzkwx2mnwhwdkfycmowz8fth2bxxdpj1vbvkjnb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bull-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-11*
