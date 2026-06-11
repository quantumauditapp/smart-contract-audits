---
token: Baby Troll
ticker: BABYTROLL
network: solana
risk_score: 85
status: critical
date: 2026-06-10
---

# Baby Troll (BABYTROLL) — Smart Contract Security Analysis | Solana

> **Risk Score: 85/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baby-troll-sol)

---

## Audit Summary

The Baby Troll (BABYTROLL) SPL Token Mint on Solana exhibits a robust security configuration with both mint and freeze authorities revoked, preventing further token issuance or account freezing. No Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, and RugCheck.xyz provided a score of 1/100, but no explicit 'RUGGED' verdict was given.

> **Final Recommendation:** The Baby Troll (BABYTROLL) SPL Token Mint demonstrates strong security practices by having both mint and freeze authorities revoked, ensuring a fixed supply and preventing arbitrary account freezing. No potentially risky Token-2022 extensions like permanent delegates or transfer hooks are active, and metadata is immutable.

However, potential holders should note that holder concentration data was unavailable, which prevents a full assessment of distribution risk. While the RugCheck score is very low (1/100), the specific 'RUGGED' verdict was not provided. For a Premium Deploy option, consider a token with fully transparent holder distribution and a higher RugCheck score to mitigate potential market manipulation risks.

## Security Analysis

The Baby Troll (BABYTROLL) SPL Token Mint on Solana exhibits a robust security configuration with both mint and freeze authorities revoked, preventing further token issuance or account freezing. No Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, and RugCheck.xyz provided a score of 1/100, but no explicit 'RUGGED' verdict was given.

The Baby Troll (BABYTROLL) SPL Token Mint demonstrates strong security practices by having both mint and freeze authorities revoked, ensuring a fixed supply and preventing arbitrary account freezing. No potentially risky Token-2022 extensions like permanent delegates or transfer hooks are active, and metadata is immutable.

However, potential holders should note that holder concentration data was unavailable, which prevents a full assessment of distribution risk. While the RugCheck score is very low (1/100), the specific 'RUGGED' verdict was not provided. For a Premium Deploy option, consider a token with fully transparent holder distribution and a higher RugCheck score to mitigate potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | 7.1 Architecture: The Baby Troll (BABYTROLL) token is implemented using the spl-token-2022 program, indicating support for advanced features. 7.2 Code Security: As an SPL Token Mint, there is no custo |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token exhibits a liquidity of $82,651 USD and a 24-hour trading volume of $98,956 USD. The volume/liquidity ratio is 1.20, which is considered normal and does not suggest wash tradin |
| **Upgrades** | 6/10 | Low | 7.3 Access Control: The mint authority and freeze authority are both revoked, meaning no further administrative actions can be taken to alter the token's supply or freeze accounts. 7.7 Upgrades: As an |

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
| **Contract** | [`6qdzMx...pump`](https://solscan.io/account/6qdzMx4c9rL2X3Ns3SwZ8uEo4zReDPjdXpAEmpo7pump) |
| **Network** | Solana |
| **Price** | $0.00165 |
| **24h Volume** | $757.7K |
| **Liquidity** | $136.1K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 8d |
| **Top-10 Holders** | 28.2% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/34utpx3zyyfc5gvqdxwjqlf77bu5ebb6o3c2xynpktzl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/baby-troll-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
