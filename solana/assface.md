---
token: assface
ticker: ASSFACE
network: solana
risk_score: 95
status: critical
date: 2026-06-10
---

# assface (ASSFACE) — Smart Contract Security Analysis | Solana

> **Risk Score: 95/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/assface-sol)

---

## Audit Summary

This Solana SPL token mint, "assface," exhibits strong security characteristics with both mint and freeze authorities revoked, preventing further supply inflation or account freezing. No critical or high-severity vulnerabilities were identified based on the available on-chain data and external security signals. However, holder concentration data was unavailable, and RugCheck.xyz flagged "Single holder ownership" and "High holder concentration" as risk labels, which could indicate potential centralization risks.

> **Final Recommendation:** Given the revoked mint and freeze authorities, the token's core parameters appear immutable and secure. However, the absence of detailed holder concentration data prevents a full assessment of distribution risk. It is recommended to independently verify the current holder distribution to understand potential market manipulation risks. Consider the RugCheck.xyz risk labels regarding "Single holder ownership" and "High holder concentration" as a warning sign for potential centralization. For a premium deployment, ensure comprehensive on-chain analysis of holder distribution is performed before significant interaction.

## Security Analysis

This Solana SPL token mint, "assface," exhibits strong security characteristics with both mint and freeze authorities revoked, preventing further supply inflation or account freezing. No critical or high-severity vulnerabilities were identified based on the available on-chain data and external security signals. However, holder concentration data was unavailable, and RugCheck.xyz flagged "Single holder ownership" and "High holder concentration" as risk labels, which could indicate potential centralization risks.

Given the revoked mint and freeze authorities, the token's core parameters appear immutable and secure. However, the absence of detailed holder concentration data prevents a full assessment of distribution risk. It is recommended to independently verify the current holder distribution to understand potential market manipulation risks. Consider the RugCheck.xyz risk labels regarding "Single holder ownership" and "High holder concentration" as a warning sign for potential centralization. For a premium deployment, ensure comprehensive on-chain analysis of holder distribution is performed before significant interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The token mint uses the spl-token-2022 program. Both the mint authority and freeze authority are revoked, indicating that no new tokens can be minted and no accounts can be frozen by an external autho |
| **Governance / Economics** | 6/10 | Low | The token has a liquidity of $34,653 USD with a 24-hour volume of $18,231, resulting in a normal Volume/Liquidity Ratio of 0.53. The DEX pair has been active for 53 days, providing some track record.  |
| **Upgrades** | 6/10 | Low | The mint authority and freeze authority have both been revoked, preventing any future changes to the token's supply or the ability to freeze accounts. The token does not utilize a transfer hook or def |

## Security Findings

_⚪ 3 Informational_

### `I-01` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BnXWvs...pump`](https://solscan.io/account/BnXWvsVZYgBxTUDyDqHZjvFbQGvEZeipY4ZdmqCbpump) |
| **Network** | Solana |
| **Price** | $0.0001859 |
| **24h Volume** | $230.5K |
| **Liquidity** | $54.5K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 40.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/dlwqn3x3wpeqippmnxb8rx3g6jqguecmzjqbpbd7w8yt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/assface-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
