---
token: The Red Dragon
ticker: ZION
network: solana
risk_score: 36
status: medium
date: 2026-07-07
---

# The Red Dragon (ZION) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-red-dragon-sol)

---

## Audit Summary

The Red Dragon (ZION) is a new SPL Token-2022 mint on Solana. The mint and freeze authorities have been revoked, indicating a fixed supply and no ability to freeze accounts. However, the DEX pair is very new, having been created only 1 day ago, which provides insufficient track record for assessing market behavior. Holder concentration data was unavailable from RPC, though RugCheck.xyz flagged "Top 10 holders high ownership" as a risk.

> **Final Recommendation:** Holders should be aware of the very recent launch of this token's DEX pair, as it lacks a sufficient track record for assessing long-term stability or issuer intent. While the mint and freeze authorities are revoked, which is a positive security indicator, the unavailability of detailed holder concentration data from RPC means potential whale risks cannot be fully quantified. Investors should exercise caution and monitor the token's market behavior and holder distribution as it matures.

For enhanced due diligence, consider a Premium Deploy audit which includes deeper off-chain analysis of the issuer's history and community sentiment, beyond the on-chain facts.

## Security Analysis

The Red Dragon (ZION) is a new SPL Token-2022 mint on Solana. The mint and freeze authorities have been revoked, indicating a fixed supply and no ability to freeze accounts. However, the DEX pair is very new, having been created only 1 day ago, which provides insufficient track record for assessing market behavior. Holder concentration data was unavailable from RPC, though RugCheck.xyz flagged "Top 10 holders high ownership" as a risk.

Holders should be aware of the very recent launch of this token's DEX pair, as it lacks a sufficient track record for assessing long-term stability or issuer intent. While the mint and freeze authorities are revoked, which is a positive security indicator, the unavailability of detailed holder concentration data from RPC means potential whale risks cannot be fully quantified. Investors should exercise caution and monitor the token's market behavior and holder distribution as it matures.

For enhanced due diligence, consider a Premium Deploy audit which includes deeper off-chain analysis of the issuer's history and community sentiment, beyond the on-chain facts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, which is a positive security measure as it prevents further token minting and account freezing by a |
| **Governance / Economics** | 6/10 | Medium | The token's DEX pair is very new, established only 1 day ago, which means there is insufficient historical data to assess market stability or team behavior. Current liquidity is $64,767, with a 24-hou |
| **Upgrades** | 8/10 | Low | The mint authority has been revoked, meaning the token supply cannot be increased. The freeze authority is also revoked, preventing any future freezing of token accounts. GoPlus data indicates that me |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 1 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution due to the lack of historical data. Monitor the token's performance and team activity closely over a longer period before making significant investments.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CUB9xv...pump`](https://solscan.io/account/CUB9xv5qxBbFbZ2Q7XGieijQrgAZdDRyk7ifpcawpump) |
| **Network** | Solana |
| **Price** | $0.0008226 |
| **24h Volume** | $131.3K |
| **Liquidity** | $69.2K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 575 buys / 645 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/lbaabc22fu8rcppeqwgmgpsmds8icsrtkru3xch2uc3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-red-dragon-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-07*
