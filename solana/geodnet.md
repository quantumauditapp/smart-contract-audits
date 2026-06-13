---
token: Geodnet
ticker: GEOD
network: solana
risk_score: 100
status: critical
date: 2026-06-13
---

# Geodnet (GEOD) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/geodnet-sol)

---

## Audit Summary

The Geodnet Token (GEOD) presents critical risks due to an unrevoked mint authority, allowing for unlimited token minting and potential dilution. Additionally, new holder accounts are created in a frozen state, which could hinder usability without an active issuer. Holder concentration data was unavailable, preventing a full assessment of market manipulation risks.

> **Final Recommendation:** Given the critical unrevoked mint authority, it is strongly recommended to verify on-chain that this authority is set to null before considering the token supply fixed or stable. Furthermore, the default frozen state for new accounts requires confirmation of an active issuer to unfreeze accounts; otherwise, tokens may become unspendable. Investors should proceed with extreme caution and understand the implications of these centralized controls.

## Security Analysis

The Geodnet Token (GEOD) presents critical risks due to an unrevoked mint authority, allowing for unlimited token minting and potential dilution. Additionally, new holder accounts are created in a frozen state, which could hinder usability without an active issuer. Holder concentration data was unavailable, preventing a full assessment of market manipulation risks.

Given the critical unrevoked mint authority, it is strongly recommended to verify on-chain that this authority is set to null before considering the token supply fixed or stable. Furthermore, the default frozen state for new accounts requires confirmation of an active issuer to unfreeze accounts; otherwise, tokens may become unspendable. Investors should proceed with extreme caution and understand the implications of these centralized controls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL token using the `spl-token` program. A critical risk exists as the mint authority (`AJihE2yBYmC8kTDRtj2oDGcDQduSvPQekkXZ1LSAwA5F`) is not revoked, allowing for arbitrary supply inc |
| **Governance / Economics** | 10/10 | Low | The token has a total DEX liquidity of $330,693, with a 24-hour volume of $1,923,417, resulting in a Volume/Liquidity ratio of 5.82. The DEX pair has been active for 605 days, indicating a relatively  |
| **Upgrades** | 10/10 | Low | The mint authority for the token is currently held by `AJihE2yBYmC8kTDRtj2oDGcDQduSvPQekkXZ1LSAwA5F`, posing a significant risk of supply manipulation. In contrast, the freeze authority has been revok |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 1 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is AJihE2yBYmC8kTDRtj2oDGcDQduSvPQekkXZ1LSAwA5F. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority: AJihE2yBYmC8kTDRtj2oDGcDQduSvPQekkXZ1LSAwA5F)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. (Fact: GoPlus.default_account_state: 1)

**Recommendation:** Confirm an active issuer is available to unfreeze accounts; otherwise the token is unspendable.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7JA5eZ...mKHu`](https://solscan.io/account/7JA5eZdCzztSfQbJvS8aVVxMFfd81Rs9VvwnocV1mKHu) |
| **Network** | Solana |
| **Price** | $0.2171 |
| **24h Volume** | $1.92M |
| **Liquidity** | $329.1K |
| **Volume / Liquidity** | 5.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 56.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4009 buys / 3096 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bkx9rshodjgku7pbhiksv3dprdlm3kwgodsfgn9cgj5d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/geodnet-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-13*
