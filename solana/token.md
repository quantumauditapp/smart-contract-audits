---
token: 🦎
ticker: LIZARD
network: solana
risk_score: 70
status: high
date: 2026-06-10
---

# 🦎 (LIZARD) — Smart Contract Security Analysis | Solana

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-sol)

---

## Audit Summary

The 🦎 (LIZARD) SPL token mint has a critical configuration where new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. This introduces a central point of control and potential for funds to be unspendable if the authority is inactive. Holder concentration data was unavailable, preventing assessment of supply distribution risk.

> **Final Recommendation:** Given the 'Default Frozen State' configuration, prospective holders should verify the identity and responsiveness of the authority responsible for unfreezing new accounts. Without an active and reliable unfreezing mechanism, newly acquired tokens may become unspendable. It is also recommended to monitor for any updates regarding holder concentration once that data becomes available, as high concentration can pose significant market risks. For enhanced security and operational control, consider a Premium Deploy option that allows for custom token configurations and ensures all authorities are managed or revoked as intended from inception.

## Security Analysis

The 🦎 (LIZARD) SPL token mint has a critical configuration where new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. This introduces a central point of control and potential for funds to be unspendable if the authority is inactive. Holder concentration data was unavailable, preventing assessment of supply distribution risk.

Given the 'Default Frozen State' configuration, prospective holders should verify the identity and responsiveness of the authority responsible for unfreezing new accounts. Without an active and reliable unfreezing mechanism, newly acquired tokens may become unspendable. It is also recommended to monitor for any updates regarding holder concentration once that data becomes available, as high concentration can pose significant market risks. For enhanced security and operational control, consider a Premium Deploy option that allows for custom token configurations and ensures all authorities are managed or revoked as intended from inception.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The 🦎 (LIZARD) token is an SPL token operating on the `spl-token` program. Both the Mint Authority and Freeze Authority have been successfully revoked, indicating that no new tokens can be minted and  |
| **Governance / Economics** | 6/10 | Medium | The token exhibits moderate liquidity with $33,554 USD available on DEXs, and a healthy 24-hour volume to liquidity ratio of 0.02, suggesting organic trading activity. The pair has been active for 316 |
| **Upgrades** | 6/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, have been revoked, preventing any further changes to the token's supply or the ability to freeze accounts. Metadata mutability is als |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state and require explicit unfreezing by an authority. This is indicated by `GoPlus.default_account_state: 1`.

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
| **Contract** | [`347k5f...bonk`](https://solscan.io/account/347k5f1WLRYe81roRcLBWDR6k3eCRunaqetQPW6pbonk) |
| **Network** | Solana |
| **Price** | $0.0001683 |
| **24h Volume** | $206.8K |
| **Liquidity** | $58.6K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 50.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/gcgn1netxzanrvfzfno1w1br5vdvug7mysxdcgsrfsm4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
