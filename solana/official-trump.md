---
token: Official Trump
ticker: TRUMP
network: solana
risk_score: 79
status: critical
date: 2026-06-13
---

# Official Trump (TRUMP) — Smart Contract Security Analysis | Solana

> **Risk Score: 79/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/official-trump-sol)

---

## Audit Summary

The OFFICIAL TRUMP (TRUMP) SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts by the issuer. However, new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. Holder concentration data was unavailable from RPC, but RugCheck.xyz flags high ownership by top holders, indicating potential centralization risks.

> **Final Recommendation:** Prospective holders should be aware that new token accounts for OFFICIAL TRUMP (TRUMP) are created in a frozen state, necessitating an unfreeze operation by an authority before tokens can be transferred. It is crucial to confirm the availability and responsiveness of the entity responsible for unfreezing accounts. While direct holder concentration data was unavailable, external signals from RugCheck.xyz suggest high ownership by top holders, which could pose a risk of price volatility from large sell-offs.

For enhanced security and functionality, consider a Premium Deploy option for future SPL tokens. This service ensures all critical authorities (mint, freeze) are irrevocably revoked at launch, and provides comprehensive configuration to avoid default frozen states, ensuring tokens are immediately usable upon receipt.

## Security Analysis

The OFFICIAL TRUMP (TRUMP) SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts by the issuer. However, new holder accounts are created in a frozen state, requiring an authority to unfreeze them before use. Holder concentration data was unavailable from RPC, but RugCheck.xyz flags high ownership by top holders, indicating potential centralization risks.

Prospective holders should be aware that new token accounts for OFFICIAL TRUMP (TRUMP) are created in a frozen state, necessitating an unfreeze operation by an authority before tokens can be transferred. It is crucial to confirm the availability and responsiveness of the entity responsible for unfreezing accounts. While direct holder concentration data was unavailable, external signals from RugCheck.xyz suggest high ownership by top holders, which could pose a risk of price volatility from large sell-offs.

For enhanced security and functionality, consider a Premium Deploy option for future SPL tokens. This service ensures all critical authorities (mint, freeze) are irrevocably revoked at launch, and provides comprehensive configuration to avoid default frozen states, ensuring tokens are immediately usable upon receipt.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | High | The OFFICIAL TRUMP (TRUMP) token is an SPL token operating on the Solana blockchain, utilizing the `spl-token` program. The mint authority has been revoked, ensuring no new tokens can be minted, and t |
| **Governance / Economics** | 10/10 | Medium | The token exhibits substantial liquidity with $37,319,778 USD on DEXs and a healthy 24-hour volume of $10,058,326 USD, indicating active trading. The Volume/Liquidity Ratio is 0.27, which is considere |
| **Upgrades** | 1/10 | Low | The mint authority for the token has been revoked, meaning the total supply is fixed and cannot be increased by the original issuer. Similarly, the freeze authority has been revoked, preventing the is |

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
| **Contract** | [`6p6xgH...GiPN`](https://solscan.io/account/6p6xgHyF7AeE6TZkSmFsko444wqoP15icUSqi2jfGiPN) |
| **Network** | Solana |
| **Price** | $2.1500 |
| **24h Volume** | $10.06M |
| **Liquidity** | $37.24M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4658 buys / 4986 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9d9mb8kooffad3sctgztkxqypkshx6ezhbkio89ixyy2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/official-trump-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-13*
