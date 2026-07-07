---
token: Bonk
ticker: BONK
network: solana
risk_score: 36
status: medium
date: 2026-07-07
---

# Bonk (BONK) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bonk-sol)

---

## Audit Summary

This audit of the Bonk SPL token mint reveals a high-risk finding: new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. The mint and freeze authorities are revoked, which is a positive security measure, but holder concentration data was unavailable. While GoPlus indicates metadata is immutable, RugCheck.xyz flags 'Mutable metadata' as a risk label, presenting a discrepancy.

> **Final Recommendation:** Holders should be aware that new Bonk token accounts will be created in a frozen state and require an unfreezing action before tokens can be transferred. Verify the process and availability of an unfreezing authority before acquiring or holding this token. While the mint and freeze authorities are revoked, the discrepancy regarding metadata mutability between GoPlus and RugCheck.xyz should be investigated to confirm the immutability of token branding. For a Premium Deploy, consider a token standard that does not default new accounts to a frozen state, or ensure a robust, decentralized unfreezing mechanism is in place.

## Security Analysis

This audit of the Bonk SPL token mint reveals a high-risk finding: new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. The mint and freeze authorities are revoked, which is a positive security measure, but holder concentration data was unavailable. While GoPlus indicates metadata is immutable, RugCheck.xyz flags 'Mutable metadata' as a risk label, presenting a discrepancy.

Holders should be aware that new Bonk token accounts will be created in a frozen state and require an unfreezing action before tokens can be transferred. Verify the process and availability of an unfreezing authority before acquiring or holding this token. While the mint and freeze authorities are revoked, the discrepancy regarding metadata mutability between GoPlus and RugCheck.xyz should be investigated to confirm the immutability of token branding. For a Premium Deploy, consider a token standard that does not default new accounts to a frozen state, or ensure a robust, decentralized unfreezing mechanism is in place.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | 7.1 Architecture & 7.3 Access Control: The Bonk token is an SPL token mint operating under the `spl-token` program. Both the mint authority and freeze authority have been revoked, which is a strong se |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The token exhibits healthy liquidity with $243,178 USD available on DEXs, and a normal 24-hour volume to liquidity ratio of 1.04, indicating organic trading activity rather than wash tra |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, ensuring that the token's supply and account freeze status cannot be altered post-launch by a central party. GoPlus indicates th |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state, as indicated by `GoPlus.default_account_state: 1`. This means that any new account receiving Bonk tokens will be unable to transfer them until an authority explicitly unfreezes the account.

**Recommendation:** Confirm an active issuer or designated authority is available and responsive to unfreeze accounts. Without such an authority, newly created token accounts will be unspendable. Users should understand this operational requirement before holding the token.


### `I-02` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.


### `I-03` — Insufficient data to assess  *(Severity: Informational · Status: Unresolved)*

Input did not include enough context to reliably evaluate contract behavior or upgrade safety.

**Recommendation:** Provide verified source code or ABI to enable a full review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DezXAZ...B263`](https://solscan.io/account/DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB263) |
| **Network** | Solana |
| **Price** | $0.00000426 |
| **24h Volume** | $253.6K |
| **Liquidity** | $243.2K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 40.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2955 buys / 2833 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6ofwm7kplfxnwmb3z5xwboxnspp3jjyirapqpsivcnsp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bonk-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-07*
