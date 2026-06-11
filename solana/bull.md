---
token: Bull
ticker: BULL
network: solana
risk_score: 70
status: high
date: 2026-06-10
---

# Bull (BULL) — Smart Contract Security Analysis | Solana

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bull-sol)

---

## Audit Summary

The Bull (BULL) SPL token presents a significant operational risk due to its default frozen account state, which requires manual unfreezing for new holders to interact with their tokens. While mint and freeze authorities are revoked, ensuring fixed supply and preventing arbitrary freezes, the default frozen state could hinder usability. Holder concentration data was unavailable, preventing a full assessment of market manipulation risk.

> **Final Recommendation:** Holders should be aware that new accounts for the Bull (BULL) token will be created in a frozen state, requiring an active issuer or authority to unfreeze them before transfers can occur. It is crucial to confirm the availability and responsiveness of such an entity to avoid unspendable tokens. While the token's core authorities are revoked and metadata is immutable, the operational hurdle of default frozen accounts should be carefully considered.

For a premium deployment, ensure that the default account state is set to unfrozen unless a specific, regulated use case explicitly requires accounts to be frozen by default.

## Security Analysis

The Bull (BULL) SPL token presents a significant operational risk due to its default frozen account state, which requires manual unfreezing for new holders to interact with their tokens. While mint and freeze authorities are revoked, ensuring fixed supply and preventing arbitrary freezes, the default frozen state could hinder usability. Holder concentration data was unavailable, preventing a full assessment of market manipulation risk.

Holders should be aware that new accounts for the Bull (BULL) token will be created in a frozen state, requiring an active issuer or authority to unfreeze them before transfers can occur. It is crucial to confirm the availability and responsiveness of such an entity to avoid unspendable tokens. While the token's core authorities are revoked and metadata is immutable, the operational hurdle of default frozen accounts should be carefully considered.

For a premium deployment, ensure that the default account state is set to unfrozen unless a specific, regulated use case explicitly requires accounts to be frozen by default.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | High | The Bull (BULL) token is an SPL token operating on the Solana blockchain using the standard `spl-token` program. Its mint authority has been revoked, preventing further token issuance and ensuring a f |
| **Governance / Economics** | 6/10 | Low | The token exhibits healthy liquidity with $191,731 USD available on DEXs, and a 24-hour volume of $327,127, indicating active trading (7.4 Economic). The volume/liquidity ratio of 1.71 is normal, sugg |
| **Upgrades** | 6/10 | Low | The token's mint and freeze authorities are both revoked, meaning no further changes can be made to the token's supply or the ability to freeze accounts (7.7 Upgrades). Metadata mutability is set to ` |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state (GoPlus.default_account_state: 1) and require explicit unfreezing by an authority. This can block transfers and make tokens unspendable until unfrozen.

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
| **Contract** | [`3TYgKw...pump`](https://solscan.io/account/3TYgKwkE2Y3rxdw9osLRSpxpXmSC1C1oo19W9KHspump) |
| **Network** | Solana |
| **Price** | $0.004915 |
| **24h Volume** | $735.4K |
| **Liquidity** | $324.5K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 23.6% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/hngjllzkwx2mnwhwdkfycmowz8fth2bxxdpj1vbvkjnb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bull-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
