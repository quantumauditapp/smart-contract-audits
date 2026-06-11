---
token: SpaceX
ticker: SPCX
network: solana
risk_score: 54
status: high
date: 2026-06-10
---

# SpaceX (SPCX) — Smart Contract Security Analysis | Solana

> **Risk Score: 54/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-sol)

---

## Audit Summary

This SPL token mint audit for SpaceX (SPCX) identified a High risk due to the default frozen state for new accounts, requiring explicit unfreezing by an authority. Mint and freeze authorities are revoked, indicating a fixed supply and unalterable freeze status for existing accounts. Holder concentration data was unavailable, preventing an assessment of supply distribution risk.

> **Final Recommendation:** Prospective holders should be aware of the 'Default Frozen State' for new accounts. Before acquiring this token, verify that an active and responsive issuer or authority is available to unfreeze new accounts, as otherwise, acquired tokens may be unspendable. Due to the unavailability of holder concentration data, it is advisable to monitor on-chain distribution if this information becomes available.

## Security Analysis

This SPL token mint audit for SpaceX (SPCX) identified a High risk due to the default frozen state for new accounts, requiring explicit unfreezing by an authority. Mint and freeze authorities are revoked, indicating a fixed supply and unalterable freeze status for existing accounts. Holder concentration data was unavailable, preventing an assessment of supply distribution risk.

Prospective holders should be aware of the 'Default Frozen State' for new accounts. Before acquiring this token, verify that an active and responsive issuer or authority is available to unfreeze new accounts, as otherwise, acquired tokens may be unspendable. Due to the unavailability of holder concentration data, it is advisable to monitor on-chain distribution if this information becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | High | 7.1 Architecture & 7.2 Code Security: The token is an SPL token mint on Solana, utilizing the standard `spl-token` program. Mint and Freeze authorities are both revoked (None), ensuring no new tokens  |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic: The token exhibits healthy liquidity with $239,314 USD available on DEXs, and a normal 24-hour volume to liquidity ratio of 2.98, suggesting organic trading activity. The DEX pair has be |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades: The mint authority and freeze authority are both revoked, meaning the token's supply is fixed and the ability to freeze accounts has been permanently disabled. GoPlus data indicates that |

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
| **Contract** | [`E6ifp2...pump`](https://solscan.io/account/E6ifp2mJy8cYQehUGUtFvrXriRKxRuonLmrvTFypump) |
| **Network** | Solana |
| **Price** | $0.001361 |
| **24h Volume** | $383.0K |
| **Liquidity** | $129.8K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 17.6% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/dzxwcypptyr2ntfmen2xauscb77t1zlpkg63pbpbkmbc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
