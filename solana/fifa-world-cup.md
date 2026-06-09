---
token: FIFA WORLD CUP
ticker: FWC
network: solana
risk_score: 90
status: critical
date: 2026-05-23
---

# FIFA WORLD CUP (FWC) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fifa-world-cup-sol)

---

## Audit Summary

This audit report analyzes the metadata of the FIFA WORLD CUP (FWC) SPL Token Mint on Solana. The primary concern is the mint's uninitialized state, which fundamentally prevents its proper function, despite significant reported liquidity and trading volume. Key authorities (Mint and Freeze) are appropriately revoked, indicating a fixed supply and non-freezable nature, but these security features are overshadowed by the uninitialized status. Users are advised to exercise extreme caution.

> **Final Recommendation:** The FIFA WORLD CUP (FWC) SPL Token Mint is in a critically uninitialized state, rendering it non-functional despite reported market activity. This poses a significant risk to users who might engage in trading. It is strongly recommended that users avoid interacting with this token until its initialization status is definitively resolved and verified as functional. If this token is intended for legitimate use, it must be properly initialized according to SPL Token Program standards. A Premium Deploy option would typically involve a thorough pre-deployment audit to prevent such fundamental configuration errors, ensuring all critical parameters are correctly set and verified before public launch.

## Security Analysis

This audit report analyzes the metadata of the FIFA WORLD CUP (FWC) SPL Token Mint on Solana. The primary concern is the mint's uninitialized state, which fundamentally prevents its proper function, despite significant reported liquidity and trading volume. Key authorities (Mint and Freeze) are appropriately revoked, indicating a fixed supply and non-freezable nature, but these security features are overshadowed by the uninitialized status. Users are advised to exercise extreme caution.

The FIFA WORLD CUP (FWC) SPL Token Mint is in a critically uninitialized state, rendering it non-functional despite reported market activity. This poses a significant risk to users who might engage in trading. It is strongly recommended that users avoid interacting with this token until its initialization status is definitively resolved and verified as functional. If this token is intended for legitimate use, it must be properly initialized according to SPL Token Program standards. A Premium Deploy option would typically involve a thorough pre-deployment audit to prevent such fundamental configuration errors, ensuring all critical parameters are correctly set and verified before public launch.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | 7.1 Architecture & 7.2 Code Security: The SPL Token Mint is reported as 'Initialized: False', which is a critical architectural flaw preventing its proper operation. Despite this, the Mint Authority a |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic & 7.5 Governance: The token exhibits significant liquidity ($51,346) and 24h trading volume ($89,381) despite being uninitialized. This creates a high economic risk, as users may be tradi |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The Mint Authority and Freeze Authority are both revoked, meaning the token's core parameters (supply, freeze capability) cannot be altered post-deployment. This provides strong immutabi |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized SPL Token Mint  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint at address hxwrnzznqf5iyf3ckmw3ftazqvubb53ohzpjpsnupump is reported as 'Initialized: False'. An uninitialized SPL Token Mint cannot be used to create new tokens, manage supply, or facilitate transfers correctly. This fundamental state error prevents the token from functioning as intended by the Solana Program Library standards.

**Recommendation:** The token mint must be properly initialized using the SPL Token Program's `initialize_mint` instruction. Without proper initialization, the token is non-functional and any associated market activity is highly risky.


### `H-01` — Discrepancy: Uninitialized Mint with Active Market Data  *(Severity: High · Status: Unresolved)*

Despite the token mint being in an 'Initialized: False' state, external data sources report significant liquidity ($51,346) and 24-hour trading volume ($89,381). This creates a critical discrepancy, suggesting that users may be trading a non-functional or improperly configured asset. This could lead to significant economic losses if users are unable to manage or transfer their tokens due to the underlying uninitialized state.

**Recommendation:** Investigate the source of the market data and reconcile it with the token's on-chain state. Users should be explicitly warned about the token's uninitialized status and the potential risks associated with trading it. If the market data refers to a different, functional token, clear disambiguation is required.


### `M-01` — Unknown Token Program ID  *(Severity: Medium · Status: Unresolved)*

The specific Token Program associated with this mint is listed as 'unknown'. While the context suggests it is an SPL Token, the lack of a definitive program ID introduces ambiguity regarding the exact rules governing the token's behavior and potential for unexpected interactions or vulnerabilities specific to a particular program version.

**Recommendation:** Clearly identify and verify the Token Program ID responsible for managing this mint. This ensures transparency and allows for proper security assessment against the known vulnerabilities and features of that specific program version.


### `L-01` — Missing Fundamental Token Information  *(Severity: Low · Status: Unresolved)*

Essential token properties such as 'Supply (raw)' and 'Decimals' are reported as 'unknown'. While this might be a consequence of the 'Initialized: False' state, it represents a lack of transparency and critical information for users attempting to understand and interact with the token. Without these details, it's impossible to accurately interpret token balances or market values.

**Recommendation:** Ensure that all fundamental token metadata, including total supply and decimal precision, is correctly set and publicly accessible upon initialization. This is crucial for user confidence and proper integration with wallets and exchanges.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`hxwrnz...pump`](https://solscan.io/account/hxwrnzznqf5iyf3ckmw3ftazqvubb53ohzpjpsnupump) |
| **Network** | Solana |
| **Price** | $0.001336 |
| **24h Volume** | $463.3K |
| **Liquidity** | $102.7K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 2mo |
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

- [View on DexScreener](https://dexscreener.com/solana/j56dqs7mhjtrrrup6h7qi4ftuyxmqve2plxtvwm84hwx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fifa-world-cup-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-23*
