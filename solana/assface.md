---
token: assface
ticker: ASSFACE
network: solana
risk_score: 46
status: high
date: 2026-06-10
---

# assface (ASSFACE) — Smart Contract Security Analysis | Solana

> **Risk Score: 46/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/assface-sol)

---

## Audit Summary

This audit of the assface SPL Token Mint found that critical authorities like Mint and Freeze are revoked, ensuring a fixed supply and unfreezable accounts. No Token-2022 extensions posing significant risks, such as permanent delegates or transfer hooks, are active. Holder concentration data was unavailable from RPC, though RugCheck flagged potential single holder ownership and high concentration, which could pose an economic risk.

> **Final Recommendation:** Given the revoked mint and freeze authorities, the token's core supply and transfer mechanisms are secure from central control. However, the lack of detailed holder concentration data from RPC, coupled with RugCheck's flags for 'Single holder ownership' and 'High holder concentration', suggests a potential for market manipulation or significant price impact from large holders. Users should exercise caution and consider the implications of concentrated ownership before acquiring this token. A Premium Deploy option would involve deeper off-chain due diligence on the project team and a more granular analysis of on-chain holder movements if RPC data becomes available.

## Security Analysis

This audit of the assface SPL Token Mint found that critical authorities like Mint and Freeze are revoked, ensuring a fixed supply and unfreezable accounts. No Token-2022 extensions posing significant risks, such as permanent delegates or transfer hooks, are active. Holder concentration data was unavailable from RPC, though RugCheck flagged potential single holder ownership and high concentration, which could pose an economic risk.

Given the revoked mint and freeze authorities, the token's core supply and transfer mechanisms are secure from central control. However, the lack of detailed holder concentration data from RPC, coupled with RugCheck's flags for 'Single holder ownership' and 'High holder concentration', suggests a potential for market manipulation or significant price impact from large holders. Users should exercise caution and consider the implications of concentrated ownership before acquiring this token. A Premium Deploy option would involve deeper off-chain due diligence on the project team and a more granular analysis of on-chain holder movements if RPC data becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Low | The assface token is an SPL Token-2022 mint with 6 decimals and a total supply of 999,828,017.212586 tokens. Crucially, both the Mint Authority and Freeze Authority have been revoked, preventing furth |
| **Governance / Economics** | 3/10 | Medium | The token exhibits a liquidity of $34,223 on DEXs, with a healthy 24-hour volume to liquidity ratio of 0.50, suggesting organic trading activity. The DEX pair has been active for 53 days, providing so |
| **Upgrades** | 5/10 | Low | The token's immutability is strong, with both Mint and Freeze authorities permanently revoked, ensuring no new tokens can be minted and no accounts can be frozen. Furthermore, the token metadata is im |

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
| **Top-10 Holders** | 41.2% of supply |
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
