---
token: Kiyomasa
ticker: 清正
network: solana
risk_score: 29
status: medium
date: 2026-06-14
---

# Kiyomasa (清正) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kiyomasa-sol)

---

## Audit Summary

This SPL Token Mint, Kiyomasa (清正), demonstrates a robust security posture with both mint and freeze authorities revoked, and immutable metadata. No high-risk Token-2022 extensions like transfer hooks or permanent delegates are active. Holder concentration data was unavailable, preventing a full assessment of distribution risk.

> **Final Recommendation:** Based on the available on-chain data, the Kiyomasa (清正) token appears to be well-configured from a security perspective, with critical authorities revoked and no active high-risk Token-2022 extensions. Holders should be aware that holder concentration data was not available, so a full assessment of potential market manipulation from large holders cannot be made. For a comprehensive understanding, monitor on-chain holder distribution if data becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token (7.1 Architecture) is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority have been revoked (7.3 Access Control), indicating that no single entity can mint new tokens or fre |
| **Governance / Economics** | 7/10 | Low | The token has a liquidity of $18,245 USD (7.4 Economic), which is moderate. The 24-hour volume is $8,361, resulting in a healthy Volume/Liquidity Ratio of 0.46, not indicating wash trading. The DEX pa |
| **Upgrades** | 8/10 | Low | The Mint Authority and Freeze Authority are both revoked (7.7 Upgrades), meaning the token's core parameters (supply, freeze capability) cannot be altered. The token's metadata is immutable, preventin |

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
| **Contract** | [`ANP1wJ...pump`](https://solscan.io/account/ANP1wJHYWYQPfrZvg8FnjduwfBVJhRV3xqKcs3yapump) |
| **Network** | Solana |
| **Price** | $0.0003475 |
| **24h Volume** | $410.7K |
| **Liquidity** | $56.1K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 25.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2989 buys / 2871 sells |

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

### Is Kiyomasa a scam?

Based on available data, Kiyomasa (清正) exhibits characteristics often associated with high-risk projects, such as an unverified contract and unlocked liquidity, which are concerning. However, ownership has been renounced and no mint function exists, mitigating certain developer-controlled rug pull vectors. While these red flags necessitate extreme caution and vigilance from investors, we cannot definitively label it a scam based solely on the provided data.

### Is Kiyomasa safe to buy?

Kiyomasa (清正) carries significant security risks that suggest it is not a safe investment. The contract is unverified, preventing public code review and potential hidden vulnerabilities. Crucially, liquidity is not locked, meaning the funds enabling trading can be removed by liquidity providers, risking a 'rug pull' and rendering tokens untradable. These fundamental issues, alongside some holder concentration, indicate a high-risk environment for potential buyers.

### Has Kiyomasa been audited?

There is no information indicating Kiyomasa (清正) has undergone a formal security audit. Moreover, the contract is explicitly listed as 'False' for verification. This means its source code is not publicly available or confirmed to match the deployed bytecode on the blockchain. This lack of transparency and an independent audit makes it challenging to assess the contract's integrity and security, posing a significant risk.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/dkg6ternfkmeelmxcvxwobzzzqi7vtpkco6gqvukf33c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kiyomasa-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-14*
