---
token: World Collective Oil Reserve
ticker: WCOR
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# World Collective Oil Reserve (WCOR) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-collective-oil-reserve-sol)

---

## Audit Summary

The World Collective Oil Reserve (WCOR) SPL token mint appears to be securely configured with both mint and freeze authorities revoked, preventing further supply inflation or account freezing. No critical or high-severity vulnerabilities were identified based on the available on-chain metadata and external security signals. Holder concentration data was unavailable, which prevents a full assessment of market manipulation risk.

> **Final Recommendation:** Based on the available data, the WCOR token mint exhibits a robust security configuration with no active mutable authorities. Holders should be aware that holder concentration data was not available for this audit, which is crucial for assessing potential market manipulation risks from concentrated holdings. It is recommended to monitor on-chain holder distribution if this data becomes available. No further specific actions are required regarding the token's mint configuration.

## Security Analysis

The World Collective Oil Reserve (WCOR) SPL token mint appears to be securely configured with both mint and freeze authorities revoked, preventing further supply inflation or account freezing. No critical or high-severity vulnerabilities were identified based on the available on-chain metadata and external security signals. Holder concentration data was unavailable, which prevents a full assessment of market manipulation risk.

Based on the available data, the WCOR token mint exhibits a robust security configuration with no active mutable authorities. Holders should be aware that holder concentration data was not available for this audit, which is crucial for assessing potential market manipulation risks from concentrated holdings. It is recommended to monitor on-chain holder distribution if this data becomes available. No further specific actions are required regarding the token's mint configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The token is implemented using the standard spl-token program (Token Program v3). Both the Mint Authority and Freeze Authority are revoked (None), ensuring no new tokens can be minted and no existing  |
| **Governance / Economics** | 6/10 | Low | The token exhibits a healthy liquidity profile with $56,851 USD in total DEX liquidity. The 24-hour volume of $6,997 USD results in a normal Volume/Liquidity Ratio of 0.12, indicating organic trading  |
| **Upgrades** | 6/10 | Low | The token's mint and freeze authorities are permanently revoked, meaning no further changes can be made to the token's supply or account freeze status. The token uses the standard spl-token program (v |

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
| **Contract** | [`WCoRVx...NAzM`](https://solscan.io/account/WCoRVxGcpiwE6EvtDjXHJq6Kcn4nWT9Ubt1PrJHNAzM) |
| **Network** | Solana |
| **Price** | $0.01186 |
| **24h Volume** | $479.4K |
| **Liquidity** | $318.2K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 21d |
| **Top-10 Holders** | 19.2% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/8nsepc2tykgwbaz1wctuhi1cgnqmjupkcscteerjkj9b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-collective-oil-reserve-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
