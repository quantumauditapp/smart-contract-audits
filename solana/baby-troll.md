---
token: Baby Troll
ticker: BABYTROLL
network: solana
risk_score: 45
status: medium
date: 2026-06-10
---

# Baby Troll (BABYTROLL) — Smart Contract Security Analysis | Solana

> **Risk Score: 45/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baby-troll-sol)

---

## Audit Summary

The Baby Troll (BABYTROLL) SPL token mint demonstrates a secure configuration with both mint and freeze authorities revoked, ensuring a fixed supply and unfreezable accounts. No critical Token-2022 extensions like permanent delegates or transfer hooks are active. Holder concentration data was unavailable, and while no deterministic findings were triggered, a very low RugCheck score (1/100) is noted, which typically suggests caution.

> **Final Recommendation:** Based on the available on-chain data and deterministic audit rules, the Baby Troll (BABYTROLL) token mint presents a low technical risk profile due to the revocation of critical authorities. This configuration ensures a fixed supply and prevents arbitrary freezing of user accounts. However, holder concentration data was unavailable, which limits the assessment of potential market manipulation risks. Additionally, the extremely low RugCheck score (1/100) suggests that while no specific deterministic vulnerabilities were found, broader caution is warranted regarding the project's overall trustworthiness. Investors should consider this external signal and conduct further due diligence beyond the scope of this technical audit.

## Security Analysis

The Baby Troll (BABYTROLL) SPL token mint demonstrates a secure configuration with both mint and freeze authorities revoked, ensuring a fixed supply and unfreezable accounts. No critical Token-2022 extensions like permanent delegates or transfer hooks are active. Holder concentration data was unavailable, and while no deterministic findings were triggered, a very low RugCheck score (1/100) is noted, which typically suggests caution.

Based on the available on-chain data and deterministic audit rules, the Baby Troll (BABYTROLL) token mint presents a low technical risk profile due to the revocation of critical authorities. This configuration ensures a fixed supply and prevents arbitrary freezing of user accounts. However, holder concentration data was unavailable, which limits the assessment of potential market manipulation risks. Additionally, the extremely low RugCheck score (1/100) suggests that while no specific deterministic vulnerabilities were found, broader caution is warranted regarding the project's overall trustworthiness. Investors should consider this external signal and conduct further due diligence beyond the scope of this technical audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | Low | The Baby Troll (BABYTROLL) token is an SPL Token-2022 mint. Both the mint authority and freeze authority are revoked (None), which is a strong positive indicator for fixed supply and unfreezable accou |
| **Governance / Economics** | 1/10 | Low | The token exhibits moderate liquidity at $79,171 USD, with a 24-hour volume of $79,491 USD, resulting in a normal Volume/Liquidity Ratio of 1.00 (7.4 Economic). The DEX pair is 31 days old, providing  |
| **Upgrades** | 1/10 | Low | The mint authority and freeze authority are both revoked (None), preventing future changes to supply or account freeze status (7.7 Upgrades). The token utilizes the spl-token-2022 program without acti |

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
| **Top-10 Holders** | 27.9% of supply |
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
