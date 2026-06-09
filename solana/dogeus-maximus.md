---
token: Dogeus Maximus
ticker: DOGEUS
network: solana
risk_score: 85
status: critical
date: 2026-06-09
---

# Dogeus Maximus (DOGEUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogeus-maximus-sol)

---

## Audit Summary

This report provides a security assessment of the Dogeus Maximus (DOGEUS) SPL Token Mint based on on-chain metadata and publicly available information. Source code for SPL Token Mints is not directly auditable, and the analysis is metadata-driven. The assessment reveals critical operational and security concerns, primarily due to the mint account being uninitialized and its controlling program being unidentified. While mint and freeze authorities are reported as revoked, the fundamental uninitialized state renders the token non-functional and highly risky for any interaction.

> **Final Recommendation:** The Dogeus Maximus (DOGEUS) SPL Token Mint is in a critical state due to being uninitialized and having an unknown controlling program. This renders the token non-functional and highly risky. Users should exercise extreme caution and avoid any interaction with this token until its mint account is properly initialized by a trusted entity, its decimals and supply are clearly defined, and the controlling Token Program is verified to be a standard, audited SPL Token Program. The current state poses a significant risk of loss of funds or unexpected behavior.

For projects aiming for robust security and transparency, a 'Premium Deploy' option involves a full pre-deployment audit of any custom token programs, verification of standard SPL program usage, and a post-deployment verification of all account states and authorities. This ensures all parameters are correctly set and immutable authoriti…

## Security Analysis

This report provides a security assessment of the Dogeus Maximus (DOGEUS) SPL Token Mint based on on-chain metadata and publicly available information. Source code for SPL Token Mints is not directly auditable, and the analysis is metadata-driven. The assessment reveals critical operational and security concerns, primarily due to the mint account being uninitialized and its controlling program being unidentified. While mint and freeze authorities are reported as revoked, the fundamental uninitialized state renders the token non-functional and highly risky for any interaction.

The Dogeus Maximus (DOGEUS) SPL Token Mint is in a critical state due to being uninitialized and having an unknown controlling program. This renders the token non-functional and highly risky. Users should exercise extreme caution and avoid any interaction with this token until its mint account is properly initialized by a trusted entity, its decimals and supply are clearly defined, and the controlling Token Program is verified to be a standard, audited SPL Token Program. The current state poses a significant risk of loss of funds or unexpected behavior.

For projects aiming for robust security and transparency, a 'Premium Deploy' option involves a full pre-deployment audit of any custom token programs, verification of standard SPL program usage, and a post-deployment verification of all account states and authorities. This ensures all parameters are correctly set and immutable authoriti…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical architecture (7.1 Architecture) of this SPL Token Mint presents significant issues. Most critically, the mint account is uninitialized, meaning its core properties are not set, and it ca |
| **Governance / Economics** | 6/10 | High | The economic aspects (7.4 Economic) of the Dogeus Maximus token are highly uncertain due to the uninitialized state of the mint. Key properties such as total supply and decimals are unknown, preventin |
| **Upgrades** | 6/10 | Low | The upgradeability (7.7 Upgrades) of this SPL Token Mint is minimal, which is generally a security strength for a token. Both the Mint Authority and Freeze Authority are reported as revoked. This mean |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account `femrhdedduvuzo25rzrizd6te8xy3tdykllxbheepump` is reported as `Initialized: False`. An uninitialized mint account cannot be used to create tokens, and its properties (like decimals, mint authority, freeze authority) are not yet set. This state makes the token unusable and potentially vulnerable to malicious initialization by any party, leading to an unpredictable token supply or behavior.

**Recommendation:** The token mint must be properly initialized by a trusted entity to define its properties and enable token issuance. Until initialization, the token is non-functional and poses a significant risk. All associated liquidity and trading activity is based on a non-functional token.


### `H-01` — Unknown Token Program Controlling Mint  *(Severity: High · Status: Unresolved)*

The underlying Token Program for the `Dogeus Maximus (DOGEUS)` mint is reported as `unknown`. Standard SPL tokens are managed by the official `TokenkegQfeZyiNwAJbNbGKPFXAbZf5vWPvGHFN` program. An unknown program could imply a custom implementation with unaudited or malicious logic, or simply a data retrieval issue. This introduces uncertainty about the token's behavior, security, and adherence to SPL standards.

**Recommendation:** Verify the exact program ID controlling this mint. If it's a custom program, a thorough security audit of that program's source code is essential before any interaction. If it's a standard SPL program but the data source failed to identify it, this finding's severity would decrease, but verification is still crucial.


### `M-01` — Undefined Token Properties (Supply & Decimals)  *(Severity: Medium · Status: Unresolved)*

The `Supply (raw)` and `Decimals` for the `Dogeus Maximus (DOGEUS)` token are reported as `unknown`. These fundamental properties are crucial for understanding a token's economics and usability. Their absence prevents accurate valuation, display, and interaction with the token. This is a direct consequence of the mint being uninitialized (C-01).

**Recommendation:** Ensure the token mint is initialized, which will define its decimals and allow for the tracking of supply. Users should avoid interacting with tokens where basic properties like decimals and supply are not clearly defined, as this can lead to miscalculations and potential financial loss.


### `I-01` — Lack of External Security Signals  *(Severity: Informational · Status: Unresolved)*

Data from external security analysis platforms such as GoPlus and RugCheck is unavailable for `Dogeus Maximus (DOGEUS)`. These platforms provide automated risk assessments and red flags, which are valuable for quick due diligence. The absence of this data means users lack an additional layer of automated security vetting.

**Recommendation:** Users should exercise increased caution and conduct thorough manual due diligence when external security signals are unavailable. Project teams should aim to integrate with and be recognized by reputable security analysis platforms to provide greater transparency and trust.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`femrhd...pump`](https://solscan.io/account/femrhdedduvuzo25rzrizd6te8xy3tdykllxbheepump) |
| **Network** | Solana |
| **Price** | $0.0002051 |
| **24h Volume** | $109.4K |
| **Liquidity** | $43.3K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 10d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1636 buys / 1297 sells |

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

## Frequently Asked Questions

### Is Dogeus Maximus a scam?

The provided data indicates several high-risk factors commonly associated with potential malicious projects, such as an unverified contract and unrenounced ownership. While these do not definitively confirm it as a scam, they significantly raise the risk of developer manipulation or a rug-pull, contributing to its high risk score of 68/100. Investors should exercise extreme caution and conduct thorough due diligence.

### Is Dogeus Maximus safe to buy?

Based on the security analysis, Dogeus Maximus presents substantial risks that make it unsafe for typical investment. The contract is unverified, ownership is not renounced, and liquidity is not locked. These factors indicate a high potential for developer manipulation or liquidity withdrawal, resulting in a high risk score of 68/100. Investing under these conditions carries a significant risk of capital loss.

### Has Dogeus Maximus been audited?

The contract for Dogeus Maximus is listed as 'False' for verification, meaning its code has not been publicly confirmed to match the deployed version on the blockchain. This is distinct from a formal security audit by an independent firm, which assesses code for vulnerabilities and security flaws. The current status indicates that no such audit information is available through contract verification.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/eysderowtsftm1x5abw5hwuhrvmv88gozsvdecpar38f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogeus-maximus-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-09*
