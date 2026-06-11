---
token: Vibesterz
ticker: VSTR
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Vibesterz (VSTR) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vibesterz-sol)

---

## Audit Summary

The Vibesterz (VSTR) SPL Token Mint exhibits a low-risk profile based on the available on-chain data. Both mint and freeze authorities have been revoked, indicating a fixed supply and immutability of account states. No Token-2022 extensions posing significant risks, such as transfer hooks or permanent delegates, are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available on-chain data, the Vibesterz (VSTR) token presents a low-risk profile. The revocation of mint and freeze authorities, along with immutable metadata and the absence of risky Token-2022 extensions, are positive indicators. However, potential holders should be aware that holder concentration data was unavailable, which could hide significant whale risk. It is recommended to monitor the token's liquidity and trading volume for stability and to verify the project's off-chain reputation and roadmap before making significant investments. For projects requiring enhanced security, consider a Premium Deploy option with continuous monitoring and real-time threat intelligence.

## Security Analysis

The Vibesterz (VSTR) SPL Token Mint exhibits a low-risk profile based on the available on-chain data. Both mint and freeze authorities have been revoked, indicating a fixed supply and immutability of account states. No Token-2022 extensions posing significant risks, such as transfer hooks or permanent delegates, are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

Based on the available on-chain data, the Vibesterz (VSTR) token presents a low-risk profile. The revocation of mint and freeze authorities, along with immutable metadata and the absence of risky Token-2022 extensions, are positive indicators. However, potential holders should be aware that holder concentration data was unavailable, which could hide significant whale risk. It is recommended to monitor the token's liquidity and trading volume for stability and to verify the project's off-chain reputation and roadmap before making significant investments. For projects requiring enhanced security, consider a Premium Deploy option with continuous monitoring and real-time threat intelligence.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Vibesterz (VSTR) token is an SPL Token-2022 mint. A key security strength is the revocation of both the Mint Authority and Freeze Authority, meaning no new tokens can be minted and no existing acc |
| **Governance / Economics** | 10/10 | Low | The token's economic profile shows moderate liquidity with $20,373 USD available on DEXs (Fact: Liquidity (USD): $20,373). The 24-hour trading volume of $20,459 USD is consistent with the liquidity, r |
| **Upgrades** | 10/10 | Low | The token's immutability is a strong point, as both mint and freeze authorities have been revoked, preventing future changes to supply or account states (Fact: Mint Authority: revoked (None), Freeze A |

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
| **Contract** | [`BnhsxD...pump`](https://solscan.io/account/BnhsxDwWwDPVaURQo7KsTJxYogAAc2Pe2Eo2iJa3pump) |
| **Network** | Solana |
| **Price** | $0.000113 |
| **24h Volume** | $70.2K |
| **Liquidity** | $23.6K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 6d |
| **Top-10 Holders** | 43.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 840 buys / 750 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fvxfbooyttpd1ifh3zqxydkfhshfybnfids4gn4ugcp9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vibesterz-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
