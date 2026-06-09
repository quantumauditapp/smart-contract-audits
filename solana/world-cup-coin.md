---
token: World Cup Coin
ticker: WORLDCUP
network: solana
risk_score: 85
status: critical
date: 2026-05-15
---

# World Cup Coin (WORLDCUP) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-cup-coin-sol)

---

## Audit Summary

The World Cup Coin (WORLDCUP) SPL Token Mint at address 33eum82laahtv5ykuq1bdweviserh5cnfxqvnlt5pump presents critical risks due to its reported uninitialized state. Despite showing significant liquidity and trading volume, the 'Initialized: False' flag indicates a fundamental misconfiguration or data discrepancy that severely impacts the token's integrity and functionality. Strengths include the revocation of both mint and freeze authorities, preventing further supply manipulation or asset freezing. However, the lack of crucial token details like decimals and supply, alongside unavailable external security signals, further compounds the risk profile.

> **Final Recommendation:** Given the critical finding of an uninitialized SPL Token Mint, extreme caution is advised. Users and investors should independently verify the token's actual on-chain state and functionality, as the reported 'Initialized: False' status fundamentally contradicts the existence of liquidity and trading volume. It is imperative to understand how a token in this state can be traded and what implications this has for its long-term viability and security. For any future token deployments, ensure all critical parameters are correctly initialized and verified post-deployment. A Premium Deploy option would involve a comprehensive pre-deployment audit to prevent such fundamental configuration errors and ensure all on-chain metadata accurately reflects the intended token state.

## Security Analysis

The World Cup Coin (WORLDCUP) SPL Token Mint at address 33eum82laahtv5ykuq1bdweviserh5cnfxqvnlt5pump presents critical risks due to its reported uninitialized state. Despite showing significant liquidity and trading volume, the 'Initialized: False' flag indicates a fundamental misconfiguration or data discrepancy that severely impacts the token's integrity and functionality. Strengths include the revocation of both mint and freeze authorities, preventing further supply manipulation or asset freezing. However, the lack of crucial token details like decimals and supply, alongside unavailable external security signals, further compounds the risk profile.

Given the critical finding of an uninitialized SPL Token Mint, extreme caution is advised. Users and investors should independently verify the token's actual on-chain state and functionality, as the reported 'Initialized: False' status fundamentally contradicts the existence of liquidity and trading volume. It is imperative to understand how a token in this state can be traded and what implications this has for its long-term viability and security. For any future token deployments, ensure all critical parameters are correctly initialized and verified post-deployment. A Premium Deploy option would involve a comprehensive pre-deployment audit to prevent such fundamental configuration errors and ensure all on-chain metadata accurately reflects the intended token state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The technical assessment reveals a critical issue: the SPL Token Mint is reported as 'Initialized: False' (7.2 Code Security). This state is highly unusual and problematic for a token with active trad |
| **Governance / Economics** | 6/10 | Medium | Economically, the token shows active trading with $357,410 in liquidity and $697,357 in 24h volume, indicating market interest (7.4 Economic). The volume/liquidity ratio is normal, suggesting healthy  |
| **Upgrades** | 6/10 | Low | The token's upgradeability and control mechanisms are robustly secured by the revocation of both Mint Authority and Freeze Authority (7.7 Upgrades). This means no new tokens can be minted, and existin |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized SPL Token Mint Account  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account is reported as 'Initialized: False'. For an SPL token to be fully functional and usable, its mint account must be properly initialized. An uninitialized state implies that critical parameters like decimals, supply, and authorities have not been set, or the account is not ready for token operations. This directly contradicts the presence of reported liquidity and trading volume, indicating a severe discrepancy or a non-standard, potentially problematic, token implementation.

**Recommendation:** Immediately investigate the on-chain state of the token mint account to confirm its initialization status. If it is indeed uninitialized, all associated liquidity and trading should be considered highly risky, as the token's fundamental properties are undefined. If this is a new deployment, ensure the `initialize_mint` instruction is correctly executed and confirmed.


### `H-01` — Unknown Decimals and Supply  *(Severity: High · Status: Unresolved)*

The `Decimals: unknown` and `Supply (raw): unknown` fields indicate a lack of crucial information regarding the token's fundamental properties. Without knowing the number of decimals, the token's display value and divisibility are ambiguous. Without the total supply, it's impossible to assess market capitalization, dilution, or the overall economic model. This issue is exacerbated by the 'Initialized: False' status, suggesting these core properties may not be properly defined or accessible.

**Recommendation:** Verify the token's decimals and total supply directly on-chain. This information is critical for any financial assessment or interaction with the token. If these values are genuinely undefined due to the uninitialized state, the token should be considered non-functional and highly risky.


### `M-01` — Undetermined Token Program  *(Severity: Medium · Status: Unresolved)*

The `Token Program: unknown` status for an SPL token mint is unusual. While the mint address itself implies it's an SPL token, the explicit 'unknown' flag suggests a data retrieval issue or an unexpected configuration. This could potentially mask a non-standard token implementation or an issue with how the token program is associated with the mint account, leading to unexpected behavior or security concerns.

**Recommendation:** Confirm the program ID associated with the token mint account. It should explicitly be the official Solana SPL Token Program ID. Any deviation or inability to determine this ID warrants further investigation into the token's origin and implementation.


### `L-01` — Lack of External Security Signals  *(Severity: Low · Status: Unresolved)*

Data from external security analysis platforms like GoPlus Solana and RugCheck is unavailable. This absence means there is no independent, automated assessment of potential risks such as rug pulls, honeypot characteristics, or other common malicious patterns associated with new tokens. This reduces the overall confidence in the token's safety and legitimacy from a third-party perspective.

**Recommendation:** While not a direct vulnerability, the absence of these signals means users must rely solely on their own due diligence. Encourage the project to integrate with such services or provide transparent information that addresses common security concerns.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`33eum8...pump`](https://solscan.io/account/33eum82laahtv5ykuq1bdweviserh5cnfxqvnlt5pump) |
| **Network** | Solana |
| **Price** | $0.002513 |
| **24h Volume** | $669.0K |
| **Liquidity** | $159.1K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 2d |
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

- [View on DexScreener](https://dexscreener.com/solana/8uycgrrxzc3xky8pbjdskubaup4mpbxoj1ezj7a5g9wy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-cup-coin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-15*
