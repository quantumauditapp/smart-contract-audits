---
token: Vibesterz
ticker: VSTR
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Vibesterz (VSTR) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vibesterz-sol)

---

## Audit Summary

The Vibesterz (VSTR) SPL Token Mint is in an uninitialized state, rendering it non-functional and unable to issue tokens. Despite this critical technical flaw, the token exhibits reported liquidity and trading volume on decentralized exchanges, which is a severe discrepancy. This indicates a high probability of a scam or misrepresentation, as trading activity for a non-existent token is impossible. The underlying token program ID, supply, and decimals are also unknown, further highlighting the incomplete and potentially fraudulent nature of this asset. External security signals are unavailable, preventing comprehensive vetting.

> **Final Recommendation:** Given the critical finding that the Vibesterz (VSTR) SPL Token Mint is uninitialized, rendering it non-functional, and the alarming discrepancy of reported liquidity and trading volume for such an asset, this token poses an extremely high risk to users. It is strongly recommended to avoid any interaction with this token, including trading or holding, as it appears to be a scam or a severely misconfigured asset. Further investigation into the source of liquidity and trading volume is warranted to understand how a non-existent token is being traded.

For any legitimate token project, a Premium Deploy option would involve a thorough pre-deployment audit to ensure all accounts are correctly initialized, authorities are set as intended, and all metadata is accurately reflected on-chain before any liquidity is provided or public trading commences.

## Security Analysis

The Vibesterz (VSTR) SPL Token Mint is in an uninitialized state, rendering it non-functional and unable to issue tokens. Despite this critical technical flaw, the token exhibits reported liquidity and trading volume on decentralized exchanges, which is a severe discrepancy. This indicates a high probability of a scam or misrepresentation, as trading activity for a non-existent token is impossible. The underlying token program ID, supply, and decimals are also unknown, further highlighting the incomplete and potentially fraudulent nature of this asset. External security signals are unavailable, preventing comprehensive vetting.

Given the critical finding that the Vibesterz (VSTR) SPL Token Mint is uninitialized, rendering it non-functional, and the alarming discrepancy of reported liquidity and trading volume for such an asset, this token poses an extremely high risk to users. It is strongly recommended to avoid any interaction with this token, including trading or holding, as it appears to be a scam or a severely misconfigured asset. Further investigation into the source of liquidity and trading volume is warranted to understand how a non-existent token is being traded.

For any legitimate token project, a Premium Deploy option would involve a thorough pre-deployment audit to ensure all accounts are correctly initialized, authorities are set as intended, and all metadata is accurately reflected on-chain before any liquidity is provided or public trading commences.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The technical architecture of the Vibesterz (VSTR) token mint is fundamentally flawed as the account is reported as uninitialized (7.1). This means core properties like supply and decimals are unknown |
| **Governance / Economics** | 6/10 | High | Economically, the presence of reported liquidity ($23,597) and significant 24-hour trading volume ($70,236) for an uninitialized and non-functional token presents a critical risk (7.4). This discrepan |
| **Upgrades** | 6/10 | Low | Upgradeability is not applicable for an SPL Token Mint account itself, as its properties are defined by the underlying SPL Token Program. However, the current uninitialized state means any potential f |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account for Vibesterz (VSTR) is reported as `Initialized: False`. An uninitialized mint cannot issue tokens, set supply, or define decimals, rendering it completely non-functional and unusable within the Solana ecosystem.

**Recommendation:** A token mint must be properly initialized before it can be used. This involves calling the `initialize_mint` instruction of the SPL Token Program, specifying the number of decimals, mint authority, and freeze authority. Without proper initialization, the token is effectively non-existent.


### `C-02` — Phantom Liquidity and Trading Volume  *(Severity: Critical · Status: Unresolved)*

Despite the token mint being uninitialized and non-functional (C-01), the report indicates significant liquidity ($23,597) and 24-hour trading volume ($70,236). This is a severe discrepancy, as trading a non-existent or non-functional token is impossible. This strongly suggests a potential scam where users are trading a phantom asset, or that the reported data pertains to a different, unrelated asset.

**Recommendation:** Users should exercise extreme caution and verify the legitimacy of any token before engaging in trading. Projects should ensure that liquidity is only provided for fully functional and correctly initialized token mints. Investigate the source of this liquidity and trading data to understand the nature of this discrepancy.


### `H-01` — Unknown Token Program  *(Severity: High · Status: Unresolved)*

The underlying Token Program ID associated with the Vibesterz (VSTR) mint is reported as `unknown`. For standard SPL tokens, this should be a well-known program ID (e.g., `TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA`). An unknown program ID raises concerns about the token's legitimacy, whether it's a custom and unaudited implementation, or if the data retrieval failed.

**Recommendation:** The specific Token Program ID should be clearly identified and verified. If it's a custom program, its source code must be thoroughly audited for security vulnerabilities. If it's intended to be a standard SPL token, the correct program ID should be resolvable.


### `M-01` — Undetermined Supply and Decimals  *(Severity: Medium · Status: Unresolved)*

The total supply and decimal configuration for the Vibesterz (VSTR) token are reported as `unknown`. These fundamental properties are established during the mint's initialization. Their absence prevents users from understanding the token's economic model or interacting with it correctly. This is a direct consequence of the uninitialized state (C-01).

**Recommendation:** Ensure the token mint is properly initialized, which will define and make discoverable its total supply and decimal precision. Without these, the token is unusable.


### `L-01` — Lack of External Security Vetting  *(Severity: Low · Status: Unresolved)*

Data from external security signals such as GoPlus Solana and RugCheck is unavailable. This means there is no independent, automated assessment of potential risks, rug pull indicators, or other common vulnerabilities associated with the token.

**Recommendation:** While not a direct vulnerability, the absence of external security signals means users must rely solely on manual due diligence. Projects should aim to have their tokens vetted by reputable security services to provide additional assurance to potential holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`bnhsxd...pump`](https://solscan.io/account/bnhsxdwwwdpvaurqo7kstjxyogaac2pe2eo2ija3pump) |
| **Network** | Solana |
| **Price** | $0.000113 |
| **24h Volume** | $70.2K |
| **Liquidity** | $23.6K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 840 buys / 750 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fvxfbooyttpd1ifh3zqxydkfhshfybnfids4gn4ugcp9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vibesterz-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
