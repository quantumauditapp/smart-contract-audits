---
token: Hog McCrankerson
ticker: HOG
network: solana
risk_score: 85
status: critical
date: 2026-05-29
---

# Hog McCrankerson (HOG) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hog-mccrankerson-sol)

---

## Audit Summary

The audit of the Hog McCrankerson (HOG) SPL Token Mint reveals a critical flaw: the mint is uninitialized, and its Mint Authority has been permanently revoked. This renders the token permanently unusable, as it cannot be initialized to issue tokens. Additionally, key information such as total supply, decimals, and holder distribution is unavailable. While external security signals from GoPlus indicate no immediate honeypot or mutable features, the fundamental inability to function as a token mint presents a severe operational risk.

> **Final Recommendation:** The Hog McCrankerson (HOG) SPL Token Mint is in a critically misconfigured state, being uninitialized with a permanently revoked Mint Authority. This renders the token unusable for its intended purpose. It is strongly recommended that this mint account be considered defunct. Any project intending to launch a functional token should create a new SPL Token Mint, ensure it is properly initialized, and then carefully consider the implications before revoking authorities.

For future token deployments, consider a Premium Deploy option that includes a pre-launch configuration audit. This ensures all critical parameters, such as initialization status and authority settings, are correctly established before public release, preventing fundamental operational failures like the one observed here.

## Security Analysis

The audit of the Hog McCrankerson (HOG) SPL Token Mint reveals a critical flaw: the mint is uninitialized, and its Mint Authority has been permanently revoked. This renders the token permanently unusable, as it cannot be initialized to issue tokens. Additionally, key information such as total supply, decimals, and holder distribution is unavailable. While external security signals from GoPlus indicate no immediate honeypot or mutable features, the fundamental inability to function as a token mint presents a severe operational risk.

The Hog McCrankerson (HOG) SPL Token Mint is in a critically misconfigured state, being uninitialized with a permanently revoked Mint Authority. This renders the token unusable for its intended purpose. It is strongly recommended that this mint account be considered defunct. Any project intending to launch a functional token should create a new SPL Token Mint, ensure it is properly initialized, and then carefully consider the implications before revoking authorities.

For future token deployments, consider a Premium Deploy option that includes a pre-launch configuration audit. This ensures all critical parameters, such as initialization status and authority settings, are correctly established before public release, preventing fundamental operational failures like the one observed here.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The technical review identifies a critical issue: the SPL Token Mint is uninitialized, and its Mint Authority has been revoked (7.2 Code Security). This prevents any future initialization, making the  |
| **Governance / Economics** | 6/10 | Medium | Economically, the Hog McCrankerson token exhibits low liquidity ($3,120 USD) and 24-hour trading volume ($158 USD), which could lead to price volatility (7.4 Economic). The Volume/Liquidity Ratio is n |
| **Upgrades** | 6/10 | Low | The audit notes that both the Mint Authority and Freeze Authority have been revoked (7.7 Upgrades). This means that no further modifications to the mint's properties, such as issuing new tokens or fre |

## Security Findings

_🔴 2 Critical · 🟢 1 Low · ⚪ 3 Informational_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account is reported as `Initialized: False`. This means the mint has not been properly configured and cannot be used to create or manage tokens. No tokens can be minted or transferred from this account.

**Recommendation:** The mint must be initialized using the `initialize_mint` instruction of the SPL Token Program before it can be used. This requires a Mint Authority.


### `C-02` — Uninitialized Mint with Revoked Mint Authority  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint is uninitialized, and its Mint Authority has been revoked (None). Without a Mint Authority, the `initialize_mint` instruction cannot be executed, rendering the token mint permanently unusable and preventing any token issuance or configuration.

**Recommendation:** This state indicates a critical misconfiguration. If the intention was to create a functional token, the mint account needs to be recreated and properly initialized before revoking authorities. This specific mint is permanently non-functional.


### `L-01` — Low Liquidity and Trading Volume  *(Severity: Low · Status: Unresolved)*

The token exhibits low liquidity ($3,120 USD) and 24-hour trading volume ($158 USD). While the Volume/Liquidity Ratio is normal (0.05), the absolute low values suggest potential for significant price impact on trades and limited market depth.

**Recommendation:** Projects should aim to increase liquidity and trading volume to improve market stability and facilitate larger transactions without excessive slippage.


### `I-01` — Undetermined Token Supply and Decimals  *(Severity: Informational · Status: Unresolved)*

The total supply and decimal precision for the Hog McCrankerson token are reported as `unknown`. This lack of transparency can hinder user understanding and trust regarding the token's fundamental properties.

**Recommendation:** Ensure that all necessary mint data, including supply and decimals, is publicly accessible and verifiable once the mint is initialized.


### `I-02` — Holder Distribution Data Unavailable  *(Severity: Informational · Status: Unresolved)*

Information regarding the token's holder distribution is unavailable. This prevents an assessment of centralization risks or potential whale manipulation, which is crucial for community trust and market stability.

**Recommendation:** Ensure holder distribution data is publicly accessible to allow for community analysis of decentralization and potential risks.


### `I-03` — Token Program Not Explicitly Identified  *(Severity: Informational · Status: Unresolved)*

The specific token program governing the mint is listed as `unknown`. While it is likely the standard SPL Token Program, explicit confirmation is missing, which could lead to ambiguity for users.

**Recommendation:** For clarity and user assurance, explicitly identify the governing token program.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`98z2t9...pump`](https://solscan.io/account/98z2t99jkck8nxlxgufgvvphq2eyvwfxug6b7tjzpump) |
| **Network** | Solana |
| **Price** | $0.0005152 |
| **24h Volume** | $349.6K |
| **Liquidity** | $56.4K |
| **Volume / Liquidity** | 6.2× |
| **Token Age** | 7d |
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

- [View on DexScreener](https://dexscreener.com/solana/an3pgeb7slve1kk2gbd5dyjvhdsf1yckdbdj6psvnum5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hog-mccrankerson-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-29*
