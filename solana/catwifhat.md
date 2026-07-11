---
token: catwifhat
ticker: CATWIF
network: solana
risk_score: 30
status: medium
date: 2026-06-27
---

# catwifhat (CATWIF) — Smart Contract Security Analysis | Solana

> **Risk Score: 30/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catwifhat-sol)

---

## Audit Summary

The catwifhat (CATWIF) SPL Token Mint has revoked both mint and freeze authorities, indicating a fixed supply and no ability to freeze user accounts. No Token-2022 extensions that introduce centralisation risks, such as permanent delegates or transfer hooks, are active. Holder concentration data was unavailable, preventing an assessment of distribution risk. Overall, the token exhibits a low-risk profile based on available on-chain data.

> **Final Recommendation:** Based on the available on-chain data, the catwifhat (CATWIF) token presents a low-risk profile. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing arbitrary freezing of funds. No concerning Token-2022 extensions are active, and metadata is immutable. Investors should note that holder concentration data was unavailable, which is a common limitation for new tokens. It is always recommended to perform independent due diligence and understand the project's fundamentals before investing. For a Premium Deploy, ensure all relevant authorities are permanently revoked and consider a time-locked liquidity pool.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The catwifhat (CATWIF) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, as confirmed by `Mint Authority: revoked (None)` and `Freeze Authority: revoked  |
| **Governance / Economics** | 6/10 | Medium | The token's liquidity on DEXs is $105,582, which is sufficient to avoid the 'Very Low Liquidity' flag. The 24-hour volume is $1,068,051, resulting in a Volume/Liquidity Ratio of 10.12, which does not  |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's core parameters related to supply and account control cannot be changed. The token uses the spl-token-2022 program but doe |

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
| **Contract** | [`5pYB12...pump`](https://solscan.io/account/5pYB12kEhfhSFXJjZ7JtyqDpt6uUqhsF6iu6Ee9spump) |
| **Network** | Solana |
| **Price** | $0.0004765 |
| **24h Volume** | $823.6K |
| **Liquidity** | $83.9K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 5d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9726 buys / 8883 sells |

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

### Is catwifhat a scam?

catwifhat shows characteristics that mitigate some traditional scam risks, such as renounced ownership and no mint function preventing developer manipulation or inflationary attacks. However, the contract not being verified and liquidity not being locked introduce significant vulnerabilities. While these factors don't definitively label it a 'scam' in the traditional sense, they highlight potential for malicious actions or unforeseen issues.

### Is catwifhat safe to buy?

Buying catwifhat involves notable risks. The contract's unverified status means its code isn't transparent, making it difficult to assess for security flaws or hidden functions. Crucially, the liquidity is not locked, meaning it could be withdrawn, potentially impacting tradability and value. These factors contribute to its Medium Risk score, advising caution and thorough personal due diligence.

### Has catwifhat been audited?

The catwifhat contract is currently 'Not Verified,' meaning its source code is not publicly confirmed on the blockchain. This significantly hinders independent security audits, as reviewers cannot definitively examine the deployed code. This lack of transparency is a critical consideration for assessing the token's security posture.

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4dytblybdqyqjavjlrht4xtqkvm7qayzuttjfsicromp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catwifhat-sol)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-27*
