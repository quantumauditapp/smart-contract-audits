---
token: penispoop420
ticker: PP420
network: solana
risk_score: 35
status: medium
date: 2026-05-29
---

# penispoop420 (PP420) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/penispoop420-sol)

---

## Audit Summary

This report provides a security analysis of the penispoop420 (PP420) SPL Token Mint account on Solana. The analysis is based on on-chain metadata and external security signals, as source code for SPL Token Mints is not available. Key findings include the mint's uninitialized state, which prevents token operations, and the unknown supply and decimals. Positively, both Mint and Freeze authorities have been revoked, indicating a fixed supply and immutability regarding account freezing. Data on holder distribution and certain RPC details were unavailable, limiting a full economic assessment.

> **Final Recommendation:** The penispoop420 (PP420) SPL Token Mint is in an uninitialized state, rendering it non-functional for token operations. While the revocation of Mint and Freeze authorities is a positive security characteristic, the uninitialized state is a critical impediment to its intended use. It is imperative to initialize the mint if the token is meant to be active, which will also define its supply and decimals.

For projects requiring robust security and operational integrity, a 'Premium Deploy' option is recommended. This includes a pre-deployment audit of any associated custom programs, continuous monitoring of the token's on-chain state, and expert guidance on best practices for SPL Token management and initialization to prevent such issues.

## Security Analysis

This report provides a security analysis of the penispoop420 (PP420) SPL Token Mint account on Solana. The analysis is based on on-chain metadata and external security signals, as source code for SPL Token Mints is not available. Key findings include the mint's uninitialized state, which prevents token operations, and the unknown supply and decimals. Positively, both Mint and Freeze authorities have been revoked, indicating a fixed supply and immutability regarding account freezing. Data on holder distribution and certain RPC details were unavailable, limiting a full economic assessment.

The penispoop420 (PP420) SPL Token Mint is in an uninitialized state, rendering it non-functional for token operations. While the revocation of Mint and Freeze authorities is a positive security characteristic, the uninitialized state is a critical impediment to its intended use. It is imperative to initialize the mint if the token is meant to be active, which will also define its supply and decimals.

For projects requiring robust security and operational integrity, a 'Premium Deploy' option is recommended. This includes a pre-deployment audit of any associated custom programs, continuous monitoring of the token's on-chain state, and expert guidance on best practices for SPL Token management and initialization to prevent such issues.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The SPL Token Mint `ac8escj4ufro8pifkun7diurcccktg4jvarb3mpmpump` is currently uninitialized, preventing any token operations like minting or transfers. This stat |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic & 7.5 Governance: The token exhibits a normal Volume/Liquidity Ratio of 0.17, indicating healthy trading activity relative to its liquidity. However, holder concentration data is unavaila |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: With both Mint and Freeze authorities revoked, the SPL Token Mint's configuration is immutable. This means no further changes can be made to the token's minting capabilities or freezing  |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Uninitialized Mint Account  *(Severity: Medium · Status: Unresolved)*

The SPL Token Mint account `ac8escj4ufro8pifkun7diurcccktg4jvarb3mpmpump` is reported as `Initialized: False`. An uninitialized mint account cannot be used for token operations (minting, transferring) until it is properly initialized. This state could indicate an incomplete deployment or an abandoned token, preventing any utility.

**Recommendation:** Verify the intended state of the mint. If the token is meant to be active, the mint account must be initialized using the `initialize_mint` instruction. This will set the supply, decimals, and mint/freeze authorities, making the token functional.


### `L-01` — Unknown Supply and Decimals  *(Severity: Low · Status: Unresolved)*

The total supply and decimal precision for the token are reported as `unknown`. This is a direct consequence of the mint being uninitialized. Without these fundamental parameters, the token's economic properties and usability are undefined, making it impossible to interact with it correctly.

**Recommendation:** Ensure the mint is properly initialized to establish the token's supply and decimal precision. This information is crucial for any integration or interaction with the token and will be set during the `initialize_mint` instruction.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

The Mint Authority and Freeze Authority for the token have been revoked (set to `None`). This means no new tokens can be minted, and no accounts can be frozen. This configuration makes the token supply fixed and prevents any centralized control over freezing token accounts, enhancing decentralization.

**Recommendation:** This is generally a positive security characteristic for a decentralized token, as it removes potential points of centralized control and ensures supply immutability. No action is required if this is the intended design.


### `I-02` — Unavailable Holder Distribution Data  *(Severity: Informational · Status: Unresolved)*

Data regarding holder concentration is unavailable. This prevents a comprehensive assessment of token distribution and potential whale risks or centralization of ownership, which could impact market stability.

**Recommendation:** While not a direct vulnerability, understanding holder distribution is important for assessing market stability and potential manipulation risks. If possible, monitor on-chain data for holder distribution once the token is active and initialized.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ac8esc...pump`](https://solscan.io/account/ac8escj4ufro8pifkun7diurcccktg4jvarb3mpmpump) |
| **Network** | Solana |
| **Price** | $0.0001014 |
| **24h Volume** | $124.8K |
| **Liquidity** | $30.4K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 4d |
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

- [View on DexScreener](https://dexscreener.com/solana/dyhvcioygvzrvvt7wsowmyi3uhrxnyzwzra6c55ptjb7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/penispoop420-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-29*
