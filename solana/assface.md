---
token: assface
ticker: ASSFACE
network: solana
risk_score: 95
status: critical
date: 2026-05-29
---

# assface (ASSFACE) — Smart Contract Security Analysis | Solana

> **Risk Score: 95/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/assface-sol)

---

## Audit Summary

This audit of the Solana SPL Token Mint `bnxwvsvzygbxtudydqhzjvfbqgvezeipy4zdmqcbpump` reveals a critical vulnerability: the token mint is uninitialized (`Initialized: False`) despite having active liquidity and trading volume. This means the token is non-functional, and any associated trading activity exposes users to severe economic risk. While the mint and freeze authorities are appropriately revoked, the fundamental uninitialized state renders the token unusable.

> **Final Recommendation:** Given the critical finding that the SPL Token Mint is uninitialized despite having active liquidity, it is strongly recommended that all users immediately cease any interaction with this token. Trading or holding this token carries a severe economic risk, as the asset is non-functional. Users should always verify the `Initialized` status of an SPL Token Mint before engaging in any transactions.

For future token deployments, consider a Premium Deploy option that includes pre-deployment verification of all critical account states, such as initialization, authority settings, and metadata integrity, to prevent such fundamental issues from reaching public markets. This ensures a fully functional and secure token launch from the outset.

## Security Analysis

This audit of the Solana SPL Token Mint `bnxwvsvzygbxtudydqhzjvfbqgvezeipy4zdmqcbpump` reveals a critical vulnerability: the token mint is uninitialized (`Initialized: False`) despite having active liquidity and trading volume. This means the token is non-functional, and any associated trading activity exposes users to severe economic risk. While the mint and freeze authorities are appropriately revoked, the fundamental uninitialized state renders the token unusable.

Given the critical finding that the SPL Token Mint is uninitialized despite having active liquidity, it is strongly recommended that all users immediately cease any interaction with this token. Trading or holding this token carries a severe economic risk, as the asset is non-functional. Users should always verify the `Initialized` status of an SPL Token Mint before engaging in any transactions.

For future token deployments, consider a Premium Deploy option that includes pre-deployment verification of all critical account states, such as initialization, authority settings, and metadata integrity, to prevent such fundamental issues from reaching public markets. This ensures a fully functional and secure token launch from the outset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The underlying SPL Token Program is a robust and audited Solana primitive, providing a secure foundation for token management (7.1 Architecture). This specific token mint benefits from strong access c |
| **Governance / Economics** | 6/10 | High | The economic model for this token is critically compromised due to its uninitialized state (7.4 Economic). Despite reported liquidity and trading volume ($37,174 USD and $81,526 USD respectively), the |
| **Upgrades** | 6/10 | Low | The SPL Token Program itself is a core Solana program and is not subject to upgrades by individual token creators. This audit focuses on a specific data account (the token mint) managed by this progra |

## Security Findings

_🔴 1 Critical · ⚪ 2 Informational_

### `C-01` — Uninitialized SPL Token Mint with Active Liquidity  *(Severity: Critical · Status: Unresolved)*

The SPL Token Mint account at `bnxwvsvzygbxtudydqhzjvfbqgvezeipy4zdmqcbpump` is reported as `Initialized: False`. Despite this, there is significant reported liquidity ($37,174 USD) and 24-hour trading volume ($81,526 USD) associated with a trading pair involving this token. An uninitialized SPL Token Mint cannot be used for actual token transfers, minting, or burning. Any trading activity involving an uninitialized token represents a severe economic risk, as users are acquiring a non-functional asset.

**Recommendation:** Users should immediately cease all trading activity involving this token. It is critical to verify the `Initialized` status of any SPL Token Mint before engaging in trading or holding. The presence of liquidity for an uninitialized token strongly suggests a scam or severe misinformation.


### `I-01` — Revoked Mint and Freeze Authorities  *(Severity: Informational · Status: Resolved)*

The Mint Authority and Freeze Authority for the token mint `bnxwvsvzygbxtudydqhzjvfbqgvezeipy4zdmqcbpump` have both been revoked (set to `None`). This is a positive security practice for a fully launched token, as it prevents the original creator from minting additional tokens (preventing inflationary rug pulls) or freezing user accounts.

**Recommendation:** N/A (This is a positive security feature and does not require a recommendation for resolution).


### `I-02` — Incomplete On-Chain Metadata  *(Severity: Informational · Status: Unresolved)*

Essential on-chain metadata such as total supply, decimal precision, and detailed holder distribution are reported as `unknown` or `unavailable`. This is a direct consequence of the token mint being uninitialized. Additionally, external security signals from GoPlus Solana and RugCheck were unavailable, limiting a comprehensive external risk assessment.

**Recommendation:** For any functional token, it is crucial to have complete and verifiable on-chain metadata. Users should exercise extreme caution when interacting with tokens lacking fundamental information.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`bnxwvs...pump`](https://solscan.io/account/bnxwvsvzygbxtudydqhzjvfbqgvezeipy4zdmqcbpump) |
| **Network** | Solana |
| **Price** | $0.0001859 |
| **24h Volume** | $230.5K |
| **Liquidity** | $54.5K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 1mo |
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

- [View on DexScreener](https://dexscreener.com/solana/dlwqn3x3wpeqippmnxb8rx3g6jqguecmzjqbpbd7w8yt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/assface-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-05-29*
