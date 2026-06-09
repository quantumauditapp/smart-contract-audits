---
token: Traderclaw
ticker: TCLAW
network: solana
risk_score: 72
status: critical
date: 2026-05-13
---

# Traderclaw (TCLAW) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/traderclaw-sol)

---

## Audit Summary

This audit report analyzes the Traderclaw (TCLAW) SPL Token Mint based on available on-chain metadata and security signals, as source code for the mint configuration itself is not applicable. The token exhibits strong immutability properties with revoked mint and freeze authorities, indicating a decentralized control structure. GoPlus security signals confirm non-mutable balances, non-closable accounts, and non-upgradable transfer parameters. However, the analysis identified significant data inconsistencies and missing information regarding the token's initialization state, supply, and decimals, which introduce a medium level of risk due to potential misinterpretation and lack of transparency.

> **Final Recommendation:** The Traderclaw (TCLAW) SPL Token Mint demonstrates strong security characteristics regarding immutability and decentralized control, primarily due to the revocation of mint and freeze authorities. This significantly reduces governance and economic risks associated with centralized power. However, critical data inconsistencies and missing metadata, particularly concerning the token's initialization status and supply, present transparency challenges that should be addressed for full investor confidence. These data issues do not reflect vulnerabilities in the SPL Token Program itself but rather in the reporting or retrieval of its state.

## Security Analysis

This audit report analyzes the Traderclaw (TCLAW) SPL Token Mint based on available on-chain metadata and security signals, as source code for the mint configuration itself is not applicable. The token exhibits strong immutability properties with revoked mint and freeze authorities, indicating a decentralized control structure. GoPlus security signals confirm non-mutable balances, non-closable accounts, and non-upgradable transfer parameters. However, the analysis identified significant data inconsistencies and missing information regarding the token's initialization state, supply, and decimals, which introduce a medium level of risk due to potential misinterpretation and lack of transparency.

The Traderclaw (TCLAW) SPL Token Mint demonstrates strong security characteristics regarding immutability and decentralized control, primarily due to the revocation of mint and freeze authorities. This significantly reduces governance and economic risks associated with centralized power. However, critical data inconsistencies and missing metadata, particularly concerning the token's initialization status and supply, present transparency challenges that should be addressed for full investor confidence. These data issues do not reflect vulnerabilities in the SPL Token Program itself but rather in the reporting or retrieval of its state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical assessment (7.2 Code Security, 7.3 Access Control) reveals robust immutability for the Traderclaw token. Both Mint Authority and Freeze Authority are revoked, preventing any central enti |
| **Governance / Economics** | 6/10 | Low | The governance and economic risk (7.4 Economic, 7.5 Governance) for Traderclaw is low due to the complete revocation of critical authorities. The absence of a Mint Authority prevents inflationary atta |
| **Upgrades** | 6/10 | Low | The upgradeability risk (7.7 Upgrades) for the Traderclaw SPL Token Mint is low. Key parameters such as transfer fees (`transfer_fee_upgradable: False`) and transfer hooks (`transfer_hook_upgradable:  |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Data Inconsistency: Token Initialized State  *(Severity: High · Status: Unresolved)*

The on-chain data reports the token mint as `Initialized: False`. However, the presence of active liquidity ($3,532 USD) and trading volume ($154 USD) on Dexscreener strongly indicates that the token is, in fact, initialized and functional. This discrepancy suggests a critical data retrieval or reporting error, which can lead to misinterpretation of the token's operational status.

**Recommendation:** Verify the token's initialization status directly via Solana RPC. If the token is indeed initialized and tradable, update data sources to reflect the correct state. If it is truly uninitialized, investigate how liquidity and trading volume were established.


### `M-01` — Missing Core Token Metadata  *(Severity: Medium · Status: Unresolved)*

Critical token parameters such as `Supply (raw)` and `Decimals` are reported as `unknown`. This lack of information prevents a comprehensive assessment of the token's total supply, market capitalization, and precise tokenomics, hindering a full understanding of its economic model.

**Recommendation:** Ensure all essential token metadata, including total supply and decimals, is accurately retrieved and displayed. This information is crucial for investor due diligence and transparent market analysis.


### `I-01` — Unknown Token Program Identifier  *(Severity: Informational · Status: Unresolved)*

The `Token Program` associated with the mint is listed as `unknown`. While this is an SPL Token Mint and implicitly uses the standard SPL Token Program, the explicit 'unknown' indicates a data retrieval gap. For clarity and completeness, the controlling program should be identified.

**Recommendation:** Confirm and explicitly state that the token is controlled by the official Solana Program Library (SPL) Token Program, along with its specific version if available.


### `I-02` — GoPlus Default Account State Signal  *(Severity: Informational · Status: Unresolved)*

GoPlus reports `default_account_state: 1`. While the `Freeze Authority` is revoked and `GoPlus.freezable` is `False`, this signal might indicate a specific default state for newly created token accounts that could be unexpected. Further clarification on the exact meaning of this state in conjunction with other immutability signals would be beneficial.

**Recommendation:** Investigate the precise implications of `GoPlus.default_account_state: 1` in the context of a non-freezable token with revoked freeze authority to ensure there are no unintended side effects for new token account creations.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4bccwh...pump`](https://solscan.io/account/4bccwhaanr5dntjqmmzvqre6kxggchiujryiybbvpump) |
| **Network** | Solana |
| **Price** | $0.003623 |
| **24h Volume** | $456.2K |
| **Liquidity** | $161.2K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 5d |
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

- [View on DexScreener](https://dexscreener.com/solana/2qyyx3tzafjfvtzpfnspovay1dmbwfjvywjt1uq6vhdr)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/traderclaw-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-13*
