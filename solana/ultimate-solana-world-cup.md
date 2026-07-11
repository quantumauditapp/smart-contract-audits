---
token: Ultimate Solana World Cup
ticker: USWC
network: solana
risk_score: 47
status: high
date: 2026-06-15
---

# Ultimate Solana World Cup (USWC) — Smart Contract Security Analysis | Solana

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ultimate-solana-world-cup-sol)

---

## Audit Summary

The SPL Token Mint at CqFJhmzTVCdULq4KdfwKqsBf7ABaaZarWCrarazupump exhibits a strong technical configuration with both mint and freeze authorities revoked, indicating a fixed supply and no ability to freeze user accounts. No Token-2022 transfer hook or permanent delegate is active. However, quantitative data regarding holder concentration and DEX liquidity is unavailable, preventing a full economic assessment. RugCheck.xyz qualitatively flags potential risks such as 'Single holder ownership', 'High holder concentration', and 'Low Liquidity'.

> **Final Recommendation:** The token exhibits a robust technical configuration with critical authorities revoked, ensuring a fixed supply and no ability to freeze accounts. However, the absence of quantitative data for holder concentration and DEX liquidity, coupled with RugCheck.xyz's qualitative warnings of 'High holder concentration' and 'Low Liquidity', indicates significant economic risks. Users should exercise extreme caution due to the potential for high slippage and price volatility. It is recommended to await the availability of comprehensive market data before making investment decisions. For a Premium Deploy option, consider tokens with transparent and verifiable liquidity and holder distribution metrics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture & 7.2 Code Security: The token is an SPL Token-2022 mint. 7.3 Access Control: Both the Mint Authority and Freeze Authority have been revoked, as confirmed by 'Mint Authority: revoked  |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Quantitative data for holder concentration and DEX liquidity is unavailable ('[UNKNOWN] holder concentration unavailable', '[UNKNOWN] no DEX pair data available'). This lack of data prev |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The token's configuration demonstrates strong immutability. The revocation of both Mint Authority and Freeze Authority prevents any future changes to the token supply or the ability to f |

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
| **Contract** | [`CqFJhm...pump`](https://solscan.io/account/CqFJhmzTVCdULq4KdfwKqsBf7ABaaZarWCrarazupump) |
| **Network** | Solana |
| **Price** | $0.00009856 |
| **24h Volume** | $48.8K |
| **Liquidity** | $31.6K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 2d |
| **Top-10 Holders** | 33.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4829 buys / 4479 sells |

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

## Frequently Asked Questions

### Is Ultimate Solana World Cup a scam?

Based on available data, direct evidence for USWC being an outright scam is not definitive, especially with ownership renounced and no mint function. However, the lack of contract verification means its code is not public for review, and unlocked liquidity presents a significant risk of a rug pull, where funds could be withdrawn. These factors elevate the potential for adverse outcomes for investors.

### Is Ultimate Solana World Cup safe to buy?

USWC is currently rated with a High Risk score of 46/100. Key safety concerns include the contract not being verified, which prevents code inspection, and the liquidity not being locked, meaning funds can be withdrawn at any time. While developer control risks are reduced by ownership renunciation, these fundamental vulnerabilities suggest a high degree of risk for potential buyers.

### Has Ultimate Solana World Cup been audited?

Information regarding an official security audit for USWC is not provided. Crucially, the contract is also not verified on the blockchain explorer. This means its source code is not publicly published and accessible for review by anyone, including potential auditors or investors, making it impossible to independently assess the contract's security and functionality.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/f1bb4rjipymldps8inubdy4mrnvopu7jpvgh7ighe2r)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ultimate-solana-world-cup-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-15*
