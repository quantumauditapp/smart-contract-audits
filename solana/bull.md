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

The audit of the Bull (BULL) SPL Token Mint reveals critical data inconsistencies. The mint account is reported as uninitialized, yet significant liquidity and trading volume are present, indicating a severe discrepancy. The underlying token program is unknown, and essential metadata like supply and decimals are missing. These issues prevent a comprehensive security assessment and pose significant risks to users.

> **Final Recommendation:** Due to the critical inconsistencies and missing information, interaction with the Bull (BULL) token at the provided mint address is strongly discouraged. Users should exercise extreme caution and verify the token's legitimacy and operational status independently. A thorough investigation into the discrepancy between the uninitialized mint status and reported liquidity is essential before any engagement.

For projects seeking to deploy a new token, it is recommended to ensure all on-chain metadata is correctly initialized and verifiable. Consider a Premium Deploy option that includes comprehensive pre-deployment checks and a full audit of the token program (if custom) or a verification of standard SPL Token Program usage, ensuring all critical parameters like supply, decimals, and authorities are correctly configured and transparently reported.

## Security Analysis

The audit of the Bull (BULL) SPL Token Mint reveals critical data inconsistencies. The mint account is reported as uninitialized, yet significant liquidity and trading volume are present, indicating a severe discrepancy. The underlying token program is unknown, and essential metadata like supply and decimals are missing. These issues prevent a comprehensive security assessment and pose significant risks to users.

Due to the critical inconsistencies and missing information, interaction with the Bull (BULL) token at the provided mint address is strongly discouraged. Users should exercise extreme caution and verify the token's legitimacy and operational status independently. A thorough investigation into the discrepancy between the uninitialized mint status and reported liquidity is essential before any engagement.

For projects seeking to deploy a new token, it is recommended to ensure all on-chain metadata is correctly initialized and verifiable. Consider a Premium Deploy option that includes comprehensive pre-deployment checks and a full audit of the token program (if custom) or a verification of standard SPL Token Program usage, ensuring all critical parameters like supply, decimals, and authorities are correctly configured and transparently reported.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical assessment is severely hampered by critical data gaps and inconsistencies. While the mint authority and freeze authority are revoked (7.3 Access Control), which is generally a good secur |
| **Governance / Economics** | 6/10 | High | The economic and governance assessment is severely limited by the lack of fundamental data. The unknown supply and decimals (7.4 Economic) prevent any analysis of tokenomics or potential inflation/def |
| **Upgrades** | 6/10 | Low | N/A - Upgradeability is not applicable for an SPL Token Mint account itself. The underlying SPL Token Program is managed by Solana Labs and is not subject to project-specific upgrade risks. Therefore, |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized SPL Token Mint Account with Active Trading Data  *(Severity: Critical · Status: Unresolved)*

The provided on-chain facts state the SPL Token Mint account (`3tygkwke2y3rxdw9oslrspxpxmsc1c1oo19w9khspump`) is `Initialized: False`. However, external data indicates significant liquidity ($186,166 USD) and 24h trading volume ($277,786 USD) associated with this token. An uninitialized SPL mint cannot have a supply, decimals, or be traded, creating a direct and severe contradiction in the reported data. This inconsistency poses a critical risk of misleading users into interacting with a non-functional or non-existent token.

**Recommendation:** Investigate the discrepancy between the mint's uninitialized status and the reported trading activity. Verify if the provided mint address is indeed the correct address for the token being traded, or if the `Initialized` status is incorrectly reported. Users should avoid interacting with this token until this critical inconsistency is resolved and verified.


### `H-01` — Token Program for SPL Mint is Unknown  *(Severity: High · Status: Unresolved)*

The 'Token Program' responsible for managing the SPL Token Mint is listed as `unknown`. For a standard SPL Token, this should be the official Solana Program Library Token Program (e.g., `TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA`). An unknown token program introduces significant uncertainty regarding the token's underlying logic, security, and adherence to standard SPL functionalities. If it's a custom program, its security cannot be assessed without source code.

**Recommendation:** Identify and verify the exact token program governing this mint. If it is a custom program, a full security audit of its source code is essential. If it is intended to be a standard SPL token, ensure the correct program ID is associated and reported.


### `M-01` — Critical Token Metadata (Supply, Decimals) is Unknown  *(Severity: Medium · Status: Unresolved)*

Essential token metadata, specifically `Supply (raw)` and `Decimals`, are reported as `unknown`. These are fundamental properties required to understand the token's total issuance, divisibility, and economic characteristics. The absence of this information prevents a comprehensive assessment of the token's design and potential economic risks.

**Recommendation:** Ensure all critical token metadata, including total supply and decimals, is correctly initialized and publicly verifiable on-chain. This transparency is crucial for user trust and informed decision-making.


### `L-01` — Holder Distribution Data Unavailable  *(Severity: Low · Status: Unresolved)*

Information regarding the `holder concentration` for the Bull (BULL) token is `unavailable`. The absence of holder distribution data prevents an assessment of centralization risks, potential for whale manipulation, or the overall distribution fairness of the token. This limits the ability to evaluate the token's economic health and decentralization.

**Recommendation:** Implement or utilize tools to track and publicly report token holder distribution. Transparent holder data allows for better community assessment of decentralization and potential market risks.

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
