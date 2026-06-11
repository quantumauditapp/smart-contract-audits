---
token: Aliens are real
ticker: ALIENS
network: solana
risk_score: 90
status: critical
date: 2026-06-10
---

# Aliens are real (ALIENS) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aliens-are-real-sol)

---

## Audit Summary

No critical or high-severity vulnerabilities were identified based on the provided on-chain data and external security signals. Holder concentration data was unavailable, preventing a full assessment of supply distribution risk.

> **Final Recommendation:** The Aliens SPL token mint appears to have a secure on-chain configuration with revoked mint and freeze authorities. However, the absence of holder concentration data means that potential risks from concentrated supply cannot be assessed. It is recommended to monitor the token's holder distribution if this data becomes available. For any token, always verify the status of mint and freeze authorities on-chain before considering it for investment. If you are considering deploying a token, ensure all authorities are revoked post-launch and consider a Premium Deploy option to integrate robust pre-launch checks and ongoing monitoring.

## Security Analysis

No critical or high-severity vulnerabilities were identified based on the provided on-chain data and external security signals. Holder concentration data was unavailable, preventing a full assessment of supply distribution risk.

The Aliens SPL token mint appears to have a secure on-chain configuration with revoked mint and freeze authorities. However, the absence of holder concentration data means that potential risks from concentrated supply cannot be assessed. It is recommended to monitor the token's holder distribution if this data becomes available. For any token, always verify the status of mint and freeze authorities on-chain before considering it for investment. If you are considering deploying a token, ensure all authorities are revoked post-launch and consider a Premium Deploy option to integrate robust pre-launch checks and ongoing monitoring.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an `spl-token-2022` mint with a total supply of 995,377,903,620,994 units and 6 decimals. Both the Mint Authority and Freeze Authority have been revoked, preventing further token issuance |
| **Governance / Economics** | 10/10 | Medium | The token exhibits moderate liquidity at $121,579 USD, with a healthy 24-hour volume to liquidity ratio of 0.26, indicating normal trading patterns. The DEX pair has been active for 116 days, providin |
| **Upgrades** | 10/10 | Low | The mint's core authorities, Mint Authority and Freeze Authority, are both revoked, ensuring that the token supply cannot be arbitrarily increased and holder accounts cannot be frozen. The token is an |

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
| **Contract** | [`F5tfzt...pump`](https://solscan.io/account/F5tfztTnE4sYsMhZT5KrFpWvHmYSfJZoRjCuxKPbpump) |
| **Network** | Solana |
| **Price** | $0.0008594 |
| **24h Volume** | $648.2K |
| **Liquidity** | $158.6K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 25.0% of supply |
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

- [View on DexScreener](https://dexscreener.com/solana/7nvp4qykvmpeuhobyrzcn1tqiz7k8pmk5uxqeebrzyh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aliens-are-real-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
