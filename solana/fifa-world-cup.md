---
token: FIFA WORLD CUP
ticker: FWC
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# FIFA WORLD CUP (FWC) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fifa-world-cup-sol)

---

## Audit Summary

This audit of the FIFA WORLD CUP (FWC) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states. Holder concentration data was unavailable, preventing an assessment of supply distribution risk.

> **Final Recommendation:** Based on the available data, the FIFA WORLD CUP (FWC) token presents a low-risk profile regarding its on-chain configuration and authorities. The revocation of mint and freeze authorities provides strong assurances against supply dilution and account confiscation. However, the absence of holder concentration data means that potential risks related to whale holdings and market manipulation cannot be assessed. Users should consider this data gap and monitor liquidity and trading patterns. For a premium deployment, ensure all relevant data points, including holder distribution, are available for a comprehensive risk assessment.

## Security Analysis

This audit of the FIFA WORLD CUP (FWC) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states. Holder concentration data was unavailable, preventing an assessment of supply distribution risk.

Based on the available data, the FIFA WORLD CUP (FWC) token presents a low-risk profile regarding its on-chain configuration and authorities. The revocation of mint and freeze authorities provides strong assurances against supply dilution and account confiscation. However, the absence of holder concentration data means that potential risks related to whale holdings and market manipulation cannot be assessed. Users should consider this data gap and monitor liquidity and trading patterns. For a premium deployment, ensure all relevant data points, including holder distribution, are available for a comprehensive risk assessment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The FWC token is an SPL Token-2022 mint with a total supply of 999,981,213.932627 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be m |
| **Governance / Economics** | 6/10 | Low | The token has a DEX liquidity of $39,605, with a 24-hour volume of $115,586. The volume/liquidity ratio is 2.92, which is considered normal and does not indicate wash trading. The DEX pair has been ac |
| **Upgrades** | 6/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account freezing capabilities are immutable. The token uses the spl-token-2022 program, but no specific upgrada |

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
| **Contract** | [`HxWrnZ...pump`](https://solscan.io/account/HxWrnZznqF5iYf3ckMw3FTaZQvubB53ohzpjPSNUpump) |
| **Network** | Solana |
| **Price** | $0.001336 |
| **24h Volume** | $463.3K |
| **Liquidity** | $102.7K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 20.8% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/j56dqs7mhjtrrrup6h7qi4ftuyxmqve2plxtvwm84hwx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fifa-world-cup-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
