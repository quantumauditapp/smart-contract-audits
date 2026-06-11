---
token: Pudgy Penguins
ticker: PENGU
network: solana
risk_score: 72
status: critical
date: 2026-06-10
---

# Pudgy Penguins (PENGU) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pudgy-penguins-sol)

---

## Audit Summary

The audit of the Pudgy Penguins (PENGU) SPL token mint identified a high-severity risk: new holder accounts are created in a frozen state, requiring manual unfreezing by an authority. While mint and freeze authorities are revoked, which is positive for supply control and general account security, the default frozen state introduces operational friction. Holder concentration data was unavailable from RPC, though RugCheck flagged high concentration as a risk label.

> **Final Recommendation:** Holders should be aware that new accounts for Pudgy Penguins (PENGU) tokens are created in a frozen state. This means that upon receiving tokens, users may need an active issuer or authority to unfreeze their accounts before they can transfer or spend the tokens. It is crucial to confirm the availability and responsiveness of such an entity. While mint and freeze authorities are revoked, which is positive for supply control and general account security, the default frozen state introduces operational friction and potential for funds to be unspendable if the unfreezing mechanism is not accessible.

Consider the operational implications of the default frozen state before acquiring or holding this token. Verify the process for unfreezing accounts and the reliability of the entity responsible for this action. For a premium deployment, ensure that any future token launches explicitly set the…

## Security Analysis

The audit of the Pudgy Penguins (PENGU) SPL token mint identified a high-severity risk: new holder accounts are created in a frozen state, requiring manual unfreezing by an authority. While mint and freeze authorities are revoked, which is positive for supply control and general account security, the default frozen state introduces operational friction. Holder concentration data was unavailable from RPC, though RugCheck flagged high concentration as a risk label.

Holders should be aware that new accounts for Pudgy Penguins (PENGU) tokens are created in a frozen state. This means that upon receiving tokens, users may need an active issuer or authority to unfreeze their accounts before they can transfer or spend the tokens. It is crucial to confirm the availability and responsiveness of such an entity. While mint and freeze authorities are revoked, which is positive for supply control and general account security, the default frozen state introduces operational friction and potential for funds to be unspendable if the unfreezing mechanism is not accessible.

Consider the operational implications of the default frozen state before acquiring or holding this token. Verify the process for unfreezing accounts and the reliability of the entity responsible for this action. For a premium deployment, ensure that any future token launches explicitly set the…

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The Pudgy Penguins (PENGU) token is an SPL token mint operating on the Solana blockchain using the standard `spl-token` program. Both the mint authority and freeze authority have been revoked, indicat |
| **Governance / Economics** | 6/10 | Medium | The token has substantial liquidity, with $3,289,871 USD available on DEXs, and a healthy 24-hour volume of $505,667 USD. The volume/liquidity ratio is 0.15, which is considered normal and does not su |
| **Upgrades** | 6/10 | Low | The token's mint authority and freeze authority are both revoked, meaning no further tokens can be minted and no accounts can be frozen by an external authority. The metadata for the token is immutabl |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority (GoPlus.default_account_state: 1).

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
| **Contract** | [`2zMMhc...uauv`](https://solscan.io/account/2zMMhcVQEXDtdE6vsFS7S7D5oUodfJHE8vd1gnBouauv) |
| **Network** | Solana |
| **Price** | $0.00772 |
| **24h Volume** | $358.5K |
| **Liquidity** | $3.67M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 47.5% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/ddma1chcheqyfttc1z1sjey978ccu1pyjnutwtnmdvzu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pudgy-penguins-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
