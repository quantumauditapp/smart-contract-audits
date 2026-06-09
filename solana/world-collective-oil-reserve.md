---
token: World Collective Oil Reserve
ticker: WCOR
network: solana
risk_score: 90
status: critical
date: 2026-05-11
---

# World Collective Oil Reserve (WCOR) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-collective-oil-reserve-sol)

---

## Audit Summary

The audit of the World Collective Oil Reserve (WCOR) SPL Token Mint reveals critical issues. The mint account is currently uninitialized, meaning no tokens can be minted, and its supply and decimals are undefined. Despite this, significant liquidity ($55,230) exists for this token, posing a severe risk to investors trading a non-functional asset. Additionally, the owning Token Program is reported as unknown, which introduces further uncertainty regarding its behavior and authenticity.

> **Final Recommendation:** The World Collective Oil Reserve (WCOR) SPL Token Mint presents critical risks primarily due to its uninitialized state and the unknown owning Token Program. Investors are currently exposed to significant risk by trading a non-functional asset. It is strongly recommended that the project team addresses the uninitialized mint status and clarifies the owning program. Until these fundamental issues are resolved, the token should be considered highly speculative and risky.

For projects aiming for high security and transparency, a Premium Deploy option is available. This includes a comprehensive pre-deployment audit, verification of all on-chain configurations, and continuous monitoring to ensure the integrity and expected behavior of the token program and its associated accounts.

## Security Analysis

The audit of the World Collective Oil Reserve (WCOR) SPL Token Mint reveals critical issues. The mint account is currently uninitialized, meaning no tokens can be minted, and its supply and decimals are undefined. Despite this, significant liquidity ($55,230) exists for this token, posing a severe risk to investors trading a non-functional asset. Additionally, the owning Token Program is reported as unknown, which introduces further uncertainty regarding its behavior and authenticity.

The World Collective Oil Reserve (WCOR) SPL Token Mint presents critical risks primarily due to its uninitialized state and the unknown owning Token Program. Investors are currently exposed to significant risk by trading a non-functional asset. It is strongly recommended that the project team addresses the uninitialized mint status and clarifies the owning program. Until these fundamental issues are resolved, the token should be considered highly speculative and risky.

For projects aiming for high security and transparency, a Premium Deploy option is available. This includes a comprehensive pre-deployment audit, verification of all on-chain configurations, and continuous monitoring to ensure the integrity and expected behavior of the token program and its associated accounts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The technical analysis highlights a critical finding: the SPL Token Mint is uninitialized (7.2 Code Security), rendering it non-functional for token issuance. This state is inconsistent with the prese |
| **Governance / Economics** | 6/10 | High | The primary economic risk stems from the uninitialized state of the WCOR token mint (7.4 Economic). Despite being non-functional, the token has accumulated $55,230 in liquidity, exposing investors to  |
| **Upgrades** | 6/10 | Low | The WCOR token mint has both Mint and Freeze authorities revoked (7.7 Upgrades), indicating that no further tokens can be minted or account states frozen by a central authority once the token is initi |

## Security Findings

_🔴 2 Critical · 🟠 1 High · ⚪ 3 Informational_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account for WCOR is reported as `Initialized: False`. An uninitialized mint cannot issue tokens, and its supply and decimals are undefined. This means the token is not yet functional, despite having active trading liquidity.

**Recommendation:** The project team must initialize the SPL Token Mint account to enable token functionality. This involves setting the supply, decimals, and initial authorities. Clear communication to the community regarding the initialization process and timeline is essential.


### `C-02` — Liquidity for Non-Functional Token  *(Severity: Critical · Status: Unresolved)*

Despite the SPL Token Mint being uninitialized and non-functional, there is reported liquidity of $55,230 and active 24h trading volume of $4,050. Investors are currently trading a token that technically does not exist in a functional state, exposing them to severe economic risk.

**Recommendation:** The project team should immediately halt trading or issue a clear warning to investors about the uninitialized state of the token. Trading should only resume once the mint is properly initialized and fully functional.


### `H-01` — Unknown Token Program Owner  *(Severity: High · Status: Unresolved)*

The owning Token Program for the WCOR mint account is reported as `unknown`. For standard SPL Tokens, this should be the official SPL Token Program. An unknown or non-standard owning program introduces significant trust and security risks, as its behavior cannot be guaranteed or easily audited.

**Recommendation:** The project team should clarify and confirm the legitimate owning Token Program for the WCOR mint. If it is not the standard SPL Token Program, a detailed explanation of the custom program's functionality and security implications is required.


### `I-01` — Inconsistent Authority Revocation with Uninitialized State  *(Severity: Informational · Status: Unresolved)*

Both Mint Authority and Freeze Authority are reported as `revoked (None)`. While this is generally a positive security measure for a launched token, it is inconsistent with the `Initialized: False` status of the mint. Authorities cannot truly be revoked if the mint itself has not been fully set up.

**Recommendation:** This observation should be re-evaluated once the mint is initialized. If authorities remain revoked after initialization, it indicates an immutable token supply and freeze status, which is a strong security posture.


### `I-02` — Undefined Supply and Decimals  *(Severity: Informational · Status: Unresolved)*

The `Supply (raw)` and `Decimals` for the WCOR token are reported as `unknown`. This is a direct consequence of the mint being uninitialized. These critical parameters are essential for understanding the token's economics and divisibility.

**Recommendation:** Upon initialization of the SPL Token Mint, the supply and decimal values will be defined and should be clearly communicated to the community.


### `I-03` — GoPlus Default Account State Inconsistency  *(Severity: Informational · Status: Unresolved)*

GoPlus reports `default_account_state: 1` (implying frozen) for the token. This is an unusual default for an uninitialized mint. If the token were initialized, a default frozen state would significantly impact usability.

**Recommendation:** The project team should clarify the intended default account state upon initialization. If a default frozen state is intended, users should be made aware of the process to thaw their accounts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`wcorvx...nazm`](https://solscan.io/account/wcorvxgcpiwe6evtdjxhjq6kcn4nwt9ubt1prjhnazm) |
| **Network** | Solana |
| **Price** | $0.01186 |
| **24h Volume** | $479.4K |
| **Liquidity** | $318.2K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 21d |
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

- [View on DexScreener](https://dexscreener.com/solana/8nsepc2tykgwbaz1wctuhi1cgnqmjupkcscteerjkj9b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-collective-oil-reserve-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-11*
