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

This audit of the RECON RACCOON (RCON) SPL Token Mint at address `7nzuyzyznof9gf3zr9qhdnxpq1mtm8ln3vajuhrgbonk` reveals critical inconsistencies. The mint account is reported as `Initialized: False`, which means it is non-functional and cannot issue tokens. This directly contradicts the presence of reported liquidity and trading volume. This fundamental discrepancy indicates either severe data integrity issues or that the token is not operational as a standard SPL token. Further investigation is urgently required.

> **Final Recommendation:** Immediate and thorough investigation is required to clarify the `Initialized: False` status of the RECON RACCOON (RCON) SPL Token Mint. If the mint is indeed uninitialized, the token is non-functional, and any associated liquidity or trading volume is based on erroneous data, posing a severe risk to users. It is crucial to determine if the reported market data pertains to a different, functional token, or if the mint's on-chain state has been misinterpreted.

For any future token deployments, consider a Premium Deploy option that includes a pre-launch audit of the mint's configuration and a verification of its on-chain state to prevent such critical discrepancies. This ensures all fundamental parameters are correctly set and verified before public listing and liquidity provision.

## Security Analysis

This audit of the RECON RACCOON (RCON) SPL Token Mint at address `7nzuyzyznof9gf3zr9qhdnxpq1mtm8ln3vajuhrgbonk` reveals critical inconsistencies. The mint account is reported as `Initialized: False`, which means it is non-functional and cannot issue tokens. This directly contradicts the presence of reported liquidity and trading volume. This fundamental discrepancy indicates either severe data integrity issues or that the token is not operational as a standard SPL token. Further investigation is urgently required.

Immediate and thorough investigation is required to clarify the `Initialized: False` status of the RECON RACCOON (RCON) SPL Token Mint. If the mint is indeed uninitialized, the token is non-functional, and any associated liquidity or trading volume is based on erroneous data, posing a severe risk to users. It is crucial to determine if the reported market data pertains to a different, functional token, or if the mint's on-chain state has been misinterpreted.

For any future token deployments, consider a Premium Deploy option that includes a pre-launch audit of the mint's configuration and a verification of its on-chain state to prevent such critical discrepancies. This ensures all fundamental parameters are correctly set and verified before public listing and liquidity provision.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The technical assessment reveals a critical issue: the SPL Token Mint is reported as `Initialized: False` (7.2 Code Security). This state renders the token non-functional, preventing any minting or tr |
| **Governance / Economics** | 6/10 | Low | The economic viability of the RECON RACCOON token is critically compromised by its `Initialized: False` status (7.4 Economic). An uninitialized mint cannot support any economic activity, making report |
| **Upgrades** | 6/10 | Low | As an SPL Token Mint, the RECON RACCOON token is managed by the core SPL Token Program, which is not subject to custom upgradeability by the token creator (7.7 Upgrades). This eliminates risks associa |

## Security Findings

_🔴 2 Critical · 🟠 1 High · ⚪ 2 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at `7nzuyzyznof9gf3zr9qhdnxpq1mtm8ln3vajuhrgbonk` is explicitly reported as `Initialized: False`. An uninitialized mint account cannot be used to mint new tokens, nor can it be associated with token accounts for transfers. This renders the token non-functional and unusable within the Solana ecosystem.

**Recommendation:** Verify the on-chain state of the mint account. If it is indeed uninitialized, it cannot function as a token. Any associated market data is misleading. The token creator must initialize the mint account using the `InitializeMint` instruction of the SPL Token Program for it to become functional.


### `C-02` — Critical Data Inconsistency: Uninitialized Mint with Active Liquidity  *(Severity: Critical · Status: Unresolved)*

The audit data presents a critical contradiction: the mint account is reported as `Initialized: False`, yet there is reported `Liquidity (USD): $51,139` and `24h Volume (USD): $626`. An uninitialized SPL token mint cannot facilitate any form of liquidity or trading volume. This indicates a severe data integrity issue, either in the reported state of the mint account or in the market data being attributed to this specific, non-functional mint address.

**Recommendation:** Investigate the source of the market data (Dexscreener) and cross-reference it with the actual on-chain state of the mint account. Determine if the liquidity and volume are associated with a different token or if the `Initialized: False` status is erroneous. Rectify the data discrepancy immediately to prevent user confusion and potential financial loss.


### `H-01` — Unknown Token Program Association  *(Severity: High · Status: Unresolved)*

The "Token Program" associated with the mint is listed as `unknown`. While the context implies it should be the standard SPL Token Program, an explicit "unknown" raises concerns. If a custom or non-standard token program is used, it could contain un-audited logic or vulnerabilities not present in the well-vetted SPL Token Program, potentially exposing users to unforeseen risks.

**Recommendation:** Clarify and verify the exact program ID that manages this SPL Token Mint. If it is not the official SPL Token Program, a comprehensive security audit of the custom token program's source code is essential to identify and mitigate potential vulnerabilities.


### `I-01` — Missing Fundamental Token Information  *(Severity: Informational · Status: Unresolved)*

Key token parameters such as `Supply (raw)` and `Decimals` are reported as `unknown`. This lack of fundamental information hinders a complete assessment of the token's economic design, its divisibility, and potential for supply manipulation or misinterpretation by users and platforms.

**Recommendation:** Ensure that all essential token metadata, including total supply and decimal precision, is accurately retrievable and publicly available. This transparency is crucial for user trust and proper integration with ecosystem tools.


### `I-02` — Incomplete External Security Signal Coverage  *(Severity: Informational · Status: Unresolved)*

External security signals from GoPlus Solana data and RugCheck are reported as `unavailable`. These services provide additional layers of automated security analysis and risk assessment. The absence of this data means that potential red flags or known scam indicators from these sources could not be factored into this audit.

**Recommendation:** Integrate with and monitor external security analysis platforms like GoPlus and RugCheck to gain a broader perspective on potential risks and enhance the overall security posture and transparency of the token.

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
