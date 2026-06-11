---
token: Bullish Degen
ticker: BULLISH
network: solana
risk_score: 72
status: critical
date: 2026-06-10
---

# Bullish Degen (BULLISH) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bullish-degen-sol)

---

## Audit Summary

The Bullish Degen token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. Holder concentration data was unavailable from RPC, but RugCheck flagged high ownership by top holders, indicating potential centralization risks.

> **Final Recommendation:** Holders should be aware that new token accounts for Bullish Degen are created in a frozen state. This means that upon receiving tokens, users may need an issuer or designated authority to unfreeze their account before they can transfer or use the tokens. Verify the availability and responsiveness of such an authority. Due to unavailable holder concentration data and RugCheck's "high ownership" flags, consider the potential for price manipulation from large holders.

## Security Analysis

The Bullish Degen token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. Holder concentration data was unavailable from RPC, but RugCheck flagged high ownership by top holders, indicating potential centralization risks.

Holders should be aware that new token accounts for Bullish Degen are created in a frozen state. This means that upon receiving tokens, users may need an issuer or designated authority to unfreeze their account before they can transfer or use the tokens. Verify the availability and responsiveness of such an authority. Due to unavailable holder concentration data and RugCheck's "high ownership" flags, consider the potential for price manipulation from large holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The token is an SPL token using the standard `spl-token` program. Both mint and freeze authorities are revoked, ensuring no new tokens can be minted and no existing accounts can be frozen by an author |
| **Governance / Economics** | 3/10 | Medium | The token has a liquidity of $68,889 USD, with a 24-hour volume of $50,879, resulting in a normal volume/liquidity ratio of 0.74. The DEX pair is 251 days old, indicating a reasonable track record. Ho |
| **Upgrades** | 4/10 | Low | The mint authority and freeze authority for the token have both been revoked, meaning the token supply is fixed and no accounts can be frozen by an external authority. The token uses the standard `spl |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. (Fact: GoPlus.default_account_state: 1)

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
| **Contract** | [`C2omVh...pump`](https://solscan.io/account/C2omVhcvt3DDY77S2KZzawFJQeETZofgZ4eNWWkXpump) |
| **Network** | Solana |
| **Price** | $0.00169 |
| **24h Volume** | $308.8K |
| **Liquidity** | $150.3K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 28.6% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/gc1utsxrrlauwby3uwsemjuxhjmjhhv1sxj9a1jhvyxp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bullish-degen-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
