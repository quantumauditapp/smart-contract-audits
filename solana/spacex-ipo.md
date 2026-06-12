---
token: SPACEX IPO
ticker: SPCX
network: solana
risk_score: 59
status: high
date: 2026-06-12
---

# SPACEX IPO (SPCX) — Smart Contract Security Analysis | Solana

> **Risk Score: 59/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-ipo-sol)

---

## Audit Summary

This audit of the SPACEX IPO (SPCX) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint and freeze authorities are revoked, and no Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

> **Final Recommendation:** Based on the available data, the SPACEX IPO (SPCX) token exhibits strong security properties regarding its mint and freeze authorities, which are both revoked. This significantly reduces central party risk. The absence of active Token-2022 extensions like transfer hooks or permanent delegates also contributes to predictable token behavior.

However, a complete assessment of market risk is hindered by the unavailability of holder concentration data. Potential investors should consider this information gap and the low RugCheck score (1/100) as potential indicators of underlying market risks not covered by the deterministic rules. For a Premium Deploy, consider using a token standard that allows for transparent on-chain governance or multi-signature control over any remaining administrative functions, if applicable, although for this token, most critical authorities are already revoked.

## Security Analysis

This audit of the SPACEX IPO (SPCX) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and external security signals. The mint and freeze authorities are revoked, and no Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, which prevents a full assessment of distribution risk.

Based on the available data, the SPACEX IPO (SPCX) token exhibits strong security properties regarding its mint and freeze authorities, which are both revoked. This significantly reduces central party risk. The absence of active Token-2022 extensions like transfer hooks or permanent delegates also contributes to predictable token behavior.

However, a complete assessment of market risk is hindered by the unavailability of holder concentration data. Potential investors should consider this information gap and the low RugCheck score (1/100) as potential indicators of underlying market risks not covered by the deterministic rules. For a Premium Deploy, consider using a token standard that allows for transparent on-chain governance or multi-signature control over any remaining administrative functions, if applicable, although for this token, most critical authorities are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The SPACEX IPO (SPCX) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, preventing further token creation or freezing of user accounts (7.3 Access Contro |
| **Governance / Economics** | 6/10 | Low | The token has a total DEX liquidity of $32,721, which is sufficient to avoid the 'Very Low Liquidity' flag (7.4 Economic). The 24-hour volume is $219,388, resulting in a Volume/Liquidity Ratio of 6.70 |
| **Upgrades** | 6/10 | Low | The mint authority and freeze authority are both revoked, meaning the core properties of the token supply and transferability cannot be altered by a central entity (7.7 Upgrades). The token's metadata |

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
| **Contract** | [`Fuu6SA...pump`](https://solscan.io/account/Fuu6SApor3k4JQQHMEUW33wsar7hdTh3gYLh75Cipump) |
| **Network** | Solana |
| **Price** | $0.0001812 |
| **24h Volume** | $219.2K |
| **Liquidity** | $32.7K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 11d |
| **Top-10 Holders** | 32.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3022 buys / 2022 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/eirxgcv81ql86apv5xz1rwchahjtynv1d7b6l1nmrqfu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-ipo-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-12*
