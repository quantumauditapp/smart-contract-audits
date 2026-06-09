---
token: Catcoin
ticker: CATCOIN
network: solana
risk_score: 90
status: critical
date: 2026-05-14
---

# Catcoin (CATCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catcoin-sol)

---

## Audit Summary

The Catcoin (CATCOIN) SPL Token presents a mixed security profile. While key authorities (Mint and Freeze) are revoked, and external security signals from GoPlus are largely positive, a critical data inconsistency is reported: the token mint is flagged as 'Initialized: False' despite having active liquidity and trading volume. This contradiction requires further investigation as an uninitialized token should not be functional. Users should exercise caution until this fundamental discrepancy is resolved.

> **Final Recommendation:** The Catcoin SPL Token presents a unique situation due to the reported 'Initialized: False' status conflicting with its active trading and liquidity. While other security aspects, such as revoked authorities and immutable features, are robust, this core inconsistency must be thoroughly investigated. Users should exercise extreme caution until this fundamental discrepancy is resolved, as an uninitialized token could lead to unpredictable behavior or loss of funds.

For projects seeking to deploy tokens with verifiable integrity, a Premium Deploy option is recommended. This service includes a comprehensive pre-deployment audit of the token's configuration and associated programs, ensuring all parameters are correctly set and verified on-chain before public launch, thereby preventing critical initialization errors or data inconsistencies.

## Security Analysis

The Catcoin (CATCOIN) SPL Token presents a mixed security profile. While key authorities (Mint and Freeze) are revoked, and external security signals from GoPlus are largely positive, a critical data inconsistency is reported: the token mint is flagged as 'Initialized: False' despite having active liquidity and trading volume. This contradiction requires further investigation as an uninitialized token should not be functional. Users should exercise caution until this fundamental discrepancy is resolved.

The Catcoin SPL Token presents a unique situation due to the reported 'Initialized: False' status conflicting with its active trading and liquidity. While other security aspects, such as revoked authorities and immutable features, are robust, this core inconsistency must be thoroughly investigated. Users should exercise extreme caution until this fundamental discrepancy is resolved, as an uninitialized token could lead to unpredictable behavior or loss of funds.

For projects seeking to deploy tokens with verifiable integrity, a Premium Deploy option is recommended. This service includes a comprehensive pre-deployment audit of the token's configuration and associated programs, ensuring all parameters are correctly set and verified on-chain before public launch, thereby preventing critical initialization errors or data inconsistencies.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical configuration of the Catcoin SPL Token exhibits strong security features, including the revocation of both Mint and Freeze authorities, preventing unauthorized token creation or freezing |
| **Governance / Economics** | 6/10 | Low | The economic and governance aspects of the Catcoin token show positive indicators. The revocation of Mint and Freeze authorities ensures that no central entity can arbitrarily inflate supply or lock u |
| **Upgrades** | 6/10 | Low | The Catcoin SPL Token demonstrates a low risk profile regarding upgrades. The metadata is reported as immutable, meaning the token's name, symbol, and other descriptive properties cannot be altered po |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Data Inconsistency - Uninitialized Mint with Active Trading  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint for Catcoin is reported as 'Initialized: False'. However, the token has significant reported liquidity ($61,018) and 24h trading volume ($36,503). An uninitialized SPL Token Mint account should not be functional or tradable, as its core data (like supply and decimals) would be unconfigured. This presents a critical contradiction in the reported on-chain facts. If the 'Initialized: False' flag is accurate, the token is fundamentally malformed and should not be trading, posing a severe risk to users. If it's a data reporting error, it's an informational issue, but the report must highlight the stated fact.

**Recommendation:** The project team should clarify the true initialization status of the mint account. If it is indeed uninitialized, immediate action is required to address the malformed state and prevent further trading. If it is a data reporting error, the team should provide verifiable on-chain proof of initialization to reassure users and correct external data sources.


### `I-01` — Unknown Supply and Decimals  *(Severity: Informational · Status: Unresolved)*

The raw supply and decimal precision of the Catcoin token are reported as 'unknown'. This information is crucial for users to understand the token's total issuance and divisibility. This is likely a consequence of the 'Initialized: False' status, as these fields are part of the mint account's initialized data.

**Recommendation:** The project team should ensure that all fundamental token parameters, including total supply and decimals, are publicly verifiable and accurately reported by data sources. This requires proper initialization of the mint account.


### `I-02` — Unavailable Holder Distribution Data  *(Severity: Informational · Status: Unresolved)*

Information regarding the holder distribution of Catcoin is unavailable. This prevents a comprehensive assessment of token centralization, which is an important factor for understanding potential market manipulation risks or governance influence.

**Recommendation:** While not a direct vulnerability, providing transparent holder distribution data enhances trust and allows for better community analysis of decentralization. The project team should aim to make this data accessible through standard explorers or reporting tools.


### `I-03` — Unavailable RugCheck Data  *(Severity: Informational · Status: Unresolved)*

RugCheck data for Catcoin is unavailable. RugCheck provides an additional layer of automated security analysis, and its absence means a potential external risk assessment is missing.

**Recommendation:** Projects should aim for comprehensive external security assessments. While not directly controllable by the project, awareness of missing data points from common security tools is important for a full risk picture.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5gtpsp...coin`](https://solscan.io/account/5gtpspc2ricugwiyq4ghausg8fsq7ucrggsvacatcoin) |
| **Network** | Solana |
| **Price** | $0.0008021 |
| **24h Volume** | $327.4K |
| **Liquidity** | $95.6K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 20d |
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

- [View on DexScreener](https://dexscreener.com/solana/6fnwjffn6kdkybwk5pflwqznptmobaswuwvxig3g5d2d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catcoin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-14*
