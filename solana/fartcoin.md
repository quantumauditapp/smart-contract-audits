---
token: Fartcoin
ticker: FARTCOIN
network: solana
risk_score: 16
status: low
date: 2026-07-10
---

# Fartcoin (FARTCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fartcoin-sol)

---

## Audit Summary

The Fartcoin SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts by the issuer. However, new holder accounts are created in a frozen state, requiring an explicit unfreeze operation by an authority before tokens can be transferred. Holder concentration data was unavailable, and RugCheck.xyz provided a very low score (1/100) without explicitly flagging it as 'RUGGED'.

> **Final Recommendation:** Before interacting with Fartcoin, it is critical to understand the implications of the 'Default Frozen State' extension. New token accounts will be unusable until an authority explicitly unfreezes them. Verify the availability and responsiveness of the entity responsible for unfreezing accounts. Given the unavailability of holder concentration data, it is advisable to proceed with caution regarding potential market manipulation from large holders. The low RugCheck score (1/100) also warrants further investigation into the project's background, despite not being explicitly flagged as 'RUGGED'. For enhanced security, consider a Premium Deploy option that includes a comprehensive review of the unfreezing mechanism and a deeper dive into the project's history and team.

## Security Analysis

The Fartcoin SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts by the issuer. However, new holder accounts are created in a frozen state, requiring an explicit unfreeze operation by an authority before tokens can be transferred. Holder concentration data was unavailable, and RugCheck.xyz provided a very low score (1/100) without explicitly flagging it as 'RUGGED'.

Before interacting with Fartcoin, it is critical to understand the implications of the 'Default Frozen State' extension. New token accounts will be unusable until an authority explicitly unfreezes them. Verify the availability and responsiveness of the entity responsible for unfreezing accounts. Given the unavailability of holder concentration data, it is advisable to proceed with caution regarding potential market manipulation from large holders. The low RugCheck score (1/100) also warrants further investigation into the project's background, despite not being explicitly flagged as 'RUGGED'. For enhanced security, consider a Premium Deploy option that includes a comprehensive review of the unfreezing mechanism and a deeper dive into the project's history and team.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The Fartcoin token (9BB6NFEcjBCtnNLFko2FqVQBq8HHM13kCyYcdQbgpump) is an SPL token operating under the `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring no n |
| **Governance / Economics** | 5/10 | Medium | Economic stability indicators show a healthy liquidity of $6,407,559 USD and a 24-hour trading volume of $713,270 USD. The volume/liquidity ratio is 0.11, which is normal and does not suggest wash tra |
| **Upgrades** | 8/10 | Low | The Fartcoin SPL token mint has a robust upgrade posture regarding core authorities, with both the mint authority and freeze authority permanently revoked. This prevents any future changes to the toke |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.8% (≈ permanent lock) |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Default Frozen State  *(Severity: High · Status: Unresolved)*

New holder accounts are created in a frozen state (`GoPlus.default_account_state: 1`) and require explicit unfreezing by an authority.

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
| **Contract** | [`9BB6NF...pump`](https://solscan.io/account/9BB6NFEcjBCtnNLFko2FqVQBq8HHM13kCyYcdQbgpump) |
| **Network** | Solana |
| **Price** | $0.1481 |
| **24h Volume** | $713.3K |
| **Liquidity** | $6.41M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 32.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 626 buys / 1100 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bzc9nzfmqkxr6fz1dbph7bdf9broyef6pnzesp7v5iiw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fartcoin-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-10*
