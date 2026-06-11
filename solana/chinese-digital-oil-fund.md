---
token: Chinese Digital Oil Fund
ticker: CDOF
network: solana
risk_score: 72
status: critical
date: 2026-06-10
---

# Chinese Digital Oil Fund (CDOF) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/chinese-digital-oil-fund-sol)

---

## Audit Summary

This audit of the Chinese Digital Oil Fund (CDOF) SPL token mint identified a High-severity risk due to new holder accounts being created in a frozen state, requiring an authority to unfreeze them before use. Critical authorities such as Mint and Freeze have been revoked, indicating a fixed supply and immutability of existing accounts. Holder concentration data was unavailable for analysis.

> **Final Recommendation:** Prospective holders should be aware that new token accounts for CDOF are created in a frozen state. It is critical to confirm the availability and responsiveness of an active issuer or authority capable of unfreezing accounts. Without this, newly acquired tokens may be unspendable. Given that Mint and Freeze authorities are revoked, the token's supply is fixed, and existing accounts cannot be frozen by an authority, which is a positive security aspect. However, the default frozen state introduces a significant operational hurdle.

## Security Analysis

This audit of the Chinese Digital Oil Fund (CDOF) SPL token mint identified a High-severity risk due to new holder accounts being created in a frozen state, requiring an authority to unfreeze them before use. Critical authorities such as Mint and Freeze have been revoked, indicating a fixed supply and immutability of existing accounts. Holder concentration data was unavailable for analysis.

Prospective holders should be aware that new token accounts for CDOF are created in a frozen state. It is critical to confirm the availability and responsiveness of an active issuer or authority capable of unfreezing accounts. Without this, newly acquired tokens may be unspendable. Given that Mint and Freeze authorities are revoked, the token's supply is fixed, and existing accounts cannot be frozen by an authority, which is a positive security aspect. However, the default frozen state introduces a significant operational hurdle.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | High | 7.1 Architecture & 7.2 Code Security: The CDOF token operates on the standard `spl-token` program. Both the Mint Authority and Freeze Authority have been revoked (None), ensuring no new tokens can be  |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic: The token exhibits healthy liquidity with $298,434 USD available on DEXs. The 24-hour volume is $293,547, resulting in a normal Volume/Liquidity Ratio of 0.98, which does not suggest was |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades: The Mint and Freeze authorities are revoked, which means these critical functions cannot be changed or re-enabled, providing stability regarding supply and account status. The token uses |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority, as indicated by `GoPlus.default_account_state: 1`.

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CDoFug...E4az`](https://solscan.io/account/CDoFug7K6gYgiotXw1vcyfc9p4rdAxnbbj2DcH5AE4az) |
| **Network** | Solana |
| **Price** | $0.009503 |
| **24h Volume** | $314.9K |
| **Liquidity** | $282.5K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 14d |
| **Top-10 Holders** | 10.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2477 buys / 997 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2j8va5luscsdjq8gt4huz2cukttbrfpdswhvouqfrh5v)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/chinese-digital-oil-fund-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
