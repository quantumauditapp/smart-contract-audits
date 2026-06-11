---
token: Staked Bank
ticker: STAKE
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Staked Bank (STAKE) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/staked-bank-sol)

---

## Audit Summary

The Staked Bank (Stake) token mint audit reveals a well-configured SPL Token-2022 mint with no active mint or freeze authorities, ensuring a fixed supply and preventing account freezing. No transfer hooks or permanent delegates are configured, and metadata is immutable. Holder concentration data was unavailable from direct RPC queries, but RugCheck.xyz flagged high ownership by top holders.

> **Final Recommendation:** The Staked Bank (Stake) token mint appears to be well-configured with critical authorities revoked, offering a fixed supply and preventing account freezing. While direct holder concentration data was unavailable, RugCheck.xyz's 'high ownership' flag warrants caution regarding potential market manipulation. Users should consider this centralization risk and the moderate liquidity when making investment decisions. For enhanced due diligence, consider a Premium Deploy option to investigate the RugCheck findings further and potentially analyze off-chain team information.

## Security Analysis

The Staked Bank (Stake) token mint audit reveals a well-configured SPL Token-2022 mint with no active mint or freeze authorities, ensuring a fixed supply and preventing account freezing. No transfer hooks or permanent delegates are configured, and metadata is immutable. Holder concentration data was unavailable from direct RPC queries, but RugCheck.xyz flagged high ownership by top holders.

The Staked Bank (Stake) token mint appears to be well-configured with critical authorities revoked, offering a fixed supply and preventing account freezing. While direct holder concentration data was unavailable, RugCheck.xyz's 'high ownership' flag warrants caution regarding potential market manipulation. Users should consider this centralization risk and the moderate liquidity when making investment decisions. For enhanced due diligence, consider a Premium Deploy option to investigate the RugCheck findings further and potentially analyze off-chain team information.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Low | The Staked Bank (Stake) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, indicating a fixed supply and preventing any accounts from being frozen. No Tok |
| **Governance / Economics** | 6/10 | Medium | The token exhibits moderate liquidity with $15,856 USD available on DEXs, and a healthy 24-hour volume of $4,652, resulting in a normal Volume/Liquidity Ratio of 0.29. The DEX pair has been active for |
| **Upgrades** | 6/10 | Low | The token mint's core authorities, Mint Authority and Freeze Authority, are both revoked, meaning the token's supply cannot be increased and accounts cannot be frozen. No Token-2022 extensions that wo |

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
| **Contract** | [`5s7tf6...pump`](https://solscan.io/account/5s7tf6ih2CEZf7ZPNkJAtcknAq9DL5GsWHMMT3Jdpump) |
| **Network** | Solana |
| **Price** | $0.0001349 |
| **24h Volume** | $140.7K |
| **Liquidity** | $36.3K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 5d |
| **Top-10 Holders** | 64.6% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/eyuhvulacx9n1a3mj4lzts6ju7ejk49sfmtjne65mpnv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/staked-bank-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
