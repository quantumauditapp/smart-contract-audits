---
token: Pudgy Penguins
ticker: PENGU
network: solana
risk_score: 90
status: critical
date: 2026-05-29
---

# Pudgy Penguins (PENGU) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pudgy-penguins-sol)

---

## Audit Summary

This audit report focuses on the metadata of the Pudgy Penguins (PENGU) SPL Token Mint. A critical finding is that the token mint is reported as 'Initialized: False' despite having over $3.2 million in active liquidity. This fundamental contradiction poses a severe risk, as an uninitialized mint cannot function, suggesting a data discrepancy or a non-standard/broken token. Strengths include the revocation of Mint and Freeze authorities, enhancing decentralization. However, key economic data such as total supply and decimals are unknown, hindering a complete risk assessment.

> **Final Recommendation:** Immediate investigation is required to clarify the 'Initialized: False' status of the SPL Token Mint, as this is a critical contradiction with its reported liquidity. Users should exercise extreme caution until this discrepancy is resolved and the token's functional status is confirmed. It is also recommended to verify the exact SPL Token Program ID and obtain full token supply and decimal information for transparency. For projects seeking to launch new tokens, a Premium Deploy option is available, offering comprehensive pre-deployment checks and verification to ensure all token parameters are correctly configured and publicly verifiable, mitigating such fundamental risks.

## Security Analysis

This audit report focuses on the metadata of the Pudgy Penguins (PENGU) SPL Token Mint. A critical finding is that the token mint is reported as 'Initialized: False' despite having over $3.2 million in active liquidity. This fundamental contradiction poses a severe risk, as an uninitialized mint cannot function, suggesting a data discrepancy or a non-standard/broken token. Strengths include the revocation of Mint and Freeze authorities, enhancing decentralization. However, key economic data such as total supply and decimals are unknown, hindering a complete risk assessment.

Immediate investigation is required to clarify the 'Initialized: False' status of the SPL Token Mint, as this is a critical contradiction with its reported liquidity. Users should exercise extreme caution until this discrepancy is resolved and the token's functional status is confirmed. It is also recommended to verify the exact SPL Token Program ID and obtain full token supply and decimal information for transparency. For projects seeking to launch new tokens, a Premium Deploy option is available, offering comprehensive pre-deployment checks and verification to ensure all token parameters are correctly configured and publicly verifiable, mitigating such fundamental risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The token mint demonstrates strong security posture regarding access control, with both Mint and Freeze authorities successfully revoked, preventing further token issuance or freezing (7.3 Access Cont |
| **Governance / Economics** | 6/10 | Medium | The token exhibits healthy market activity with over $3.2 million in liquidity and a normal 24-hour volume/liquidity ratio of 0.11, indicating active trading and market interest (7.4 Economic). The pa |
| **Upgrades** | 6/10 | Low | The SPL Token Mint's configuration is highly secure against unauthorized changes, as both Mint and Freeze authorities have been permanently revoked. This ensures that the token's core parameters canno |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Uninitialized SPL Token Mint with Active Liquidity  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint is reported as 'Initialized: False' in its on-chain metadata. However, external data sources (Dexscreener) indicate over $3.2 million in liquidity and active trading for a token with the same name/symbol. An uninitialized SPL Token Mint cannot be used for minting, transferring, or any standard token operations. This represents a severe contradiction, suggesting either a critical data discrepancy, a non-standard token implementation, or a fundamentally broken token that could lead to loss of funds for users interacting with its liquidity pools.

**Recommendation:** Immediately investigate the discrepancy between the reported 'Initialized: False' state and the active liquidity. Confirm if the token mint at address 2zmmhcvqexdtde6vsfs7s7d6ouodfjhe8vd1gnbouauv is indeed uninitialized. If so, determine why liquidity exists and alert users to potential risks. If the 'Initialized' status is incorrect, verify the data source and correct it. If it's a non-standard token, provide full details of its implementation.


### `I-01` — Unknown Total Supply  *(Severity: Informational · Status: Unresolved)*

The total supply of the PENGU token is reported as 'unknown'. Without this crucial piece of information, it is impossible to accurately calculate the token's market capitalization, assess potential dilution risks, or understand the overall tokenomics. This lack of transparency hinders a comprehensive economic evaluation.

**Recommendation:** Ensure that the total supply of the token is publicly available and verifiable on-chain. If the token is intended to have a fixed supply, this should be clearly stated and reflected in its metadata. If it's a dynamic supply, the mechanism should be transparent.


### `I-02` — Unknown Decimals  *(Severity: Informational · Status: Unresolved)*

The number of decimals for the PENGU token is reported as 'unknown'. Decimals are essential for correctly displaying token balances and ensuring accurate calculations in user interfaces and smart contracts. An unknown decimal count can lead to misinterpretations of token values and potential operational errors.

**Recommendation:** Ensure that the number of decimals for the token is publicly available and verifiable on-chain. This is a standard parameter for SPL Tokens and should be readily accessible.


### `I-03` — Unconfirmed Token Program ID  *(Severity: Informational · Status: Unresolved)*

The specific Token Program ID controlling the PENGU mint is reported as 'unknown'. While the token is identified as an SPL Token Mint, confirming that it is controlled by the official Solana Program Library (SPL) Token Program (TokenkegQfeZgYXGtf7CVDMWSS9JNoBNtt45CvsTq) is crucial for security. If it's a custom or unofficial program, it would require a full source code audit to verify its security and adherence to expected SPL token behavior.

**Recommendation:** Confirm and publicly disclose the exact Token Program ID associated with this mint. If it is not the official SPL Token Program, provide the source code and documentation for the custom program for security review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2zmmhc...uauv`](https://solscan.io/account/2zmmhcvqexdtde6vsfs7s7d5ouodfjhe8vd1gnbouauv) |
| **Network** | Solana |
| **Price** | $0.00772 |
| **24h Volume** | $358.5K |
| **Liquidity** | $3.67M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6mo |
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

- [View on DexScreener](https://dexscreener.com/solana/ddma1chcheqyfttc1z1sjey978ccu1pyjnutwtnmdvzu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pudgy-penguins-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-29*
