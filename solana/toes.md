---
token: TOES
ticker: TOESCOIN
network: solana
risk_score: 90
status: critical
date: 2026-05-29
---

# TOES (TOESCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/toes-sol)

---

## Audit Summary

This report details the security audit of the TOES (TOESCOIN) SPL token mint on Solana. A critical finding is that the mint account is reported as uninitialized, which fundamentally prevents it from functioning as a standard token, despite significant reported liquidity and trading volume. This state poses an immediate and severe risk to any associated funds. Key details such as supply, decimals, and the exact token program ID are also unavailable or inconsistent with a functional mint. External security signals from GoPlus and RugCheck were unavailable for this analysis.

> **Final Recommendation:** Given the critical finding of an uninitialized SPL token mint account, it is strongly recommended that all users and liquidity providers immediately cease interaction with this token. The reported liquidity and trading volume are highly misleading and represent a significant risk of total capital loss. Further investigation is required to understand why an uninitialized mint is associated with active trading.

For future token deployments, consider a Premium Deploy option that includes a comprehensive pre-launch audit of the token program and associated accounts, ensuring proper initialization, authority configuration, and adherence to best security practices before any liquidity is added or public trading commences.

## Security Analysis

This report details the security audit of the TOES (TOESCOIN) SPL token mint on Solana. A critical finding is that the mint account is reported as uninitialized, which fundamentally prevents it from functioning as a standard token, despite significant reported liquidity and trading volume. This state poses an immediate and severe risk to any associated funds. Key details such as supply, decimals, and the exact token program ID are also unavailable or inconsistent with a functional mint. External security signals from GoPlus and RugCheck were unavailable for this analysis.

Given the critical finding of an uninitialized SPL token mint account, it is strongly recommended that all users and liquidity providers immediately cease interaction with this token. The reported liquidity and trading volume are highly misleading and represent a significant risk of total capital loss. Further investigation is required to understand why an uninitialized mint is associated with active trading.

For future token deployments, consider a Premium Deploy option that includes a comprehensive pre-launch audit of the token program and associated accounts, ensuring proper initialization, authority configuration, and adherence to best security practices before any liquidity is added or public trading commences.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The analysis of the TOES token mint (7.1 Architecture, 7.2 Code Security) reveals a critical uninitialized state, preventing basic token operations like minting or supply tracking. While the mint auth |
| **Governance / Economics** | 6/10 | Low | From an economic and governance perspective (7.4 Economic, 7.5 Governance), the reported liquidity of $271,294 and significant trading volume for an uninitialized token mint presents a severe economic |
| **Upgrades** | 6/10 | Low | SPL token mint accounts are data structures managed by the SPL Token Program, not standalone upgradable programs. Therefore, upgradeability (7.7 Upgrades) is not applicable to this specific account. C |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 1 Informational_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL token mint account at address 6ehectmcc85anf4x9cwx8huvwghxqtvkdhkvf2hdpump is reported as 'Initialized: False'. An uninitialized mint account cannot perform core token functions such as minting, burning, or tracking supply. Despite this, the token has reported liquidity of $271,294 and significant trading volume, indicating a severe discrepancy where users are trading a non-functional token. This poses an immediate and complete loss risk to all associated capital.

**Recommendation:** Immediately cease all trading and liquidity provision for this token. Verify the true state of the mint account using Solana RPC calls. If confirmed uninitialized, any associated liquidity is at risk. If a functional token is intended, a new, properly initialized mint account must be created and used.


### `M-01` — Unknown Token Program ID  *(Severity: Medium · Status: Unresolved)*

The 'Token Program' associated with this mint is reported as 'unknown'. While the pre-filled data suggests it's an 'SPL Token v3' mint, the inability to identify the specific program ID from the provided data sources introduces uncertainty. For a standard SPL token, the program ID should be `TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5zt`. An unknown or custom program ID, especially for an uninitialized mint, adds to the overall risk and makes verification of its intended behavior difficult.

**Recommendation:** Verify the exact program ID that owns and governs this mint account. If it is not the standard SPL Token Program, a thorough audit of the custom program is essential to understand its functionality and security implications. If it is intended to be a standard SPL token, ensure the correct program ID is associated and that the mint is properly initialized by it.


### `I-01` — Revoked Mint and Freeze Authorities (Informational)  *(Severity: Informational · Status: Unresolved)*

The mint authority and freeze authority for the TOES token mint are reported as 'revoked (None)'. For a properly initialized and functional token, this is generally considered a positive security practice as it prevents further token issuance or freezing by a central authority, promoting decentralization and immutability of supply. However, in the context of an uninitialized mint, these revocations are currently moot as the mint cannot perform these operations regardless.

**Recommendation:** If a new, functional token mint is deployed, maintaining revoked mint and freeze authorities is recommended for tokens intended to have a fixed supply and no centralized control over transfers.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6ehect...pump`](https://solscan.io/account/6ehectmcc85anf4x9cwx8huvwghxqtvkdhkvf2hdpump) |
| **Network** | Solana |
| **Price** | $0.007238 |
| **24h Volume** | $1.07M |
| **Liquidity** | $229.9K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 9d |
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

- [View on DexScreener](https://dexscreener.com/solana/ee3zk9fxp9guair2xerefxf4tsexezffuwetrna2pkcv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/toes-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-29*
