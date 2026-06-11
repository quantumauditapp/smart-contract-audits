---
token: America Is Back
ticker: AMERICA
network: solana
risk_score: 39
status: medium
date: 2026-06-10
---

# America Is Back (AMERICA) — Smart Contract Security Analysis | Solana

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/america-is-back-sol)

---

## Audit Summary

The America Is Back (AMERICA) token mint on Solana exhibits a robust security configuration with both mint and freeze authorities revoked. No Token-2022 extensions that introduce centralisation risks, such as transfer hooks or permanent delegates, are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** The America Is Back (AMERICA) token presents a strong technical security posture with critical authorities revoked and no centralizing Token-2022 extensions active. However, the absence of holder concentration data means that potential risks from concentrated supply cannot be assessed. Users should be aware of this information gap and consider the implications for price stability. For a comprehensive risk assessment, obtaining holder distribution data is crucial. A Premium Deploy option is not applicable as this is an existing SPL token mint.

## Security Analysis

The America Is Back (AMERICA) token mint on Solana exhibits a robust security configuration with both mint and freeze authorities revoked. No Token-2022 extensions that introduce centralisation risks, such as transfer hooks or permanent delegates, are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

The America Is Back (AMERICA) token presents a strong technical security posture with critical authorities revoked and no centralizing Token-2022 extensions active. However, the absence of holder concentration data means that potential risks from concentrated supply cannot be assessed. Users should be aware of this information gap and consider the implications for price stability. For a comprehensive risk assessment, obtaining holder distribution data is crucial. A Premium Deploy option is not applicable as this is an existing SPL token mint.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | 7.1 Architecture & 7.3 Access Control: The token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be  |
| **Governance / Economics** | 6/10 | Low | 7.4 Economic: The token has a liquidity of $104,250 USD and a 24-hour volume of $111,215, indicating moderate trading activity. The volume/liquidity ratio of 1.07 is normal, suggesting organic trading |
| **Upgrades** | 6/10 | Low | 7.7 Upgrades: The token's mint and freeze authorities are revoked, meaning its core parameters cannot be altered post-launch. GoPlus data confirms that metadata is not mutable, ensuring the token's na |

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
| **Contract** | [`AVA8Yu...pump`](https://solscan.io/account/AVA8YuCsD2YgUSpdv3Hb2cjpdf8XAhGwyXmchxwopump) |
| **Network** | Solana |
| **Price** | $0.001653 |
| **24h Volume** | $1.09M |
| **Liquidity** | $125.5K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 15d |
| **Top-10 Holders** | 15.4% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/e9pq8h8cn2ck3uzxsq6lhkwgbyaanlgah4ywcznqdu3f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/america-is-back-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
