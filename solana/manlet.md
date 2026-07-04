---
token: manlet
ticker: MANLET
network: solana
risk_score: 33
status: medium
date: 2026-07-04
---

# manlet (MANLET) — Smart Contract Security Analysis | Solana

> **Risk Score: 33/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/manlet-sol)

---

## Audit Summary

The manlet token mint exhibits a very new DEX pair, having been created only 1 day ago, which limits the track record for assessing market behavior. While specific holder concentration data was unavailable, RugCheck.xyz flags the token with 'Single holder ownership' and 'High holder concentration' risk labels. The mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states.

> **Final Recommendation:** Prospective holders should exercise caution due to the very recent launch of the DEX pair, which offers limited historical data for market behavior analysis. While core authorities are revoked, the RugCheck.xyz labels regarding holder concentration suggest potential risks from large holders. It is recommended to monitor the token's market activity and holder distribution over a longer period before making significant investments. For enhanced security, consider using a Premium Deploy option for any future token launches to ensure comprehensive pre-deployment audits and continuous monitoring.

## Security Analysis

The manlet token mint exhibits a very new DEX pair, having been created only 1 day ago, which limits the track record for assessing market behavior. While specific holder concentration data was unavailable, RugCheck.xyz flags the token with 'Single holder ownership' and 'High holder concentration' risk labels. The mint authority and freeze authority are both revoked, indicating a fixed supply and immutability of account states.

Prospective holders should exercise caution due to the very recent launch of the DEX pair, which offers limited historical data for market behavior analysis. While core authorities are revoked, the RugCheck.xyz labels regarding holder concentration suggest potential risks from large holders. It is recommended to monitor the token's market activity and holder distribution over a longer period before making significant investments. For enhanced security, consider using a Premium Deploy option for any future token launches to ensure comprehensive pre-deployment audits and continuous monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.3 Access Control: The token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing token a |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic: The token's DEX pair is very new, established only 1 day ago, which provides an insufficient track record for assessing team or holder behavior. Current liquidity stands at $517,250, wit |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, meaning the token's supply is fixed and no accounts can be frozen. The token utilizes the spl-token-2022 program without active  |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

The DEX pair for this token was created 1 day ago. This provides an insufficient track record to assess team or holder behaviour, making it difficult to predict market stability or potential price manipulation.

**Recommendation:** Exercise caution and monitor the token's performance and community engagement over a longer period (e.g., at least 7 days) to establish a more reliable track record before making significant investments.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DdPrHY...pump`](https://solscan.io/account/DdPrHYqM8Ueovnk9kAnAgoGhswkuaTqmxcoZzU3Zpump) |
| **Network** | Solana |
| **Price** | $0.01874 |
| **24h Volume** | $1.78M |
| **Liquidity** | $516.5K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3059 buys / 3343 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ddzuehgsh9late28k8sqeewckq96k6fxgj7zuwhqnwkv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/manlet-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-04*
